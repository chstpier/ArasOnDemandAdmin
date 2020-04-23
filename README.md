## Aras On Demand Admin

Allows system administrators to temporarily gain Administrators privileges in Aras.

The idea is to assign an Identity to some people, giving them access to an action which makes them member of the Administrators Identity.

This Aras package adds 2 actions and an optional scheduled job.
 1. The first action named OnDemandAdmin_Elevate is used to become member of the Administrators Identity.
 2. The second action named OnDemandAdmin_Revoke is used to remove access to the Administrators Identity.
 3. Optionally, a scheduled job can be installed that will revoke the access automatically after a predefined amount of time.

### Installation

Import the package using the Aras Import tool.
 1. Select the imports.mf file.
 2. In the 'Available for Import' section, select OnDemandAdmin.
 3. In the 'Type' section select 'Merge'.
 
### Automatic revoke using a scheduled job

Every hour, the job will revoke all users member on 'On Demand Admin' that have been Administrator for more than 8 hours or value defined in the OnDemandAdmin_Delay_Hours Variable.

 1. Install the Aras Scheduler Service 
 2. In InnovatorServiceConfig.xml, add a new job.
 Example:
 
		<job>
			<method>OnDemandAdmin_RevokeAll</method>
			<months>*</months>
			<days>*</days>
			<hours>*</hours>
			<minutes>17</minutes>
		</job>
 3. Restart the scheduler service.
 

 
 ### Usage
 
 1. Assign the On Demand Admin Identity to the users that need to perform administrator tasks.
 2. After the next login, those users will see the action to Elevate or Revoke Administrator privileges.
 3. After the next login, those users will get their updated privileges.

