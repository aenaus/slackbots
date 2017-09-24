# Security Slackbot
##Some security enhancement bots for Slack workspaces.
Currenty the following operations are supported:
1) Sending Reminders to all  users in a Schedule

##Instructions:

###Server
Install Python 3.6 on a server of your choice, preferably linux( windows) so that you can add a  cronjob(scheduled task) that checks  if the script is running,  and if it's not, it starts it.

###Slack
Security settings review:
Go to  yourteamurl.slack.com/apps/manage/permissions
Approved Apps  <- Set this to ON
>
Only pre-approved apps can be installed by members

These people can manage Approved Apps and custom integrations
 Workspace Owners only	 Workspace Owners and selected members or groups (if the latter is checked the selected group should be only 'WorkSpace Admins'

Allow members to request additions to Approved Apps <- as you see fit , we don't allow
       
Then go to yourteamurlslack.com/apps/manage

Remove / disable all unknown (not added by you and don't know exactly what they are doing and why ) applications and confirurations from those!! It's important, since attackers may have generated API keys to gather information and  automate messaging actions


Then in order to create an APP for the reminders :
https://api.slack.com/apps   and select 'create new app'
Add a name and select the workspace for that APP
Go to Bot Users and 'Add a bot user'  for your application, select the 'always show my bot as online'
Select Oauth & Permissions and then go to Scopes :
Add the following : chat:write:bot  , reminders:write   , users:read  and save changes
Also, in the 'Restrict API token Usage' you should put for security the Static IP address of the server that will be running the scripts. Slack will  not allow other IP addresses to use the token.

Important : Since bot users cannot send reminders, the reminders will  appear as being requested by you. If you want another user to be showing as the sender of the reminders, you should go to Collaborators and  add that user as a collaborator and only then he will be able to install this application from the https://api.slack.com/apps    page


Then you should go to the 'install APP' section and 'install  app to workspace'
Then  on the install App section you will have one oauth access token and one bot user token. The first is for the user the second is for the bot.  Those Tokens are Private!! Treat those as passwords.

If you want the user that will generate the reminders to by another than you, after inviting him as collaborator  he should install the application and you will use his Oauth access token in the script.  And not yours. Bot token it's the same always
In the 'Basic information' you can customize logo, color etc.

