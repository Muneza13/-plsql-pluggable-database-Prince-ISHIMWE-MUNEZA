Oracle Pluggable Database (PDB)  Report
**Author:** Prince ISHIMWE MUNEZA
**Course:** Database Development with PL/SQL (INSY 8311)   
**Institution**: Adventist University of Central Africa (AUCA)  
**Instructor**: Eric Maniraguha  
**Assignment**: Individual Assignment II
**Submission Date**: 7 October, 2025

Executive Summary
This report documents the completion of three tasks involving Oracle Pluggable Database (PDB) management: creating a working PDB for coursework, creating and deleting a temporary PDB, and configuring Oracle Enterprise Manager (OEM) for database monitoring.

Task 1: Create a New Pluggable Database (PDB)

Implementation Details
PDB Name: pr_pdb_27816
Username: prince_plsqlauca_27816
Password: 12345
SQL Commands Used
--CREATING PLUGGABLE DATABASE
CREATE PLUGGABLE DATABASE pr_pdb_27816
ADMIN USER prince_plsqlauca_27816 IDENTIFIED BY 12345
FILE_NAME_CONVERT = ('pdbseed', 'pr_pdb_27816');
---
![CREATING PLAG](https://github.com/user-attachments/assets/4acdc75e-3a02-4a02-a301-9dfff2c3658b)

Task 1 Results

✅ PDB pr_pdb_27816 created successfully
✅ User account prince_plsqlauca_27816 configured with appropriate privileges
✅ PDB opens automatically on database startup


Task 2: Create and Delete a PDB
Objective
Demonstrate the ability to create and properly remove a PDB from the container database.
Implementation Details
Temporary PDB Name: pr_to_delete_pdb_27816
---
SQL Commands Used
-- Creating the second PDB and delete
CREATE PLUGGABLE DATABASE pr_to_delete_pdb_27816
ADMIN USER prince_pisqlauca_27816 IDENTIFIED BY 12345
FILE_NAME_CONVERT = ('pdbseed', 'pr_to_delete_pdb_27816');
---
![second pb](https://github.com/user-attachments/assets/797bc7bf-ed1e-4b7f-8f9f-23e746163151)
-- Droping the PDB
DROP PLUGGABLE DATABASE sa_to_delete_pdb_27969 INCLUDING DATAFILES;
---
![deleting plag](https://github.com/user-attachments/assets/764012d7-8418-4828-9076-0a1473156d6b)
---

Task 2 Results

✅ Temporary PDB pr_to_delete_pdb_27816 created successfully
✅ PDB deleted completely with all datafiles removed
✅ Verified PDB no longer exists in the container database
---


Task 3: Oracle Enterprise Manager (OEM)
Objective
Configure and access Oracle Enterprise Manager Database Express for database monitoring.
---
SELECT DBMS_XDB_CONFIG.GETHTTPSPORT() FROM DUAL;
then i saw that i use this link "https://localhost:5500/em/login"
--------
![configuration OEM](https://github.com/user-attachments/assets/1d85f63a-f5a0-473a-bec6-b594a46e8092)
![OEM](https://github.com/user-attachments/assets/03db05fd-2cea-40d5-bca0-efbc5d667182)
and connecting pdbs
![connecting pdbs](https://github.com/user-attachments/assets/00856713-1784-45dd-be13-6f1433eb4684)

---
Task 3 Results

✅ OEM configured successfully on port 5500
✅ Dashboard accessible via web browser
✅ Username prince_plsqlauca_27816 visible in screenshots


Issues Encountered and Solutions

Issue 1: FILE_NAME_CONVERT Path Error
Problem: Initial PDB creation failed due to incorrect file path conversion
Solution: Verified correct source and destination paths using:
sqlSELECT name FROM v$datafile WHERE con_id = 2;
Then adjusted FILE_NAME_CONVERT accordingly.

Issue 2: PDB Not Opening After Creation
Problem: PDB remained in MOUNTED state after creation
Solution: Explicitly opened the PDB using:
sqlALTER PLUGGABLE DATABASE pr_pdb_27816 OPEN;

Issue 3: OEM Access Denied
Problem: Could not access OEM dashboard initially
Solution: Ensured XML DB HTTP Server was running and port was configured correctly. Restarted listener service.


Conclusion
All three tasks have been completed successfully within the required timeframe. The working PDB pr_pdb_27816 is ready for all coursework throughout the semester. Oracle Enterprise Manager has been configured to provide ongoing monitoring and management capabilities.

Additional Resources

Oracle Multitenant Documentation
Oracle Enterprise Manager Documentation
PDB Administration Best Practices


Contact Information
For any questions regarding this submission:

Email: ishimwemunezaprince@gmail.com
phone: 250798552735

Hebrews 11:1: "Now faith is the assurance of things hoped for, the conviction of things not seen".
