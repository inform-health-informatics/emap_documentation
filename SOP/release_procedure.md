# Release Procedure


We have two versions of the public facing star database, star_a and star_b.
Views are created so that users need only query star.
When we add data or fix issues we can change the instance pointed to by star and thus avoid outages as the old version continues to run while the new version loads in data.

## Decision to release

When we have finisghed a new data item or added some requested features we decide on a target date.
At this point we create a list in the planner with vital things to be completed before release and a release task which lists the following subtasks


## Procedure

   1. Delete all data in the instance to be repopulated using script {@stef is this script in a repo somewhere and can it be named if not linked from here}

   1. Taking note of which branches of each repository are being used.

   1. Start off a run into the empty db.

   1. Validate the run when finished.

   1. If all is good, update the version number as detailed [here](repo-versioning.md) and push the branches used to main.

   1. Update the star redirect using script {@stef is this script in a repo somewhere and can it be named if not linked from here}

   1. Detail any changes in the ChangeLog.

   1. Create any queries to deemonstrate new features and add to DBCookbook.

   1. Arrange date for demo.

   1. Write release announcement and
      1. Send to EMAP Users list (ask Richard Clarke).

      2. Post on NHS Teams -> Data Science Community -> EMAP users channel

   1. Prepare and do demo.

   1. Shut down old instance.  
