# Granular Control of Attachment Security with User Criteria in ServiceNow

![Screenshot of Example Records](https://github.com/grafdigital/servicenow_attachment_ucsecurity/blob/master/screenshot.png?raw=true)

Even tough user criterias are meant for knowledge bases and catalog items, they provide a user-friendly way to dynamically specify a group of users with relation to permissions. Out of the box ServiceNow does only offer limited functionality when it comes to who can see a certain attachment. We developed a simple proof of concept to combine these two worlds to give you finer control over attachments to mimic behaviour from document management systems.

## How it works

For every attachment (if that table has been enabled for user criteria security) a new "Security Record" will be created that links this attachment to a user criteria. We modified the default attachment read ACL to check first for the availability of such a "Security Record" and evaluate its linked user criteria. If no "Security Record" is found we default to the old behaviour of "if you can see the parent record then you can see the attachment".

## Installation

- Download update set XML
- Load and commit update set on instance
- Create needed user criterias
- Configure affected tables in property "attachment.ucsecurity.tablesanddefaults"

## Limitations

- Only works with "task" records -> Can be changed by modifying the attachment ACL.
- Running user criterias per attachment isn't computationally cheap could have performance impacts.
- Proof of concept
