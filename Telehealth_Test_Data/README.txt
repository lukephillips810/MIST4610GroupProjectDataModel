TELEHEALTH SYNTHETIC TEST DATA
15 tables; 50 rows per table; 750 total rows. All records are fictional.
Every image attribute has a value. Foreign-key columns were inferred from
the diagram relationships because the image does not explicitly list them.
Match those column names to your actual database schema before importing.
Prescription values are intentionally nonclinical test placeholders.
Dates: YYYY-MM-DD. Datetimes: YYYY-MM-DD HH:MM:SS. Encoding: UTF-8.
IDs: integer primary/foreign keys. member_ID and group_ID: text.
All appointments are completed to support populated encounters.
All enrollment periods contain the appointment dates.
physician_clinic_ID is populated on telehealth rows to identify the physician's
affiliated clinic; it does not imply physical attendance.
Each referring physician differs from the referred physician.

IMPORT INTO MYSQL WORKBENCH
Extract this ZIP first. Import one CSV into its matching table using
Table Data Import Wizard. Treat the first row as column headers.
Use existing tables and map headers to existing columns where possible.
If your tables use ENUM columns, map status strings to your allowed values.
Do not import README.txt as a table.
Import order:
1. Specialties.csv
2. Physicians.csv
3. Clinics.csv
4. Patients.csv
5. Insurance_Providers.csv
6. Medications.csv
7. Physician_Specialties.csv
8. Physician_Clinics.csv
9. Insurance_Plans.csv
10. Patient_Enrollments.csv
11. Appointments.csv
12. Medical_Encounters.csv
13. Billing_Claims.csv
14. Referrals.csv
15. Prescriptions.csv

VALIDATION
50 unique primary keys in every table; no empty fields; all included
foreign keys resolve to existing parent rows in this data package.
Use an empty test schema to avoid conflicting with existing IDs 1 through 50.
