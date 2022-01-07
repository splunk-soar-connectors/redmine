[comment]: # "Auto-generated SOAR connector documentation"
# Redmine

Publisher: Splunk Community  
Connector Version: 1\.0\.1  
Product Vendor: Redmine  
Product Name: Redmine  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.9\.39220  

This app integrates with Redmine to perform several ticket management actions

[comment]: # " File: readme.md"
[comment]: # "  Copyright (c) 2021 Splunk Inc."
[comment]: # ""
[comment]: # "  Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
## Redmine

Redmine is an open-source ticketing system, and the actions performed by these API calls depend to
some extent on the configuration of the Redmine instance.

**The functioning of On Poll**

-   The On Poll action works in 2 steps. In the first step, all the tickets (issues) will be fetched
    in defined time duration. In the second step, all the components (e.g. fields) of the tickets
    (retrieved in the first step) will be fetched. A container will be created for each ticket and
    for each ticket all the components will be created as the respective artifacts.
-   The tickets will be fetched in the oldest first order based on the **updated** time in the On
    Poll action
-   The updated timestamps of the components have been appended to the end of the artifact name to
    maintain a particular component's uniqueness.
-   Users can provide the JSON formatted list of the custom fields' names (to be considered for the
    ingestion) in the asset configuration parameter `      custom_fields     ` .


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Redmine asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | Server URL
**verify\_server\_cert** |  optional  | boolean | Verify Server Certificate
**username** |  optional  | string | Username
**password** |  optional  | password | Password
**project\_id** |  required  | string | Redmine Project ID
**custom\_fields** |  optional  | string | Comma\-separated list of custom fields to extract from tickets

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[on poll](#action-on-poll) - Ingest tickets from Redmine  
[create ticket](#action-create-ticket) - Create a ticket \(issue\)  
[update ticket](#action-update-ticket) - Update ticket \(issue\)  
[add comment](#action-add-comment) - Add a comment to a ticket  
[list tickets](#action-list-tickets) - Get a list of tickets \(issues\) in a project  
[get ticket](#action-get-ticket) - Get ticket \(issue\) information  
[delete ticket](#action-delete-ticket) - Delete ticket \(issue\)  
[set status](#action-set-status) - Set ticket \(issue\) status  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'on poll'
Ingest tickets from Redmine

Type: **ingest**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**start\_time** |  optional  | Parameter ignored in this app | numeric | 
**end\_time** |  optional  | Parameter ignored in this app | numeric | 
**container\_id** |  optional  | Parameter ignored in this app | string | 
**container\_count** |  optional  | Maximum number of tickets to be ingested during poll now | numeric | 
**artifact\_count** |  optional  | Parameter ignored in this app | numeric | 

#### Action Output
No Output  

## action: 'create ticket'
Create a ticket \(issue\)

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**subject** |  required  | Title | string | 
**description** |  required  | Description of the ticket | string | 
**priority** |  optional  | Priority of the ticket | string | 
**tracker** |  optional  | Tracker type the ticket | string | 
**custom\_fields** |  optional  | JSON array containing custom field objects containing custom field id and value to set | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.custom\_fields | string | 
action\_result\.parameter\.description | string | 
action\_result\.parameter\.priority | string | 
action\_result\.parameter\.subject | string | 
action\_result\.parameter\.tracker | string | 
action\_result\.data\.\*\.issue\.author\.name | string | 
action\_result\.data\.\*\.issue\.id | string | 
action\_result\.data\.\*\.issue\.priority\.closed\_on | string | 
action\_result\.data\.\*\.issue\.priority\.created\_on | string | 
action\_result\.data\.\*\.issue\.priority\.name | string | 
action\_result\.data\.\*\.issue\.priority\.updated\_on | string | 
action\_result\.data\.\*\.issue\.project\.name | string | 
action\_result\.data\.\*\.issue\.status\.name | string | 
action\_result\.data\.\*\.issue\.subject | string | 
action\_result\.data\.\*\.issue\.tracker\.name | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'update ticket'
Update ticket \(issue\)

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | Issue ID | string | 
**update\_fields** |  optional  | JSON containing field values | string | 
**vault\_id** |  optional  | Vault ID of attachment | string |  `vault id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string | 
action\_result\.parameter\.update\_fields | string | 
action\_result\.parameter\.vault\_id | string |  `vault id` 
action\_result\.data\.\*\.issue\.author\.name | string | 
action\_result\.data\.\*\.issue\.id | string | 
action\_result\.data\.\*\.issue\.priority\.closed\_on | string | 
action\_result\.data\.\*\.issue\.priority\.created\_on | string | 
action\_result\.data\.\*\.issue\.priority\.name | string | 
action\_result\.data\.\*\.issue\.priority\.updated\_on | string | 
action\_result\.data\.\*\.issue\.project\.name | string | 
action\_result\.data\.\*\.issue\.status\.name | string | 
action\_result\.data\.\*\.issue\.subject | string | 
action\_result\.data\.\*\.issue\.tracker\.name | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'add comment'
Add a comment to a ticket

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | Issue ID | string | 
**comment** |  required  | Comment to add | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.comment | string | 
action\_result\.parameter\.id | string | 
action\_result\.data\.\*\.issue\.author\.name | string | 
action\_result\.data\.\*\.issue\.id | string | 
action\_result\.data\.\*\.issue\.priority\.closed\_on | string | 
action\_result\.data\.\*\.issue\.priority\.created\_on | string | 
action\_result\.data\.\*\.issue\.priority\.name | string | 
action\_result\.data\.\*\.issue\.priority\.updated\_on | string | 
action\_result\.data\.\*\.issue\.project\.name | string | 
action\_result\.data\.\*\.issue\.status\.name | string | 
action\_result\.data\.\*\.issue\.subject | string | 
action\_result\.data\.\*\.issue\.tracker\.name | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list tickets'
Get a list of tickets \(issues\) in a project

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**query** |  optional  | Additional parameters to query for in JQL | string | 
**start\_index** |  optional  | Start index of the list | numeric | 
**max\_results** |  optional  | Max number of issues to return | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.max\_results | numeric | 
action\_result\.parameter\.query | string | 
action\_result\.parameter\.start\_index | numeric | 
action\_result\.data\.\*\.issues\.\*\.author\.name | string | 
action\_result\.data\.\*\.issues\.\*\.id | string | 
action\_result\.data\.\*\.issues\.\*\.priority\.closed\_on | string | 
action\_result\.data\.\*\.issues\.\*\.priority\.created\_on | string | 
action\_result\.data\.\*\.issues\.\*\.priority\.name | string | 
action\_result\.data\.\*\.issues\.\*\.priority\.updated\_on | string | 
action\_result\.data\.\*\.issues\.\*\.project\.name | string | 
action\_result\.data\.\*\.issues\.\*\.status\.name | string | 
action\_result\.data\.\*\.issues\.\*\.subject | string | 
action\_result\.data\.\*\.issues\.\*\.tracker\.name | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get ticket'
Get ticket \(issue\) information

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | Ticket \(Issue\) Key | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string | 
action\_result\.data\.\*\.issue\.author\.name | string | 
action\_result\.data\.\*\.issue\.id | string | 
action\_result\.data\.\*\.issue\.priority\.closed\_on | string | 
action\_result\.data\.\*\.issue\.priority\.created\_on | string | 
action\_result\.data\.\*\.issue\.priority\.name | string | 
action\_result\.data\.\*\.issue\.priority\.updated\_on | string | 
action\_result\.data\.\*\.issue\.project\.name | string | 
action\_result\.data\.\*\.issue\.status\.name | string | 
action\_result\.data\.\*\.issue\.subject | string | 
action\_result\.data\.\*\.issue\.tracker\.name | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete ticket'
Delete ticket \(issue\)

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | Issue ID | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'set status'
Set ticket \(issue\) status

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | Ticket \(Issue\) Key | string | 
**status** |  required  | Status to set | string | 
**comment** |  optional  | Comment to set | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.comment | string | 
action\_result\.parameter\.id | string | 
action\_result\.parameter\.status | string | 
action\_result\.data\.\*\.issue\.author\.name | string | 
action\_result\.data\.\*\.issue\.id | string | 
action\_result\.data\.\*\.issue\.priority\.closed\_on | string | 
action\_result\.data\.\*\.issue\.priority\.created\_on | string | 
action\_result\.data\.\*\.issue\.priority\.name | string | 
action\_result\.data\.\*\.issue\.priority\.updated\_on | string | 
action\_result\.data\.\*\.issue\.project\.name | string | 
action\_result\.data\.\*\.issue\.status\.name | string | 
action\_result\.data\.\*\.issue\.subject | string | 
action\_result\.data\.\*\.issue\.tracker\.name | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 