# MIST4610GroupProjectDataModel


# Team Name: Schema_Squad - Group 5

Team Members: 

Chex Schirripa [@Schirripa81](https://github.com/Schirripa81)

Roee Peled 

Luke Phillips [@lukephillips810](https://github.com/lukephillips810)

Grace Rogers 

Anika Rawi [@anikarawi](https://github.com/anikarawi)

Misael Rufael 

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


<img width="1555" height="964" alt="mb_SchemaSquad" src="https://github.com/user-attachments/assets/9f9cb6dc-9607-4d05-b62a-cfc02d76249b" />

Our database tracks each visit from scheduling through reimbursement. It stores who the patient and physician are, when and how the visit happened, what the encounter record says, which medications were prescribed, which referrals were made, and where each insurance claim stands. Dollar amounts are not stored, including charges, payments and copays, so we can see the status of a claim but not what it is worth. Diagnoses, vitals and lab results are also missing beyond the encounter's clinical record text, and the same goes for physician availability or schedules and for patient details past name and contact information.

# Data Dictionary 

<img width="3000" height="1316" alt="data_dictionary_1_Appointments" src="https://github.com/user-attachments/assets/d1f08985-41e7-4034-89cb-3a68b9a4091b" />
<img width="3000" height="2012" alt="data_dictionary_5_Prescriptions" src="https://github.com/user-attachments/assets/dc75eef7-251a-4e4c-a53c-1fd719adad92" />
<img width="3000" height="2052" alt="data_dictionary_4_Patients" src="https://github.com/user-attachments/assets/5ba1db3a-9327-4538-b1d3-81d2504d97c3" />
<img width="3000" height="2050" alt="data_dictionary_3_Medical_Encounters" src="https://github.com/user-attachments/assets/923347e8-0924-4fbc-a713-3b64e248ac04" />
<img width="3000" height="2166" alt="data_dictionary_2_Billing_Claims" src="https://github.com/user-attachments/assets/395deca5-36fc-40ae-8cfb-9810eefc7bd7" />

# Database Information

Schema name on the MySQL server: **SchemaSquad**

The database has 15 tables, and every table holds 50 rows of sample data.

<img width="1870" height="1445" alt="GPDEL4_SchemaSquad_PopulatedTables_page5" src="https://github.com/user-attachments/assets/d494fd11-6203-4789-86b3-827214933e50" />
<img width="1870" height="1445" alt="GPDEL4_SchemaSquad_PopulatedTables_page4" src="https://github.com/user-attachments/assets/59cabe93-814b-4569-96cb-8d1a99328fca" />
<img width="1870" height="1445" alt="GPDEL4_SchemaSquad_PopulatedTables_page3" src="https://github.com/user-attachments/assets/e92b965b-dfa3-4d59-903c-d3729f30f089" />
<img width="1870" height="1445" alt="GPDEL4_SchemaSquad_PopulatedTables_page2" src="https://github.com/user-attachments/assets/aaa40f40-3c3d-4e8f-b1c6-7b5f41fedc1f" />
<img width="1870" height="1445" alt="GPDEL4_SchemaSquad_PopulatedTables_page1" src="https://github.com/user-attachments/assets/bb9e3158-c463-4cba-a7dd-3374dca86678" />


# Queries:




