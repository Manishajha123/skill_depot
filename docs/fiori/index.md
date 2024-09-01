## SAP FIORI
Sap Fiori is a new user experience (UX) for sap software and application. It provides a set of applications that are used in regular business functions like work approvals, financial apps and calculation apps etc…
                                      Sap Fiori enables multiple devices application that allows users to start a process on their desktop/laptop and to continue that process on a smartphone or on a tablet.
## Design Principles
The design philosophy of SAP Fiori is based on five core principles. SAP Fiori user experience is role-based, adaptive, simple, coherent, and delightful.

## Type of Fiori app
SAP Fiori has three app types, each distinguished by their focus and infrastructure requirements:
i> Transactional apps
ii> Fact sheets
iii> Analytical apps

## SAP FIORI LAUNCHPAD :
Launchpad is the single entry point for all business users.
http://<host>.<domain>:<port>/sap/bc/ui5_ui5/ui2/ushell/shells/abap/Fiorilaunchpad.html?sap-client=<client>&sap-language=EN

## T-code:
- /n/UI2/FLP- Launchpad
- /n/UI2/FLPD_CUST- Launchpad Designer

## SAP FIORI LAUNCHPAD DESIGNER :
The Fiori launchpad designer is a tool to configure the tiles for static and dynamic Fiori apps.

HTTP://<host>.<domain>:<port>/sap/bc/ui5_ui5/sap/arsrvc_upb_admn/main.html?sap-client=<client>?scope=CUST
HTTP://<host>.<domain>:<port>/sap/bc/ui5_ui5/sap/arsrvc_upb_admn/main.html?sap-client=<client>?scope=CONF

## CATALOG : 
A catalog is a set of apps we want to make available for one role.
TWO WAYS OF SAP FIORI APPS IMPLEMENTATION :
- Standard Fiori apps
- Customized Fiori apps


- Standard Fiori apps
STEP 1. In the launchpad designer, click the + icon at the lower-left.

Step 2: Click on add / create button

Step 3: Click save
Step 4: We can use Standard SAP Catalogs which is will full fill our requirement, once we select catalog its tiles / Applications will be displayed on the right side

Step 5 :
Select the required Tile which you need to add to our catalog and drag it or Create Reference.


Step 6:
Once I drop in Create reference, a popup will be enabled to select under which need to add


Step 7: Select catalog which you created earlier


- Customized Fiori apps (ztodes)
STEP1: Create catalog ID:- Z*

Step: 2  Create tiles (dynamic, news, static tiles)


SEMANTIC OBJECT:  semantic identification of Fiori apps.
TARGET MAPPING :
Target mapping is part of the SAP Fiori launchpad configuration. It defines the target application, which is launched when clicking on a tile, on a link or within app-to-app navigation. 
TARGET MAPPING CREATION :
Step 8: Click on target mapping




SAP FIORI GROUP: 
A group is a subset of Applications from one or more catalogs. 

STEP 1: Now click on Group and click Create

 STEP: Give Title & ID and click on save


STEP 3: CLICK ON ADD

STEP 4: Once you click on add will get a list of tiles / Apps which we added On Catalog

STEP 5: Click on Add button which is bottom of the tile

STEP 6:We can also add other Apps/tiles from other Catalogs by searching in the search bar. 



STEP 7: WE have selected ANY Catalog and under  Catalog selected any numbers  Of Apps which are required





STEP 8: Click the back button and come to the main page



ROLE ASSIGNMENT
Step 1: In SAP Open PFCG Transaction.
Step 2:  Give the role name and click on the single role


Step 3: Give the description and long text

step4: Save
Step 5: Select Menu Tab and select Transaction Dropdown to select SAP Fiori Tile Catalog

Step 6: Once you select Fiori Catalog “Assign Catalog” Popup will be opened in catalog ID select from search and select Catalog which we created

Step 7: Clicks continue.



Step 8: repeat same to select Business Group

Step 9: Select Business Group we created
Step 10.Click Continue




Step 11. Go to User Tab and assign User ID to whom these new roles need to be assigned.

Step 12. Click Save














