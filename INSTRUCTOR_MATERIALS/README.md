# Instructor instructions

Prior to beginning the workshop, the following items need to be completed:

## Prerequisites

1. Create tenancy
2. Provision OIC
   - Settings for OIC instance vary from customer to customer; use best judgment or ask someone experienced
3. Provision ATP
   - Can be basically all default settings

## OIC setup

1. In IDCS, add all OIC users to all roles in the OIC cloud service
2. Enable file server for OIC
3. In the file server settings, enable all users with default setting
4. Create a folder called "workshop" under the home directory and enable full access for all users to the directory
5. Using SQL Developer create a new table called `WORKSHOP` with all the columns of person.csv, and two more columns: timestamp and user name
   - It might be helpful to just upload person.csv, then delete all the data and create the extra columns. Finally make timestamp the only primary key column
SQL used to generate my table:
```
  CREATE TABLE "ADMIN"."WORKSHOP" 
   (	"FNAME" VARCHAR2(26 BYTE) COLLATE "USING_NLS_COMP", 
	"LNAME" VARCHAR2(26 BYTE) COLLATE "USING_NLS_COMP", 
	"EMAIL" VARCHAR2(26 BYTE) COLLATE "USING_NLS_COMP", 
	"PHONE" NUMBER(38,0), 
	"BID" NUMBER(38,0), 
	"TIMESTAMP" DATE NOT NULL ENABLE, 
	"CREATED_BY" VARCHAR2(255 BYTE) COLLATE "USING_NLS_COMP", 
	 CONSTRAINT "WORKSHOP_PK" PRIMARY KEY ("TIMESTAMP")
  USING INDEX PCTFREE 10 INITRANS 20 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "DATA"  ENABLE
   )  DEFAULT COLLATION "USING_NLS_COMP" SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 10 MAXTRANS 255 
 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "DATA" ;
```