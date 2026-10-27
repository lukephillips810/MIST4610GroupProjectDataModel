# MIST4610GroupProjectDataModel


# Team Name: Schema_Squad - Group 5

Team Members: 

Chex Schirripa [@Schirripa81](https://github.com/Schirripa81)

Roee Peled rp46411@uga.edu

Luke Phillips [@lukephillips810](https://github.com/lukephillips810)

Grace Rogers ger42695@uga.edu

Anika Rawi [@anikarawi](https://github.com/anikarawi)

Misael Rufael mhr85142@uga.edu

# Problem Description:
The task at hand is to model and build a relational database for a telehealth patient and provider portal. The central entity in the model is the Appointment, which connects a patient to a physician, either virtually or in person at one of the physical clinics where the physician works. Physicians can hold multiple specialties, and patients are covered by insurance plans, offered by insurance providers, through enrollments that track when coverage starts and ends. Each appointment that takes place is documented by a medical encounter, which can lead to prescriptions for medications, referrals to other physicians, and billing claims sent to the patient's insurance plan. An encounter cannot be closed until a billing record is linked to an insurance claim, so we can follow every visit through to reimbursement. We are interested in accurately modeling these relationships, generating sample data, and populating the entities and their attributes with this sample data. Furthermore, we are interested in performing functioning queries on this data so that they may provide valuable business insight into the portal's virtual clinic throughput and insurance reimbursement.

# Data Model
Explanation of data model:

Our model is built around the Appointment, which is the moment a patient and a physician connect through the portal. A Patient schedules zero or many Appointments, and a Physician provides zero or many Appointments. Each visit is either Virtual or In Person, and each appointment has a status of Scheduled, Completed or No Show.

To understand who is providing care, we start with the Physician. A physician can hold one or many specialties, and a specialty can belong to many physicians, so Physician_Specialties resolves that many to many relationship. Physicians also work at zero or many clinics, and a clinic can host many physicians, so Physician_Clinics handles that link. Clinics are physical locations only. An In Person appointment points to one Physician_Clinics record, which ties the visit to a clinic where that physician actually works, while a Virtual appointment has no clinic at all.

On the patient side, we track insurance coverage over time. Insurance_Providers has a one to many relationship with Insurance_Plans, since a provider offers many plans but each plan belongs to just one provider. Patient_Enrollments ties a patient to a plan for a stretch of time and stores the start date, end date, member ID and group ID. A patient can have one or many enrollments over the years, but only one can be active at a time, and a single plan can cover many enrollments.

When a visit actually happens, it is recorded in a Medical_Encounter. An appointment is documented by zero or one encounter, since only appointments that happen produce one, so that relationship is one to zero or one. The encounter holds the clinical record and whether the encounter is Open or Closed.

Care often ends with a prescription. An encounter produces zero or many Prescriptions, and each prescription is for one Medication, though a medication can show up on many prescriptions. Each prescription also stores the dosage and how long the patient should take it.

After the visit comes billing. An encounter is billed through one or many Billing_Claims, because a claim can be resubmitted after a denial, and each claim is funded by one Insurance_Plan. A claim’s status is Submitted, Approved, Denied, Resubmitted or Paid. An encounter cannot be Closed until a billing claim is linked to it, so every visit is followed through to reimbursement.

Finally, one physician sometimes sends a patient to another. Referrals is an associative entity that connects two Physicians, the referring physician who sends it and the receiving physician who gets it, which makes it a recursive many to many relationship on Physicians. Each referral is also tied to the Patient being referred and to the Medical_Encounter that triggered it. Each referral results in zero or one Appointment, and an appointment comes from at most one referral, which brings the story back to where it started.


<img width="2475" height="1327" alt="Group5Model" src="https://github.com/user-attachments/assets/3cbc4d8d-cac7-4934-ac50-bb8a4a372c9f" />


# Data Dictionary 

<img width="3000" height="1316" alt="data_dictionary_1_Appointments" src="https://github.com/user-attachments/assets/9323d356-7b0c-473a-b64a-d55e5a71c70f" />
<img width="3000" height="2012" alt="data_dictionary_5_Prescriptions" src="https://github.com/user-attachments/assets/ed09c62a-23af-4534-be30-3a498d53b58c" />
<img width="3000" height="2052" alt="data_dictionary_4_Patients" src="https://github.com/user-attachments/assets/eb15ae3c-6cb6-4f52-af1b-045e2ff5e75e" />
<img width="3000" height="2050" alt="data_dictionary_3_Medical_Encounters" src="https://github.com/user-attachments/assets/ccd769c7-e039-4348-91fa-557207c8fc19" />
<img width="3000" height="2166" alt="data_dictionary_2_Billing_Claims" src="https://github.com/user-attachments/assets/4defe10c-04d2-4f60-b839-d51807ff403c" />

# Queries:




