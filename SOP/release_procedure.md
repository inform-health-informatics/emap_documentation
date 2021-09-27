# Release Procedure


We have two versions of the public facing star database, star_a and star_b.
Views are created so that users need only query star.
When we add data or fix issues we can change the instance pointed to by star and thus avoid outages as the old version continues to run while the new version loads in data.

## Decision to release

When we have finished a new data item or added some requested features we decide on a target date.
At this point we create a list in the planner with vital things to be completed before release and a release task which lists the following subtasks


## Procedure

   1. Delete all data in the instance to be repopulated using script 
      `\\sharefs6\UCLH6\EMAP\Shared\EmapSqlScripts\devops\drop.sql`

   1. Taking note of which branches of each repository are being used.

   1. Start off a run into the empty db.

   1. Validate the run when finished.

   1. If all is good, copy the zip file for the validation to UCLH Teams: [(UCLH) EMAP Team > General > validation_runs/](https://teams.microsoft.com/_#/files/General?threadId=19%3Aff1802fc10694e648652c0c93a54882f%40thread.tacv2&ctx=channel&context=validation_runs&rootfolder=%252Fsites%252Fmsteams_7131aa%252FShared%2520Documents%252FGeneral%252Fvalidation_runs)
   
   1. Update the version number as detailed [here](repo-versioning.md) and push the branches used to main.

   1. Update the star redirect using function in UDS , e.g. `SELECT star.make_views('star_a', 'star');`

   1. Detail any changes in the ChangeLog.

   1. Create any queries to demonstrate new features and add to DBCookbook, add a link to these in the changelog. 

   1. Arrange date for demo.

   1. Write release announcement [(- see template)](./tmp_release_announce.md)
      1. Send to EMAP Users list (ask Richard Clarke).

      2. Post on NHS Teams -> Data Science Community -> EMAP users channel

   1. Prepare and do demo.

   1. Shut down old instance.  
