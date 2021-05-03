# OIC_WORKSHOP

This repository details how to create an integration from scratch and is designed to supplement a workshop. The workshop is as follows:
- Create a connection to ATP
  - ATP instance is created beforehand
- Create a connection to the OIC FTP Server
  - Embedded FTP Server can be enabled for the OIC instance
- Create an integration
- Integration (version 1.0.0) does this:
  - Pulls data from a specific CSV file on the FTP server
  - For each row of data from the CSV file, create a new row in the ATP table with a timestamp and your name
    - This allows users to check what data they have created
    - This method might change when I get better at SQL. Ideally all workshop attendees should not be able to query data from other users, but this is a workshop so this probably doesn't matter
- Activate the integration
- Trigger the integration
  - Users may use SQL Developer or Toad or other database applications to check if the data was created in the database (they have the wallet file so they should be able to run queries against the table).
- Track the integration for potential errors

There is also an optional additional exploration of OIC that workshop attendees can do if they complete early:
<ol>
<li>Add an email notification at the end of the integration that sends you an email if the integration successfully completes, as well as an attachment of the data that was inserted. Designated version is 1.1.0.</li>
<li>Add some error handling logic to the integration to avoid common errors, such as:<ul>
  <li>File not found on the FTP server</li>
  <li>Table not found in ATP</li>
  <li>Unable to write data to ATP</li></ul>
Designated version is 1.2.0.
</li></ol>

As of now only the first one will have written instructions here. All additional exploration options will have attendees create a new version of their integration so that all the work they have completed up to this point remains intact.

Other things to explore:
- You can perform some basic variable manipulation in the mapper. For instance, you can concatenate two strings together, like so: `concat("Hi, my name is ", $NAME)`.
- View the file server contents by going to **Settings > File Server > Files**. Note that you can make changes to the _folder_ structure, but you are unable to CRUD any of the _files_; for this, you will need to download tools like filezilla or cyberduck to connect to the file server. Please do not make any changes to the permissions of the **workshop** folder as this will break the lab.
- You can now write your own XSLT mappings in the "Code" tab of a mapper. This should only be used by experienced OIC users, as its definition is very strict and a small change can cause the mapper to fail. However, this enables you to perform otherwise impossible actions in the mapper using solely the drag-drop functionality, such as filtering items of a nested list (basically making the equivalent of a sql query against some kind of structured data). Read this [blog post](https://blogs.oracle.com/integration/edit-xslt-source-code-in-oic-mapper-ui) for more information.
