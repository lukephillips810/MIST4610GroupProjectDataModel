# MIST4610GroupProjectDataModel


# Team Name: Schema_Squad - Group 5

Team Members: 

Chex Schirripa fcs42496@uga.edu 

Roee Peled rp46411@uga.edu

Luke Phillips lkp21071@uga.edu

Grace Rogers ger42695@uga.edu

Anika Rawi ar67889@uga.edu

Misael Rufael mhr85142@uga.edu

# Problem Description:
The task at hand is to model and build a relational database for a telehealth patient and provider portal. The central entity in the model is the Appointment, which connects a patient to a physician, either virtually or in person at one of the physical clinics where the physician works. Physicians can hold multiple specialties, and patients are covered by insurance plans, offered by insurance providers, through enrollments that track when coverage starts and ends. Each appointment that takes place is documented by a medical encounter, which can lead to prescriptions for medications, referrals to other physicians, and billing claims sent to the patient's insurance plan. An encounter cannot be closed until a billing record is linked to an insurance claim, so we can follow every visit through to reimbursement. We are interested in accurately modeling these relationships, generating sample data, and populating the entities and their attributes with this sample data. Furthermore, we are interested in performing functioning queries on this data so that they may provide valuable business insight into the portal's virtual clinic throughput and insurance reimbursement.

The database has 15 tables. The conceptual model (no foreign keys shown) is below, followed by the physical model from MySQL Workbench.

