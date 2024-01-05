## Vacation Tracker documentation
The purpose of this documentation is to provide a technical analysis on MRi's Vacation tracker. 

The Vacation Tracker can be split into two parts
    - Vacation days
    - Sick days


## Vacation: Managing Vacation Days and Date Lists
How are Vacation days calculated.<br/>
In vacalc.php: <br/>
    <ul>
    <li>  <b>Vacation Days for the Month = Initial Vacation Days + Accrual Rate</b> <br/></li>
        <ul>
            <li>  For employees with 0 to 2 years of service, the monthly accrual is 0.833 days.<br/></li>
            <li>  For employees with 4 to 6 years of service, the monthly accrual is 1.25 days.<br/></li>
            <li>  For employees with 7 or more years of service, the monthly accrual is 1.66 days.<br/></li>
        </ul>
    </ul>
<br/>


## Vacation Submission and Email Functionality
<p>Location of the file: <code>/var/www/apps/http/pto/ajax/submit.php</code></p>
<p>This file is responsible for setting permissions and managing the core functionalities related to submitting a PTO (Paid Time Off) request. It includes:</p>

<ul>
    <li>Permission settings and PTO request handling.</li>
    <li>Email functionality starting from line 180, utilizing PHP's built-in mailer (phpmailer).</li>
</ul>

<h3>Notable Items:</h3>
<ul>
    <li>When Julie requests a vacation day, the intended receiver is Daryl; otherwise, it defaults to the employee's supervisor.</li>
    <li>If no supervisor is found, the email should be sent to Syed. If no user information is available, Tim is the intended receiver.</li>
    <li>There are two versions of PHP mailer. The current email system uses the newer version, which is located at: <code>/var/www/apps/includes/class.phpmailer.php</code></li>
</ul>
