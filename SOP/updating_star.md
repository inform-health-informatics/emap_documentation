# Updating public facing star instance

We have two versions of the public facing star database, star_a and star_b.
Views are created so that users need only query star.
When we add data or fix issues we can change the instance pointed to by star and thus avoid outages as the old version continues to run while the new version loads in data.

## Procedure

   1. Delete all data in the instance to be repopulated using script ....

   1. Taking note of which branches of each repository are being used.

   1. Start off a run into the empty db.

   1. Validate the run when finished.

   1. If all is good, update the version number as detailed [here](repo-versioning.md) and push the branches used to main.

   1. Update the star redirect using script ...

   1. Detail any changes in the ChangeLog.
