# PR checklist
<!--
    This checklist will be copied by a github actions bot as a comment on every PR
    for an emap repository. 
    So that there is only one checklist across all PRs for a set of changes,
    delete all of the automatically added comments on all but one of the PRs 
    (usually Emap-Core, but if Emap-Core is not involved then use your best judgement)
 -->

Default guide for a PR (if multiple PRs for the work, only keep one version of it and link to it on the other PRs)

- [ ] From the UCLH data science desktop, a [validation run](https://github.com/inform-health-informatics/emap_documentation/blob/develop/SOP/validation_run.md) has been set off
- [ ] [load times](https://teams.microsoft.com/l/channel/19%3Ad3a19685d37241fdbfceb9d30303ea1b%40thread.tacv2/tab%3A%3A20f76f5b-b0d0-45ad-a0a8-3777aa82628d?groupId=03f64fac-1f4f-447c-8a74-6fe0054cf06a&tenantId=1faf88fe-a998-4c5b-93c9-210a11d9a5c2)
in UCL teams has been populated with the run information
- [ ] During the run, glowroot has been checked for any queries which are taking a substantial proportion of the
total processing time. This can be useful to identify indexes that are required.
- [ ] After the run, look for any unexpected errors in the `etl_per_message_logging table`, the error_search.sql file
on the shared drive can be used for this `\\sharefs6\UCLH6\EMAP\Shared\EmapSqlScripts\devops\error_search.sql`.
Create an issue if you find an unexpected exception and is not related to the changes you've made, otherwise
fix them!
- [ ] After the run, [load times](https://teams.microsoft.com/l/channel/19%3Ad3a19685d37241fdbfceb9d30303ea1b%40thread.tacv2/tab%3A%3A20f76f5b-b0d0-45ad-a0a8-3777aa82628d?groupId=03f64fac-1f4f-447c-8a74-6fe0054cf06a&tenantId=1faf88fe-a998-4c5b-93c9-210a11d9a5c2)
has been populated with end time
- [ ] Let Aasiyah know about the completed validation and give her information on the changes and where to start
with the validation
- [ ] Check validation report and give any feedback to Aasiyah if there are any changes needed on her side,
iterate on getting the validation to match at least 99% (validation and emap code).
