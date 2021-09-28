# Background for EMAP

While the focus of the Experimental Medicine Application Platform (EMAP) is the integration of different kinds of data
from trusted sources, it is important to acknowledge common concepts for all the different types of data. 
EMAP aims to provide a real-time view on the current situation of a hospital; e.g. how many beds are occupied on a ward or which patients need short supply, perishable medication at 
any point in time. This involves variety of hospital and data-flows that are outlined here.


## Patient journey when coming to the hospital

Patients are admitted to hospital for various reasons, but the importance for the EMAP pipeline is what happens to these
patients while they are in hospital. Let's assume that someone had a sporting accident and twisted their ankle and 
because all GPs are closed, they are attending the A&E unit of a hospital to seek appropriate treatment. 

Upon arrival, each patient is registered and receives a priority based on the condition they are in. While the first 
registration is typically conducted through a nurse, the decision on what needs to happen in terms of diagnostics and 
treatment typically lies with a doctor. So for the patient with the painful ankle, they would talk to a doctor, who may refer them for an X-ray to be taken on a specific ward. The 
patient is taken, either by medical staff or by making their own way to a different location in the hospital to take 
the X-ray. Once that has finished, the patient is then sent back to their consulting doctor and based on the 
image taken, the doctor decides how best the patient can eb aided, e.g. whether a plaster is appropriate because 
the bone is fractured or pain killers suffice as it was simple sprain. 

It is important to note that this is a very simple example for illustration purposes and depending on the complications
experienced by a patient, they may be admitted into hospital for a period of time, being operated on to stabilise 
their conditions, or they might come back after having been released from hospital with potential new conditions. 

Nonetheless, we see some important concepts emerge from this simplistic example that are important for understanding 
what data needs to be governed in a hospital at real-time: 

* information about people in the hospital such as patients, doctors and nurses
* key information about the patient, e.g. demographics (age, ethnicity, etc.), but also their past medical history, 
  medication they are regularly taking, allergies, advanced care decisions and so on
* diagnostic instruments and the output thereof, such as laboratory results or imaging
* locations where either diagnostics or treatments are happening (e.g. wards, operation theatres or special units)
* important time points on a patient journey, e.g. admission and duration of a hospital stay, number of hospital visit 
  for a condition and
* medication/treatments administered to patients while in the hospital

Any data pipeline employed in a hospital setting must be able to handle these different concepts adequately. In order to
understand how the EMAP pipeline is handling these concepts, it is best to start reading the [technical overview of the
pipeline](./Technical_overview_of_EMAP.md).
