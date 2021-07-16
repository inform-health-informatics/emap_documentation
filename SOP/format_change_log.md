# Formatting ChangeLog

The text shown here should be copied into the ChangeLog document with the appropriate information added.
It should also be copied to the Release Announcements document after appropriate information has been added, with the exception of the Repositories Version section.

---

## EMAP Release

**Date: YYYY-MM-DD**

### Tables changed

| Table           | Attributes added | Attributes removed |
| :-              |:-                |:-                  |
| hospital_visit  | new_att          |                    |
| location        |                  | old_att            |

#### Explanation

hospital_visit.new_att was added to ...

location.old_att was removed because ...

### Additional tables

#### table_xyz

- add image ?

This captures information about ...

#### another_new_table

- add image ?

This captures information about ...

### Deprecated tables

#### table_gone1

This table is gone because ...

### Data sources

hospital_visit.new att comes from the live HL7 feed.

table_xyz coms from the SDE interface that is updated every 15 minutes.

another_new_table comes from caboodle that is updated every 24 hours.

### Repository Versions

| Repository            | Version |
| :-                    | :-:     |
|Hl7-processor          | 2.0     |
|Emap_interchange       | 2.0     |
|Emap-Core              | 2.0     |
|Inform-DB              | 2.0     |
|Hoover                 | 2.0     |
