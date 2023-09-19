## Vacation Tracker documentation
The purpose of this documentation is to provide a technical analysis on MRi's Vacation tracker. 

The Vacation Tracker can be split into two parts
    - Vacation days
    - Sick days


## Part 1: Vacation: Managing Vacation Days and Date Lists
How are Vacation days calculated.<br/>
In vacalc.php: <br/>
    <ul>
    <li>  <b>Vacation Days for the Month = Initial Vacation Days + Accrual Rate</b> <br/></li>
        <li>  For employees with 0 to 2 years of service, the monthly accrual is 0.833 days.<br/></li>
        <li>  For employees with 4 to 6 years of service, the monthly accrual is 1.25 days.<br/></li>
        <li>  For employees with 7 or more years of service, the monthly accrual is 1.66 days.</li>
    </ul>
