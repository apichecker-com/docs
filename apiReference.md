# ApiChecker GRAPH documentation

## Query
<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>me</strong></td>
<td valign="top"><a href="/#/apiReference?id=user">User</a></td>
<td>

Get basic information about current User

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>apps</strong></td>
<td valign="top">[<a href="/#/apiReference?id=application">Application</a>]</td>
<td>

Fetch list of applications and list of monitors

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>monitors</strong></td>
<td valign="top">[<a href="/#/apiReference?id=monitor">Monitor</a>]</td>
<td>

Fetch list of monitors without grouping by Applications

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>checkLogs</strong></td>
<td valign="top">[<a href="/#/apiReference?id=checklogs">CheckLogs</a>]</td>
<td>

Fetch list of CheckLogs for selected Monitor. 'monitorId' should be provided.

</td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">monitorId</td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td></td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">numLogs</td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td></td>
</tr>
</tbody>
</table>

## Mutation / Actions
this schema allows the following mutation:

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>changeMonitorStatus</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td>

Method to pause or resume monitoring for selected monitor

</td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">monitorId</td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td></td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">enable</td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td></td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">delay</td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td></td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>changeApplicationStatus</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td>

Method to pause or resume monitoring for selected Application and all nested monitors

</td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">applicationId</td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td></td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">enable</td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td></td>
</tr>
<tr>
<td colspan="2" align="right" valign="top">delay</td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td></td>
</tr>
</tbody>
</table>

## Objects Structure

### Application

Represent application object with list of monitors attached

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>_id</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td></td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>appName</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Application name

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>createAt</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Created at

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>updatedAt</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Updated at

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>monitors</strong></td>
<td valign="top">[<a href="/#/apiReference?id=monitor">Monitor</a>]!</td>
<td>

List of monitors for this application

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>createdBy</strong></td>
<td valign="top"><a href="/#/apiReference?id=user">User</a>!</td>
<td>

User who create this application

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>access</strong></td>
<td valign="top">[<a href="/#/apiReference?id=user">User</a>]</td>
<td>

Users who have access to this app

</td>
</tr>
</tbody>
</table>

### CheckLogs

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>statusCode</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

Response status code

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>OK</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a></td>
<td>

Is health check was successful. It will be TRUE in case of below checks:
1. Expected status code = (equal) Response status code. 
2. (only in case of KeywordCheck enabled on Monitor) Keyword check is passed as well.

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>passCheck</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a></td>
<td>

Is Check pass Keyword check (only in case of KeywordCheck enabled on Monitor)

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>timingPhases</strong></td>
<td valign="top"><a href="/#/apiReference?id=timingphases">TimingPhases</a></td>
<td>

Information about each step of request timings, such as "DNS query timing, first type timing, etc)

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>elapsedTime</strong></td>
<td valign="top"><a href="/#/apiReference?id=float">Float</a></td>
<td>

Elapsed time for request (in milliseconds)

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>responseSize</strong></td>
<td valign="top"><a href="/#/apiReference?id=float">Float</a></td>
<td>

Response size in kilobytes

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>createAt</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

When current health-check was performed

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>checkerInformation</strong></td>
<td valign="top"><a href="/#/apiReference?id=checkerinformation">CheckerInformation</a></td>
<td>

Information from what location this health-check was performed. 

</td>
</tr>
</tbody>
</table>

### CheckerInformation

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>checkerLocation</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

Server location

</td>
</tr>
</tbody>
</table>

### HealthLogs

Contain information about Health/Uptime changes for monitor. Once any Monitor change state (UP -> Down, DOWN -> UP, DISABLE -> UP, etc) it will be recorded in this array

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>status</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

Status of Monitor:
* "0" - down
* "1" - up
* "2" - unknown

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>dateTime</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

Start date time for this monitor status

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>reason</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

Reason of monitor change

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>duration</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

Period duration

</td>
</tr>
</tbody>
</table>

### Monitor

Represent monitor object with information about monitoring URL, name, etc

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>_id</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td></td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>monitorUrl</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Monitoring URL

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>monitorName</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Monitor name

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>requestType</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Type of monitoring request, can be:
* POST
* GET
* DELETE
* PUT
etc

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>checkInterval</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a>!</td>
<td>

How frequently ApiChecker monitoring this URL

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>authRequired</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td>

Is AuthRequired for this Monitor?

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>alertsEnabled</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td>

Is alerts enabled for this Monitor?

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>expectedStatusCode</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a>!</td>
<td>

Expected status code for this Monitor. Usually it's 200 OK STATUS Code.

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>countOfFailedChecks</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a>!</td>
<td>

Count of failed checks

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>checkEnabled</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td>

Is monitoring active for this Monitor?

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>createdBy</strong></td>
<td valign="top"><a href="/#/apiReference?id=user">User</a>!</td>
<td>

User that crate current Monitor

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>authType</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Type of Auth for current monitor, can be "Basic, oAUTH, etc"

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>keywordCheck</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

ApiChecker will use this "String" to verify response body for selected Keyword.
If response body will not contain Keyword - it will be marked as failed, even if response status code will be same as expected status code. 

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>uptimeChanges</strong></td>
<td valign="top">[<a href="/#/apiReference?id=healthlogs">HealthLogs</a>]</td>
<td>

Every uptime changes in current monitor will be recorded in this array 

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>uptime</strong></td>
<td valign="top"><a href="/#/apiReference?id=uptimemetrics">UptimeMetrics</a></td>
<td>

Information about Uptime for today, last week, last month, last 3 month 

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>keywordCheckEnabled</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a>!</td>
<td>

Is ApiChecker should verify response body for selected Keyword. (take a look on keywordCheck property)

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>createAt</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Monitor Created at

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>updatedAt</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Monitor Updated at

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>language</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Request language, applied for PUT and POST requests.
Can be:
* JSON
* XML (SOAP)

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>lastCheck</strong></td>
<td valign="top"><a href="/#/apiReference?id=checklogs">CheckLogs</a></td>
<td>

Information about last health check for current monitor

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>currentStatus</strong></td>
<td valign="top"><a href="/#/apiReference?id=currentstatus">CurrentStatus</a>!</td>
<td>

Current status of monitor

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>sslInformation</strong></td>
<td valign="top"><a href="/#/apiReference?id=sslinformation">SslInformation</a></td>
<td>

Information about SSL certificates, only applicable for HTTPS monitors 

</td>
</tr>
</tbody>
</table>

### SslInformation

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>subject</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

SSL certificate Subject information

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>issuer</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

Information about who issuer of current SSL certificate

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>validFrom</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

When certificate created

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>valid</strong></td>
<td valign="top"><a href="/#/apiReference?id=boolean">Boolean</a></td>
<td>

Is certificate still valid

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>validTo</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a></td>
<td>

When certificate will expire

</td>
</tr>
</tbody>
</table>

### TimingPhases

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>wait</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

Wait phase of request

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>dns</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

DNS resolution phase of request

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>tcp</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

TCP connection phase of request

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>firstByte</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

FirstByte retrieving phase of request

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>download</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

Download phase of request

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>total</strong></td>
<td valign="top"><a href="/#/apiReference?id=int">Int</a></td>
<td>

Total time spend on request

</td>
</tr>
</tbody>
</table>

### UptimeMetrics

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>avgHealthLastDay</strong></td>
<td valign="top"><a href="/#/apiReference?id=float">Float</a></td>
<td>

Uptime last 24 hours

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>avgHeathLastMonth</strong></td>
<td valign="top"><a href="/#/apiReference?id=float">Float</a></td>
<td>

Uptime last 30 days

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>avgHeathLastThreeMonth</strong></td>
<td valign="top"><a href="/#/apiReference?id=float">Float</a></td>
<td>

Uptime last 90 days

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>avgHeath</strong></td>
<td valign="top"><a href="/#/apiReference?id=float">Float</a></td>
<td>

Uptime last 7 days, default value for dashboard

</td>
</tr>
</tbody>
</table>

### User

Represent user object with email, name and current subscription information

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>email</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

user email

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>name</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

user name

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>createAt</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

user registered at

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>subscription</strong></td>
<td valign="top"><a href="/#/apiReference?id=usersubscription">UserSubscription</a>!</td>
<td>

Information about user Subscription. Such as: user subscription plan, current status

</td>
</tr>
</tbody>
</table>

### UserSubscription

<table>
<thead>
<tr>
<th align="left">Field</th>
<th align="right">Argument</th>
<th align="left">Type</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="2" valign="top"><strong>plan</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Current subscription plan

</td>
</tr>
<tr>
<td colspan="2" valign="top"><strong>status</strong></td>
<td valign="top"><a href="/#/apiReference?id=string">String</a>!</td>
<td>

Is User Still Active?

</td>
</tr>
</tbody>
</table>

## Enums

### CurrentStatus

<table>
<thead>
<th align="left">Value</th>
<th align="left">Description</th>
</thead>
<tbody>
<tr>
<td valign="top"><strong>UP</strong></td>
<td>

Monitor is up

</td>
</tr>
<tr>
<td valign="top"><strong>DOWN</strong></td>
<td>

Monitor is down

</td>
</tr>
<tr>
<td valign="top"><strong>DISABLED</strong></td>
<td>

Monitoring disabled

</td>
</tr>
<tr>
<td valign="top"><strong>UNKNOWN</strong></td>
<td>

Monitor status unknown

</td>
</tr>
</tbody>
</table>

