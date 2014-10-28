![Alt Text](https://github.com/humazafar/testRepo/blob/master/Cobone.png?raw=true)

# Technical Design Document

![Alt Text](https://github.com/humazafar/testRepo/blob/master/Raawee.png?raw=true)

<!--BREAK-->

## Document Revision History Log
| Date | Version  | Name  | Changes Description | Sections Impacted  |
|:-:|:-:|:-:|:-:|:-:|
| 08/27/2014  | 1.0  |  Huma Zafar | Initial Draft  |   |
|  09/23/2013 |  1.1 |  Huma Zafar | Updated Apex Classes, Visual force pages and Test classes  |  3.24, 3.25 & 3.26 |

[TOC]
### Table of Contents

<!--BREAK-->

### Document Overview
This document describes the technical design of Salesforce.com App for Cobone Implementation.

### Audience
Technical people from Raawee and Cobone for Implementation.

### Document Scope
Out of the box configuration and customization. Custom development (e.g. Apex and Visual force).

### Assumptions
Currently there is no assumption.

### Scope Exceptions
Scope has already been defined. Out of scope items are also defined.

### 1.	Entity Relation Diagram (ERD)
![Alt Text](https://github.com/humazafar/testRepo/blob/master/data%20model%20cobone.PNG?raw=true)

### 2.	Object Inventory
Below are the names of the standard and custom objects which are part of Cobone Implementation.

| Object Name  | Description  | Custom/Native  |
|:-:|:-:|:-:|
| Chatter  |  <p>Chatter is a Salesforce collaboration application that helps you connect with people and share business information securely and in real time.</p><p> Chatter, Profile, People, Groups, and Files tabs are available by default in the Chatter app.</p> | Native  |
| User  | <p>In Salesforce, every user is identified by a username, password, and a single profile. The profile determines what tasks users can perform, what data they see, and what they can do with the data.</p> <p>You can control a user's access to data in several ways: </p><p>a) To control access to applications and objects, including fields and record types within objects, use profiles and permission sets.</p> <p>b) To control access to specific records, use sharing settings and rules.</p>  | Native  |
| Lead  | A lead is a prospect or potential opportunity - a person you met at a conference who expressed interest or someone who filled out a form on your company’s website.   |  Native |
| Account  | Accounts are your organization’s customers, competitors, and partners. Each account stores information such as name, address, and phone numbers. For each account, you can store related information such as opportunities, activities, cases, partners, contracts, and notes.  |  Native |
| Contact | Contacts are the people associated with your business accounts that you need to track in Salesforce. For each contact, you can store various kinds of information, such as phone numbers, addresses, titles, and roles in a deal.  |  Native |
| Opportunity (Deal)  | Opportunities refer to deals information in salesforce.  |  Native |
| Cases  | Represents a case, which is a customer issue or problem.   |  Native |
| Contract  | Contracts are agreements between you and your customers for a type of customer support.   |  Native |
| Contract Line  |   | Custom  |
| Activities (Tasks)  | Activities include tasks, calendar events, and requested meetings. User can define and track activities for many different objects, including leads, accounts, contacts, opportunities and custom objects.  |  Native |
| Activities (Events)  | Activities include tasks, calendar events, and requested meetings. User can define and track activities for many different objects, including leads, accounts, contacts, opportunities and custom objects.  |  Native |
| Notes& Attachments  | <p>User can create, view, and edit notes and add attachments from the Notes and Attachments related list on selected detail pages such as accounts, contacts, leads, opportunities, and custom objects. </p><p>The size limit for an attached file is 5 MB when attached directly to the related list, including a file attached to a solution. When a file is attached to a record’s Chatter feed it’s added to the Notes and Attachments related list as a feed attachment and the file size limit is 2 GB. The size limit for all files attached to an email is 10 MB.</p>  |  Native |
| Document  | A document library is a place to store files without attaching them to accounts, contacts, opportunities, or other records. Each document in the document library resides in a folder. The folder’s attributes determine the accessibility of the folder and the documents within it.  |  Native |
| Reports  |   |  Native |
| Dashboards  |   |  Native |
| Cobone API  |  Custom object used for specifying API Details and credentials |  Custom |
| Conditions And Highlights Master  |   |  Custom |
| Country  |   |  Custom |
| Customer  |   |  Custom |
| Deal Outlets  |   | Custom  |
| Hotel  |   | Custom  |
| Purchase  |   | Custom  |
| Refund/Reward  |   | Custom  |
| Scheduling  |   | Custom  |
| Score Card  |   | Custom  |
| Venue  |   | Custom  |
| Vertical  |   | Custom  |

### 3.	Technical Specification
#### 3.1	Require Activations
##### 3.1.1	Activation Information
| Items Require Activation By Salesforce.com  |
|:-:|
| Multi-Currency / Advanced Multi-Currency |

#### 3.2	Global Search
| Global Search in Salesforce.com  |
|:-:|
| <p>Global search and feed search are automatically enabled when Chatter is enabled. However, enabling Chatter disables sidebar search and advanced search. Search for salesforce.com records and tags using: </p><p>**Sidebar Search:** From the sidebar search box you can search a subset of objects and fields. You can use wildcards and filters to refine your search.</p><p>**Advanced Search:** Click Advanced Search... in the sidebar to search a subset of objects in combination and more fields than sidebar search, including custom fields and long text fields such as descriptions, notes, and task and event comments. You can use wildcards, operators, and filters to refine your search. </p><p>**Global Search:** From the header search box you can search more objects than sidebar search and advanced search, including articles, documents, products, solutions, and Chatter feeds, files, groups, topics, and people. You can also search more fields than sidebar search, including custom fields, and long text fields such as descriptions, notes, and task and event comments. You can use wildcards, operators, and filters to refine your search. Global search keeps track of which objects you use and how often you use them, and arranges the search results accordingly. Search results for the objects you use most frequently appear at the top of the list.</p> |

#### 3.3	Lead
##### 3.3.1	Page Layout Information
| Page Layout Name |
|:-:|
| Lead Layout |
| Pre-Qualified |
| Pre-Qualified - Sales Manager |
| Qualified |
| Qualified - Sales Executive |
| Qualified - Sales Manager |

##### 3.3.2	Validation Rule Information
| Validation Rule  | Error Message  | Description  |
|:-:|:-:|:-:|
| Competitor_Information  | Please enter the details of the Competitors  | On Competitor Website is selected and Competitor is not specified.  |
| One_Contact_Info  | Please enter either the Phone or Mobile Phone  | At least one contact information should be present  |

##### 3.3.3	Lead Process Information
| Lead Process Name  | Lead Status Values  |
|:-:|:-:|
| Lead Qualification Process  | Contacted (Converted), Open, Qualified (Converted), Unqualified  |

##### 3.3.4	Record Type Information
| Record Type Layout Name  | Assigned Lead Process  | Assigned Page Layout  |
|:-:|:-:|:-:|
| Pre-Qualified  | Lead Qualification Process  | Pre-Qualified, Pre-Qualified Sales Manager  |
| Qualified  | Lead Qualification Process  | Qualified Sales Manager, Qualifies Sales Executive  |

##### 3.3.5	Workflow Rule Information
| Workflow Name  | Workflow Event | Action(s)  |  Description |
|:-:|:-:|:-:|:-:|
| Lead Status Change  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Field Update: Lead Change to Qualified  | When Lead Status is Qualified, change Lead Record Type to Qualified  |
| Lead Status Change - Pre-Qualified  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: Change to Pre-Qualified  | When Lead Status is , change Lead Record Type to Pre-Qualified  |

##### 3.3.6	Sharing Rules
| Criteria  | Share with | Access  |
|:-:|:-:|:-:|
| Owner in Role and Subordinates: Sales Manager - Dubai  | Role and Subordinates: Sales Manager - Dubai  | Read/Write  |
| Owner in Role and Subordinates: Sales Manager - Jeddah  | Role and Subordinates: Sales Manager - Jeddah  | Read/Write  |
| Owner in Role and Subordinates: Sales Manager - Riyadh  | Role and Subordinates: Sales Manager - Riyadh  | Read/Write  |
| Owner in Role and Subordinates: Sales Manager - Travel  | Role and Subordinates: Sales Manager - Travel  | Read/Write  |

#### 3.4	Account
##### 3.4.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Account - KSA  |
| Account - Triperna  |
| Account Layout  |

##### 3.4.2	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| BillingAddresValidation  | For cheque courier please provide delivery address  | If Cheque Delivery Preference is Courier then Billing Address must be provided.  |
| ChequekDeliveryValidation  | Cheque Delivery Preference must be provided  | If Payment Preference is Cheque then Cheque Delivery Preference must be provided.  |
| PaymentInformationValuidation  | Please provide Bank Name, Branch, IBAN and SWIFT Code for Bank Transfer  | If Payment Preference is Bank Transfer then Bank Information must be provided.  |

##### 3.4.3	Record Type Information
| Record Type Layout Name  | Assigned Page Layout |
|:-:|:-:|
| Account - Dubai  | Account Layout  |
| Account - KSA  | Account - KSA  |
| Account - Triperna  | Account - Triperna  |

##### 3.4.4	Workflow Rule Information
| Workflow Name  | Workflow Event | Action(s)  |  Description |
|:-:|:-:|:-:|:-:|
| No Activity for 30 days  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Email Alert: Email Alert - No activity  | When Last Activity Date is blank for 30 days, Send Email to Account Owner.  |
| New Account Notification  | Evaluate the rule when a record is created  | Email Alert: New Account email  | When Account is created, Send Email to Account Owner.  |
| Disable welcome emails fro triperna  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Field Update: make send welcome mail false  | When Account Record type is Triperna, Account send welcome email checkbox should be false.  |

##### 3.4.5	Sharing Rules
| Criteria  | Share with | Access  |
|:-:|:-:|:-:|
| Owner in Role and Subordinates: Sales Manager - Dubai  | Role and Subordinates: Sales Manager - Dubai  | Read/Write  |
| Owner in Role and Subordinates: Sales Manager - Jeddah  | Role and Subordinates: Sales Manager - Jeddah  | Read/Write  |
| Owner in Role and Subordinates: Sales Manager - Riyadh  | Role and Subordinates: Sales Manager - Riyadh  | Read/Write  |
| Owner in Role and Subordinates: Sales Manager - Travel  | Role and Subordinates: Sales Manager - Travel  | Read/Write  |

#### 3.5	Contact
##### 3.5.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Contact Layout  |

##### 3.5.2	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| EmailValidation  | Invalid Email Address  | Validate Email Address  |

##### 3.5.3	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| ContactEmailPopulationOnAccount  | Before Insert, Before Update, After Insert, After Update  | This trigger errors out duplicate contacts through email. It also updates Partner access user name field in related account.  |

#### 3.6	Opportunity (Deal)
##### 3.6.1	Page Layout Information
| Page Layout Name |
|:-:|
| Approved Partnership Fixed Commission Layout  |
| Approved Partnership Fixed Layout SR  |
| Approved Partnership Management - KSA  |
| Approved Partnership Variable Commission Layout  |
| Approved Partnership Variable Layout SR  |
| Approved Standard Travel Deal Layout  |
| Approved Standard Travel Deal Layout SR  |
| Approved Standard Triperna Deal Layout  |
| Approved Standard Triperna Deal Layout - KSA  |
| Approved Travel Parent Bundle Deal Layout  |
| Approved Travel Parent Bundle Deal Layout SR  |
| Approved Triperna Parent Bundle Deal Layout  |
| Child Deal Layout  |
| Normal Deal _Admin  |
| Opportunity Layout  |
| Opportunity Layout - KSA  |
| Opportunity Layout_Approved  |
| Opportunity Layout_Approved SR  |
| Partnership Fixed Commission Layout  |
| Partnership Management - KSA  |
| Partnership Variable Commission Layout  |
| Standard Travel Deal Layout  |
| Standard Triperna Deal Layout  |
| Standard Triperna Deal Layout - KSA  |
| Travel Child Bundle Deal Layout  |
| Travel Parent Bundle Deal Layout  |
| Triperna Child Bundle Deal Layout  |
| Triperna Parent Bundle Deal Layout  |
| Umbrella deal  |
| Umbrella deal Approved  |

##### 3.6.2	Sales Process Information
| Sales Process Name  | Opportunity Stage Values with Probability |
|:-:|:-:|
| Cobone Approved Sales Process  | New Deal - 15%, Deal Review - 30%, Deal Approved - 50%, Closed Won - 100%, Closed Lost - 0%  |
| Cobone Sales Process  | New Deal - 15%, Deal Review - 30%  |

##### 3.6.3	Record Type Information
| Record Type Name  | Assigned Sales Process | Assigned Page Layout  |
|:-:|:-:|:-:|
| Approved Normal Deal  | Cobone Approved Sales Process  | Opportunity Layout_Approved, Opportunity Layout_Approved SR, Normal Deal _Admin  |
| Approved Normal Deal - KSA  | Cobone Approved Sales Process  | Opportunity Layout_Approved SR  |
| Approved Parent Bundled Deal  | Cobone Approved Sales Process  | Umbrella deal Approved  |
| Approved Partnership Fixed Commission  | Cobone Approved Sales Process  | Approved Partnership Fixed Commission Layout  |
| Approved Partnership Management - KSA  | Cobone Approved Sales Process  | Opportunity Layout  |
| Approved Partnership Variable Commission  | Cobone Approved Sales Process  | Approved Partnership Variable Commission Layout  |
| Approved Standard Travel Deal  | Cobone Approved Sales Process  | Approved Standard Travel Deal Layout, Approved Standard Travel Deal Layout SR  |
| Approved Standard Triperna Deal  | Cobone Approved Sales Process  | Approved Standard Triperna Deal Layout  |
| Approved Travel Bundled Parent Deal  | Cobone Approved Sales Process  | Approved Travel Parent Bundle Deal Layout, Approved Travel Parent Bundle Deal Layout SR  |
| Approved Triperna Bundled Parent Deal  | Cobone Approved Sales Process  | Approved Travel Parent Bundle Deal Layout  |
| Approved Triperna Deal - KSA  | Cobone Approved Sales Process  | Approved Standard Triperna Deal Layout - KSA  |
| Bundled Deal  | Cobone Sales Process  | Child Deal Layout  |
| Normal Deal  | Cobone Sales Process  | Normal Deal _Admin, Opportunity Layout  |
| Normal Deal - KSA  | Cobone Sales Process  | Opportunity Layout - KSA  |
| Parent bundled deal  | Cobone Sales Process  | Umbrella deal  |
| Partnership Fixed Commission  | Cobone Sales Process  | Partnership Fixed Commission Layout  |
| Partnership Management - KSA  | Cobone Sales Process  | Opportunity Layout  |
| Partnership Variable Commission  | Cobone Sales Process  | Partnership Variable Commission Layout  |
| Standard Travel Deal  | Cobone Sales Process  | Standard Travel Deal Layout  |
| Standard Triperna Deal  | Cobone Sales Process  | Standard Triperna Deal Layout  |
| Standard Triperna Deal - KSA  | Cobone Sales Process  | Standard Triperna Deal Layout - KSA  |
| Travel Bundled Child Deal  | Cobone Sales Process  | Travel Child Bundle Deal Layout  |
| Travel Bundled Parent Deal  | Cobone Sales Process  | Travel Parent Bundle Deal Layout  |
| Triperna Bundled Child Deal  | Cobone Sales Process  | Triperna Child Bundle Deal Layout  |
| Triperna Bundled Parent Deal  | Cobone Sales Process  | Triperna Parent Bundle Deal Layout  |

##### 3.6.4	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| Calendar_condtion  | Number of nights are necessary when deal has calendar  | Number of nights are necessary when deal has calendar  |
| Child_Deal_Number_of_nights_validation  | Number of nights is necessary due to calendar being selected in parent  | Number of nights is necessary due to calendar being selected in parent  |
| ConditionsRule  | Condition is a required field  | Condition is a required field  |
| ContractAccountValidation  | Account is not valid for contract selected  | Account is not valid for contract selected  |
| ContractLine  | Contract line is required  | Contract line is required  |
| ContractValidation  | Attached Contract is not activated or is not valid for provide scheduling dates.  | Attached Contract is not activated or is not valid for provide scheduling dates.  |
| DealNameValidation  | Deal Name cannot be more than 50 character long.  | Deal Name cannot be more than 50 character long.  |
| HighlightsRule  | Highlights is a required field  | Highlights is a required field  |
| IncludeInPromotionValidation  | Please provide a valid Promotion to Include this deal in promotion  | Please provide a valid Promotion to Include this deal in promotion  |
| IsLocationSpecificValidation_BundleDeals  | Is Location Specific checkbox should be the same as on Parent Bundled Deal.  | Is Location Specific checkbox should be the same as on Parent Bundled Deal.  |
| LastChanceValidation  | To create a last chance deal please select parent deal or mark deal as forced last chance deal  | To create a last chance deal please select parent deal or mark deal as forced last chance deal  |
| Merchant_Venues  | Associated merchant must have atleast 1 venue  | Associated merchant must have atleast 1 venue  |
| MOHDealsValidation  | MOH Approval is only required for Healthcare category.  | MOH Approval is only required for Healthcare category.  |
| NewRecordToValidateRecordType  | Wrong deal creation, please go to specific contract and generate deal of contract detail page  | Wrong deal creation, please go to specific contract and generate deal of contract detail page  |
| RelaunchValidation  | Please select parent deal for a relaunch deal type.  | Please select parent deal for a relaunch deal type.  |
| SchedulingDatesMustBeWithInMOHApproval  | Scheduling of a deal should be within the expiry of MOH validity for Medical Deals.  | Scheduling of a deal should be within the expiry of MOH validity for Medical Deals.  |
| ValidateVoucherReleaseDate  | Please provide Voucher Release Date  | Please provide Voucher Release Date  |
| Dest_Cords_Reqd  | Destination Coordinates are required when destination city and country are specified.  | Destination Coordinates are required when destination city and country are specified.  |

##### 3.6.5	Workflow Rule Information
| Workflow Name  | Workflow Event | Action(s)  |  Description |
|:-:|:-:|:-:|:-:|
| DealDiscountUpdate  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: DealAmountUpdate, DealDiscountValueUpdate  | If record type is parent bundled deal, update deal amount and discount.  |
| NotificationToProductionSystemToProduceMedicalDeal  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Email Alert: NotificationToProductionSystemToProduceMedicalDeal  | Notification To Production System To Produce Medical Deal.  |
| NotificationToPartnershipToGetMedicalApproval  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Email Alert: NotificationToPartnershipManagerToGetMedicalApproval  | Send email to selected users  |
| NotificationToDealManagementForMockDateRequirementOnMedicalDeal  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Email Alert: NotificationToDealManagementForMockScreenRequiredByDate  | When category if health care and deal is closed won, send email to selected users.  |
| UpdateMOHApprovalExpiry  |  Evaluate the rule when a record is created, and every time it’s edited | Field Update: UpdateMOHExpiryDate  | When Approval Date is changed, Expiry Date becomes approval date  + 30 days  |
| OpportunityTextHighlightsConversion  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: GetHightlightsText, GetConditionsText  | When a record is new or highlights or conditions are changed, update text highlights and text conditions.  |
| UpdateSalesCommission  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: UpdateSalesCommissionValue  | Update Sales Commission value.  |
| PopulateMinimumSales  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: UpdateMinimumSales  | Update Minimum sales from contract.  |
| DealCommitNotificationForSalesUser  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Task: Deal Committed, Email Alert: DealCommit  | When Deal Id is greater than 0 and Scheduling Date is not Blank, create task for Deal Owner and send email to Deal Owner.  |
| Update Gross Margin  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: Gross Margin Update  | Update Gross Margin as Cobone Revenue.  |
| Mark address for Travel deals  | Evaluate the rule when a record is created, and any time it’s edited to subsequently meet criteria  | Field Update: Update isAddress  | When Category is Travel, update is Address Required checkbox to true.  |

##### 3.6.6	Approval Process Information
| Approval Process  Name  | 
|:-:|
| DealApprovalProcessBundledTravel_N  |
| DealApprovalProcessBundled_New  |
| DealApprovalProcessPartnershipFixedCo_N  |
| DealApprovalProcessPartnershipVariable_N  |
| DealApprovalProcessTravel_N  |
| DealApprovalProcess_New  |
| DealApprovalProcessTriperna_N  |
| DealApprovalProcessBundledTripernal_N  |
| DealApprovalProcessTriperna - KSA  |
| DealApprovalProcess_Partnership - KSA  |
| DealApprovalProcess_New - KSA  |
| DealApprovalProcessBundledTravel_N  |

##### 3.6.7	Buttons Information
| Button Type(Standard / Custom)  | Button Name | Purpose  |
|:-:|:-:|:-:|
| Custom  | Activate / Inactivate  | Button for Activating/Inactivating Deal  |
| Custom  | Attach Destination  | This button redirects to deal location page.  |
| Custom  | Clone  | This button clones deal using Relaunch class.  |
| Custom  | Generate Deal Info Sheet  | This button is used for generating Info Sheet using mail merge.  |
| Custom  | Generate Deal Info Sheet - TP  | This button is used for generating Info Sheet using mail merge for Triperna.  |
| Custom  | New Child Deal  | Create new Child Deal.  |
| Custom  | New Deal  | List button.  |
| Custom  | New Deal  | List button.  |
| Custom  | New Deal  | List button.  |
| Custom  | New Deal  | List button.  |
| Custom  | New Fixed Commission Deal  | List button.  |
| Custom  | New Fixed Commission Deal  | List button.  |
| Custom  | New PM Deal  | List button.  |
| Custom  | New Standard Travel Deal  | List button.  |
| Custom  | New Standard Triperna Deal  | List button.  |
| Custom  | New Travel Bundled Deal  | List button.  |
| Custom  | New Travel Child Deal  | List button.  |
| Custom  | New Triperna Bundled Deal  | List button.  |
| Custom  | New Triperna Child Deal  | List button.  |
| Custom  | New Triperna Travel Deal  | List button.  |
| Custom  | New Variable Commission Deal  | List button.  |
| Custom  | New Variable Commission Deal  | List button.  |
| Custom  | Relaunch  | This button re-launches deal using Relaunch class.  |
| Custom  | Send MOH deal to Production  | This button sends MOH Deals to production.  |
| Custom  | View Purchases  | Button for viewing purchase report.  |

##### 3.6.8	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| Opportunity_Trigger  | Before Insert, Before Update, After Update  |   |

#### 3.7	Cases
##### 3.7.1	Page Layout Information
| Page Layout  Name  | 
|:-:|
| Case Layout  |
| Triperna Case Layout  |



|   |
|   |
|   |
|   |
|   |
|   |
|   |
|   |

|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |


|   |   |   |   |
|   |   |   |   |
|   |   |   |   |
|   |   |   |   |
|   |   |   |   |

