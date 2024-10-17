## What is CAP?

The SAP Cloud Application Programming Model (CAP) is a framework of languages, libraries, and tools for building enterprise-grade services and applications. 

**Create a new project:- terminal -> new Terminal -> command "cds init PROJECTSPECCIFNAME".** 

## Project Structure
The default project structure of CAP projects is as follows:

---

Folders:-

The project folder may include subfolders for different purposes, such as: 

**app: For creating the UI**

**db: For creating files to define the application data model**

**srv: For placing files of your service definition and business logic** 

---

Files:-
The project folder may include files such as: 

**cdsrc.json: For specifying settings to be used across multiple projects**

**package.json: For holding project specific configuration**

**README.md: For project documentation**

---


**Database :**
The most important things is about the database. **During the application development time we uses the SQLite database**, without changing much, we can easily move the application to **HANA DB for production**.

**Command for run the app**
**cds watch**: watches for changes in the CDS model
**cds run**: run the app
