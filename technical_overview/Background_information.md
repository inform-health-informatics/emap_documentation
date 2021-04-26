# Background for EMAP

While the focus of the Experimental Medicine Application Platform (EMAP) is the integration of different kinds of data
from trusted sources, it is important to acknowledge common concepts for all the different types of data. The data that
is collected through EMAP is to provide a real-time view on the current situation of a hospital and as such provide 
information such as how many beds are occupied on a ward or which patients need short supply, perishable medication at 
any point in time. This creates a variety of information that needs to be coordinated and the different actors are to be
outlined here.


## Patient journey when coming to the hospital

Patients are admitted to hospital for various reasons, but the importance for the EMAP pipeline is what happens to these
patients while they are in hospital. Let's assume that someone had a sporting accident and twisted their ankle and 
because all GPs are closed, they are attending the A&E unit of a hospital to seek appropriate treatment. 

Upon arrival, each patient is registered and receives a priority based on the condition they are in. While the first 
registration is typically conducted through a nurse, the decision on what needs to happen in terms of diagnostics and 
treatment typically lies with a GP. So for the patient with the painful ankle, in the next step they would be talking to
a GP, who may refer them for an X-ray to be taken on a very specific ward. So for that purpose the patient is taken, 
either by medical staff or by making their own way to a different location in the hospital to take the X-ray. Once that
has finished, the patient is then sent back to the GP they talked to before and based on the image taken, the GP 
decides what is best in the case of the patient, e.g. whether a plaster is appropriate because the bone is fractured or
pain killers suffice as it was more of a shock than any damage taken to the physical structure of the patient. 

From this examples, we see some important concepts emerge that are important for understanding what is happening in a 
hospital at any one point in time: patients, GPs, nurses, diagnostic instruments and people being able to operate this 
equipment, locations (e.g. wards or special units), time of admission and duration of a hospital stay, and 
medication/treatment received while staying in the hospital. 

Any data pipeline employed in a hospital setting must be able to handle these different concepts adequately. 