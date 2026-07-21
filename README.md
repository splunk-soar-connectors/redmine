# Redmine

Publisher: Splunk Community <br>
Connector Version: 1.0.1 <br>
Product Vendor: Redmine <br>
Product Name: Redmine <br>
Minimum Product Version: 4.9.39220

This app integrates with Redmine to perform several ticket management actions

### Configuration variables

This table lists the configuration variables required to operate Redmine. These variables are specified when configuring a Redmine asset in Splunk SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base_url** | required | string | Server URL |
**verify_server_cert** | optional | boolean | Verify Server Certificate |
**username** | optional | string | Username |
**password** | optional | password | Password |
**project_id** | required | string | Redmine Project ID |
**custom_fields** | optional | string | Comma-separated list of custom fields to extract from tickets |

### Supported Actions

[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration <br>
[on poll](#action-on-poll) - Ingest tickets from Redmine <br>
[create ticket](#action-create-ticket) - Create a ticket (issue) <br>
[update ticket](#action-update-ticket) - Update ticket (issue) <br>
[add comment](#action-add-comment) - Add a comment to a ticket <br>
[list tickets](#action-list-tickets) - Get a list of tickets (issues) in a project <br>
[get ticket](#action-get-ticket) - Get ticket (issue) information <br>
[delete ticket](#action-delete-ticket) - Delete ticket (issue) <br>
[set status](#action-set-status) - Set ticket (issue) status

## action: 'test connectivity'

Validate the asset configuration for connectivity using supplied configuration

Type: **test** <br>
Read only: **True**

#### Action Parameters

No parameters are required for this action

#### Action Output

No Output

## action: 'on poll'

Ingest tickets from Redmine

Type: **ingest** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**start_time** | optional | Parameter ignored in this app | numeric | |
**end_time** | optional | Parameter ignored in this app | numeric | |
**container_id** | optional | Parameter ignored in this app | string | |
**container_count** | optional | Maximum number of tickets to be ingested during poll now | numeric | |
**artifact_count** | optional | Parameter ignored in this app | numeric | |

#### Action Output

No Output

## action: 'create ticket'

Create a ticket (issue)

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**subject** | required | Title | string | |
**description** | required | Description of the ticket | string | |
**priority** | optional | Priority of the ticket | string | |
**tracker** | optional | Tracker type the ticket | string | |
**custom_fields** | optional | JSON array containing custom field objects containing custom field id and value to set | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.custom_fields | string | | |
action_result.parameter.description | string | | |
action_result.parameter.priority | string | | |
action_result.parameter.subject | string | | |
action_result.parameter.tracker | string | | |
action_result.data.\*.issue.author.name | string | | |
action_result.data.\*.issue.id | string | | |
action_result.data.\*.issue.priority.closed_on | string | | |
action_result.data.\*.issue.priority.created_on | string | | |
action_result.data.\*.issue.priority.name | string | | |
action_result.data.\*.issue.priority.updated_on | string | | |
action_result.data.\*.issue.project.name | string | | |
action_result.data.\*.issue.status.name | string | | |
action_result.data.\*.issue.subject | string | | |
action_result.data.\*.issue.tracker.name | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'update ticket'

Update ticket (issue)

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | Issue ID | string | |
**update_fields** | optional | JSON containing field values | string | |
**vault_id** | optional | Vault ID of attachment | string | `vault id` |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | | |
action_result.parameter.update_fields | string | | |
action_result.parameter.vault_id | string | `vault id` | |
action_result.data.\*.issue.author.name | string | | |
action_result.data.\*.issue.id | string | | |
action_result.data.\*.issue.priority.closed_on | string | | |
action_result.data.\*.issue.priority.created_on | string | | |
action_result.data.\*.issue.priority.name | string | | |
action_result.data.\*.issue.priority.updated_on | string | | |
action_result.data.\*.issue.project.name | string | | |
action_result.data.\*.issue.status.name | string | | |
action_result.data.\*.issue.subject | string | | |
action_result.data.\*.issue.tracker.name | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'add comment'

Add a comment to a ticket

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | Issue ID | string | |
**comment** | required | Comment to add | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.comment | string | | |
action_result.parameter.id | string | | |
action_result.data.\*.issue.author.name | string | | |
action_result.data.\*.issue.id | string | | |
action_result.data.\*.issue.priority.closed_on | string | | |
action_result.data.\*.issue.priority.created_on | string | | |
action_result.data.\*.issue.priority.name | string | | |
action_result.data.\*.issue.priority.updated_on | string | | |
action_result.data.\*.issue.project.name | string | | |
action_result.data.\*.issue.status.name | string | | |
action_result.data.\*.issue.subject | string | | |
action_result.data.\*.issue.tracker.name | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'list tickets'

Get a list of tickets (issues) in a project

Type: **investigate** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**query** | optional | Additional parameters to query for in JQL | string | |
**start_index** | optional | Start index of the list | numeric | |
**max_results** | optional | Max number of issues to return | numeric | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.max_results | numeric | | |
action_result.parameter.query | string | | |
action_result.parameter.start_index | numeric | | |
action_result.data.\*.issues.\*.author.name | string | | |
action_result.data.\*.issues.\*.id | string | | |
action_result.data.\*.issues.\*.priority.closed_on | string | | |
action_result.data.\*.issues.\*.priority.created_on | string | | |
action_result.data.\*.issues.\*.priority.name | string | | |
action_result.data.\*.issues.\*.priority.updated_on | string | | |
action_result.data.\*.issues.\*.project.name | string | | |
action_result.data.\*.issues.\*.status.name | string | | |
action_result.data.\*.issues.\*.subject | string | | |
action_result.data.\*.issues.\*.tracker.name | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'get ticket'

Get ticket (issue) information

Type: **investigate** <br>
Read only: **True**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | Ticket (Issue) Key | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | | |
action_result.data.\*.issue.author.name | string | | |
action_result.data.\*.issue.id | string | | |
action_result.data.\*.issue.priority.closed_on | string | | |
action_result.data.\*.issue.priority.created_on | string | | |
action_result.data.\*.issue.priority.name | string | | |
action_result.data.\*.issue.priority.updated_on | string | | |
action_result.data.\*.issue.project.name | string | | |
action_result.data.\*.issue.status.name | string | | |
action_result.data.\*.issue.subject | string | | |
action_result.data.\*.issue.tracker.name | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'delete ticket'

Delete ticket (issue)

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | Issue ID | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.id | string | | |
action_result.data | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

## action: 'set status'

Set ticket (issue) status

Type: **generic** <br>
Read only: **False**

#### Action Parameters

PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** | required | Ticket (Issue) Key | string | |
**status** | required | Status to set | string | |
**comment** | optional | Comment to set | string | |

#### Action Output

DATA PATH | TYPE | CONTAINS | EXAMPLE VALUES
--------- | ---- | -------- | --------------
action_result.parameter.comment | string | | |
action_result.parameter.id | string | | |
action_result.parameter.status | string | | |
action_result.data.\*.issue.author.name | string | | |
action_result.data.\*.issue.id | string | | |
action_result.data.\*.issue.priority.closed_on | string | | |
action_result.data.\*.issue.priority.created_on | string | | |
action_result.data.\*.issue.priority.name | string | | |
action_result.data.\*.issue.priority.updated_on | string | | |
action_result.data.\*.issue.project.name | string | | |
action_result.data.\*.issue.status.name | string | | |
action_result.data.\*.issue.subject | string | | |
action_result.data.\*.issue.tracker.name | string | | |
action_result.status | string | | success failed |
action_result.message | string | | |
action_result.summary | string | | |
summary.total_objects | numeric | | 1 |
summary.total_objects_successful | numeric | | 1 |

______________________________________________________________________

Auto-generated Splunk SOAR Connector documentation.

Copyright 2026 Splunk Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and limitations under the License.
