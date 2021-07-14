# Numbering procedure 

Use only major and minor versions as we are unlikely to push patch releases to main branch.

When a release is made the repos that have changed need to be incremented.
The incrementation is done by taking the number of the highest numbered repo, incrementing by .1 and then **ALL changed repos** being updated to use that version number.

Thus version number updates may look like:

| REPO |    | Update A | Update A & C | Update B | Update A,B & C |
| :-:  |:-: | :-:      | :-:          | :-:      | :-:            |
| A    |2.0 | 2.1      | 2.2          |          | 2.4            |
| B    |2.0 |          |              | 2.3      | 2.4            |
| C    |2.0 |          | 2.2          |          | 2.4            |

This means that some repos may 'miss' a version number.
Since we are not aiming for any sort of backwards compatibility this should not be an issue.
  
The latest version of all repos will work together e.g. after **Update A & C** above A v2.2, B v2.0 and C v2.2 will work together.

There should never be the case where non-compatible versions have the same number – which would happen if in the table above the Update to A & C incremented A to v2.2 and C to v2.1.
A v 2.1 would not be compatible with C v 2.1. 