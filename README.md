# OIC_WORKSHOP

This repository details how to create an integration from scratch and is designed to supplement a workshop. The workshop is as follows:
- Create a connection to ATP
  - ATP instance is created beforehand
- Create a connection to the OIC FTP Server
  - Embedded FTP Server can be enabled for the OIC instance
- Create an integration
- Integration (version 1.0) does this:
  - Pulls data from a specific CSV file on the FTP server
  - For each row of data from the CSV file, create a new row in the ATP table with a timestamp and your name
    - This allows users to check what data they have created
    - This method might change when I get better at SQL. Ideally all workshop attendees should not be able to query data from other users, but this is a workshop so this probably doesn't matter
- Activate the integration
- Trigger the integration
  - Users may use SQL Developer or Toad or other database applications to check if the data was created in the database (they have the wallet file so they should be able to run queries against the table).
- Track the integration for potential errors

There is also an optional additional exploration of OIC that workshop attendees can do if they complete early:
1. Add an email notification at the end of the integration that sends you an email if the integration successfully completes, as well as an attachment of the data that was inserted.
2. Add some error handling logic to the integration to avoid common errors, such as:
  - File not found on the FTP server
  - Table not found in ATP
  - Unable to write data to ATP

As of now only the first one will have written instructions here.

Other things to explore:
- You can now write your own XSLT mappings in the "Code" tab of a mapper. This should only be used by experienced OIC users, as its definition is very strict and a small change can cause the mapper to fail.
