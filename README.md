# MRI-Timesheet documentation 09/06/2023
<h2>The purpose of this document is to provide explanations, descriptions, and context for the code behind MRI's Timesheet function.</h2>

## Table of Contents

- [User flow](##User-flow)

- [Timesheet Entry Form (add_hours)](##Timesheet-Entry-Form-(add_hours))






## User flow
<p>This section describes how the user is intended to use the timesheet.</p>

<b>1. Initial Landing Page</b>

User starts at the homepage: https://apps.marketingresources.com/
User should be logged in and authenticated.

<b>2. Navigate to Timesheet Page</b>

User proceeds to the "Timesheet" page by clicking on a link, located on the left side of the screen.
URL: https://apps.marketingresources.com/timesheet

<b>3. Timesheet Form Entry</b>

3.1 Select a Job

User encounters a form that includes fields for their timesheet entry.
The user first needs to select a job from one of the following options:
Select a Job from Your Recent Jobs list.
Select a Job from Active Jobs List.

3.2 Select Function

After selecting a job, the user must specify their function related to the selected job.

3.3 Enter Comments (Optional)

The user can choose to enter comments or notes related to the work performed, which is an optional field.

3.4 Select Department

The user is required to select their department from a list of available options.

3.5 Enter Hours and Minutes Worked

The user needs to input the number of hours and minutes worked for the specified job.

<b>4. Submit Timesheet Entry</b>

4.1 Review Entries

The user should have the opportunity to review all the information entered in the timesheet form to ensure accuracy.

4.2 Submit Timesheet

Once the user is satisfied with the entered information, they can submit the timesheet entry by clicking "Add Entry".

Recording Timesheet Entry in a Table

<p>Upon successful submission of the timesheet entry, the user's provided information is systematically added to a table within the system. Each entry is recorded in its respective location within the table, ensuring accurate tracking and management of timesheet data.
</p>

## Timesheet Entry Form (add_hours)

The `add_hours` form allows users to submit their timesheet entries. Upon submission, the `add_hours.hours` and `add_hours.minutes` values are returned and used to populate a table located at the bottom of the screen. The process of filling in hours and minutes is handled by the `Validate2` function.

<b>Form Inputs:</b>

1. **Recent Job List**

This section generates a list of the user's 20 most recent job entries, retrieved from an SQL Query. Below is an example of the SQL Query code:
   ```sql
   SELECT DISTINCT job_id FROM job_log WHERE user_id = " . $_COOKIE['x'] . " AND job_id in (select id from job_info where active = 'Y' OR active='P') ORDER BY id desc limit 20"
   ```

2. Active Job List

Users can choose from a list of active jobs at MRI (Marketing Resources Inc.), which is also generated from an SQL Query. Here is an example of the SQL Query code:
``` SQL
"SELECT id,name,active from job_info where (active = 'Y' OR active='P') order by id, name");
                                                while ($iRow = @mysql_fetch_object($pr_jobs)) {
                                                    echo "<option value=\"$iRow->id\"";
                                                    if ($iRow->active == "P") {
                                                    echo ">" . $iRow->id . "  :: " . $iRow->name . "(PENDING)</option>"; }
                                                    else {
                                                        echo ">" . $iRow->id . "  :: " . $iRow->name . "</option>"; }
```
3. Function

This input allows users to select a specific function related to the job they have chosen.

4. Comments (Optional)

Users have the option to include additional notes or comments related to their timesheet entry.
Role

This field permits users to select their department or role within the organization.
Hours Worked

Users can input the number of hours worked for the selected job.
Multiple Entries Per Day
Users are allowed to submit more than one timesheet entry per day, enabling them to record their work for various jobs and functions as needed.
