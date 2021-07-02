# Validation Issues

These are issues we have encountered where it is not viable to match data exactly or data must be processed before it can be matched.

## Letter case and whitespace

At times there is a mismatch in case of text stored in the reference databases.
EMAP processes HL7 messages exactly as it receives them.
Data in the reference databases can be 'corrected' without an HL7 message being triggered, and thus essentially changed without EMAP being aware.

There may be a mismatch on white space.
For example, Clarity stores results on separate lines, whilst EMAP puts them on one line.

Thus, to exactly match text it is necessary to adjust case and whitespace in the text messages.

## Timestamps

Using Caboodle, it is possible to edit data without the LastUpdatedTime field associated with this ata being changed.
This presents an immediate problem, since the actual time the data was last updated is not recorded as the LastUpdatedTime, making matching impossible.

## Location information

EMAP does not have mortuary information.
The patient appears to be staying where they were previously admitted.
Caboodle leaves a gap between visits when the patient is in the mortuary.

Some EMAP locations don’t match with caboodle ones. These don’t show up in covid_staging.locations.

Caboodle leaves a gap between bed stays when a patient has a leave of absence, or is tagged as AMUBLATORY or HOTEL.

Caboodle and EMAP don’t agree on a when a patient is in a chemotherapy discharge room.

## Delays in HL7 messages

Some HL7 messages are extremely delayed, and so don’t end up in EMAP at the time we expect.
This can result in EMAP having an old MRN, while caboodle has the new one. The CSNs stay the same.

# Validation Exceptions

1. We allow a time difference of less than 15 minutes to match.

2. Exclude leave of absence, hotel, home, and ambulatory patients.

3. Exclude locations which won’t join.

4. Exclude non-matching vists of dead patients.

5. Exclude visits which join on CSN, but not MRN (this does not apply to ops).

6. Exclude just the chemotherapy visits which don’t join.
