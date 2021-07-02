# Validation

|                  |Internal          |External|
|---               | :---:            | :---: |
|**Communication** |Linting           | Validation % |
|                  |Documentation     | Statistics page|
|------------------|------------------|-----------------|
|                  |Unit tests        | Validation % |
|**Correctness**   |Integration tests | |
|                  |Validation report | |
|------------------|------------------|-----------------|
|**Performance**   |Timing log        | |

---
When creating any substantial change to the EMAP processes, we ensure that the changes produce the 
expected final state in the star database. 
We have unit and integration tests during development but we run an additional validation step that allows us to check

1. the data is not inferior to previous data
2. we meet a predetermined metric, usually 99%, compliance with other existing sources of data  

## Code validation

Unit tests are written to confirm the correct functionality of individual functions within the code. 
We also apply linting tests to check that code written conforms to particular standards involving naming conventions, whitespace used etc.
We use a continuous integration platform (Circle CI) to ensure that any code pushed to the repository passes these tests.  

## Integration tests

We write fake HL7 messages to allow the system to be tested as a pipeline. 
These tests mimic the exact format of HL7 messages but with entirely synthetic data.
We manually curate the expected results of these messages as they traverse the pipeline.

Additionally the progress of every message is logged to allow the history of messages pertaining to an individul to be tracked and anomalies in the processing identified.

## Validation of data

### Validation schema

We maintain a non-public instance of the star schema 'star_validation' which we use for running parts or all of the pipeline with the express purpose of producing data that we can use for validation purposes. 

### Validation run

Since validation run is designed for testing purposes it can be by giving a specified set of dates on which to run the hl7 processor and/or the Hoover.
This means we can look at as little as a days worth of data, or more usually a week or month and in some cases may be a year depending on the feature we are explicitly looking to validate.

Typically a validation run involves starting off the hl7 processor, processing all the data for the time period specified.
Once the hl7 is processed the Hoover is started for the same time period. 
Obviously in production both run concurrently, however as this is a test environment it is useful to have them running separately so that we can identify any particular point of failure.

We record processing data for each run: start, end times, amount processed etc. as well as information on which code branches were used.
The number of days worth of data processed per day of the time taken to complete the validation run is calculated.
This allows us to monitor how long data is taking to process and provides data for comparison with code optimisations that we may undertake.

### Data comparison ##

We use Caboodle and Clarity as a reference data set.
We have developed an R package that queries the star_validation database and either Caboodle/Clarity for particular data, compares the resulting data and produces reports that identify matching and non-matching data. 
In some cases we apply a degree of tolerance, for example if a time comparison is within minutes, and have established a number of cases where data will not match (described in separate document).
If data does not match we review and potentially correct code or investigate that data to establish a potentially acceptable difference.
We aim to match data, with noted exceptions, to 99% accuracy or above.  