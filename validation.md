# Validation 

When creating any substantial change to the EMAP processes, we should ensure that the changes produce the 
expected final state in the star database. We have unit and integration tests during development but this allows 
us to test that we understand the real data flows. 

## Setting off a validation run

- Using DbForge drop all tables and sequences from existing schema that you will use (e.g. `star_validation`),
  the drop.sql file on the shared drive can be used for this :
  `\\sharefs6\UCLH6\EMAP\Shared\EmapSqlScripts\devops\drop.sql`
- On the GAE checkout up to date versions of all branches in the repository that uses the correct schema 
  (e.g. star_validation is in `/gae/star-validation`). Use tmux or screen if you don't hate yourself.
- in emap core directory run: 

```shell script
./emap-live.sh build # build all services
source scripts/validation/run_validation.sh # may want to give custom start and end run time 
```

## PR checklist

Suggested checklist for any pull requests for inform components, you can copy the text into your PR to help
keeping track of everything.

- [ ] From the UCLH data science desktop, a [validation run](#Setting off a validation run) has been set off
- [ ] [load times](https://teams.microsoft.com/l/channel/19%3Ad3a19685d37241fdbfceb9d30303ea1b%40thread.tacv2/tab%3A%3A20f76f5b-b0d0-45ad-a0a8-3777aa82628d?groupId=03f64fac-1f4f-447c-8a74-6fe0054cf06a&tenantId=1faf88fe-a998-4c5b-93c9-210a11d9a5c2) 
      in NHS teams has been populated with the run information 
- [ ] During the run, glowroot has been checked for any queries which are taking a substantial proportion of the
      total processing time. This can be useful to identify indexes that are required.
- [ ] After the run, look for any unexpected errors in the `etl_per_message_logging table`, the error_search.sql file
      on the shared drive can be used for this `\\sharefs6\UCLH6\EMAP\Shared\EmapSqlScripts\devops\error_search.sql`.
      Create an issue if an unexpected exception is found and is not related to the changed you've made, otherwise
      fix them!
- [ ] After the run, [load times](https://teams.microsoft.com/l/channel/19%3Ad3a19685d37241fdbfceb9d30303ea1b%40thread.tacv2/tab%3A%3A20f76f5b-b0d0-45ad-a0a8-3777aa82628d?groupId=03f64fac-1f4f-447c-8a74-6fe0054cf06a&tenantId=1faf88fe-a998-4c5b-93c9-210a11d9a5c2) 
      has been populated with end time
- [ ] Let Aasiyah know about the completed validation and give her information on the changes and where to start 
      with the validation
- [ ] Check validation report and give any feedback to Aasiyah if there are any changes needed on her side, 
      iterate on getting the validation to match at least 99% (validation and emap code).
