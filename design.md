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

##### 3.7.2	Support Process Information
| Support Process Name  |
|:-:|
| Cobone  |

##### 3.7.3	Record Type Information
| Record Type Name  | Assigned Sales Process | Assigned Page Layout  |
|:-:|:-:|:-:|
| Cobone  | Cobone  | Case Layout  |
| Triperna  | Cobone  | Triperna Case Layout  |
| Safarna  | Cobone  | Triperna Case Layout  |

##### 3.7.4	Buttons Information
| Button Type(Standard / Custom)  | Button Name | Purpose  |
|:-:|:-:|:-:|
| Custom  | Forward  | This button is used for forwarding email to any emails.  |
| Custom  | New Child Case  | List button for creating child case.  |
| Custom  | Reply  | This button is used for replying latest email from the customer.  |

##### 3.7.5	Case Auto Response Rule
| Rule Name  | Description |
|:-:|:-:|
| Cobone Auto Response Rules  |   |

##### 3.7.6	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| CaseTrg  | Before insert, after insert  | To associate Case with Customer according to Email address.  |

#### 3.8	Contract
##### 3.8.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Approved Cobone Ticket/Activity Contract  |
| Approved Contract Layout  |
| Approved Contract Layout - KSA  |
| Approved PM Agreement - KSA  |
| Approved Redemption Contract  |
| Approved Sales User Bundled Contract  |
| Approved Triperna Ticket/Activity Contract  |
| Approved_Contract_Partnership  |
| Bundled Contract  |
| Cobone Ticket/Activity Contract  |
| Contract Layout  |
| Contract_Partnership  |
| PM Agreement - KSA  |
| Sales User Approved Travel Layout  |
| Sales User Approved Triperna Layout  |
| Sales User Approved Triperna Layout - KSA  |
| Sales User Bundled Contract  |
| Sales User Contract Layout  |
| Sales User Contract Layout - KSA  |
| Sales User Contract Partnership Layout  |
| Sales User Redemption Contract  |
| Sales User Travel Layout  |
| Sales User Triperna Layout  |
| Sales User Triperna Layout - KSA  |
| Triperna Ticket/Activity Contract  |

##### 3.8.2	Record Type Information
| Record Type Layout Name  | Assigned Page Layout |
|:-:|:-:|
| Approved Bundled Contract  | Approved Sales User Bundled Contract  |
| Approved Cobone Ticket/Activity Contract  | Approved Cobone Ticket/Activity Contract  |
| Approved Normal - KSA  | Approved Contract Layout - KSA  |
| Approved Normal Deal  | Approved Contract Layout  |
| Approved PM Agreement - KSA  | Approved PM Agreement - KSA  |
| Approved Partnership Contract  | Approved_Contract_Partnership  |
| Approved Redemption Contract  | Approved Redemption Contract  |
| Approved Travel Contract  | Sales User Approved Travel Layout  |
| Approved Triperna Contract  | Sales User Approved Triperna Layout  |
| Approved Triperna Contract - KSA  | Sales User Approved Triperna Layout - KSA  |
| Approved Triperna Ticket/Activity Contract  | Approved Triperna Ticket/Activity Contract  |
| Bundled Contract  | Sales User Bundled Contract  |
| Cobone Ticket/Activity Contract  | Cobone Ticket/Activity Contract  |
| Non-Approved  | Contract Layout  |
| Normal  | Sales User Contract Layout  |
| Normal - KSA  | Sales User Contract Layout - KSA  |
| PM Agreement - KSA  | PM Agreement - KSA  |
| Partnership  | Sales User Contract Partnership Layout  |
| Redemption  | Sales User Redemption Contract  |
| Travel  | Sales User Travel Layout  |
| Triperna  | Sales User Triperna Layout  |
| Triperna - KSA  | Sales User Triperna Layout - KSA  |
| Triperna Ticket/Activity Contract  | Triperna Ticket/Activity Contract  |

##### 3.8.3	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| First_and_Second_Hold_Back_values_valid  | First and Second Hold Back values valid cannot be less than 0 and greater than 50 , Kick back range is 0- 30  | First and Second Hold Back values valid cannot be less than 0 and greater than 50 , Kick back range is 0- 30  |
| FixedCommissionContractValidation  | Sales Commission should be provided for Fixed Parntership Contracts.  | Sales Commission should be provided for Fixed Parntership Contracts.  |
| MarketPriceValidation  | Market Price should be more than 0  | Market Price should be more than 0  |
| PartnerPriceValidation  | Partner Price should be more than 0  | Partner Price should be more than 0  |
| Payment_Frequency_Period_Limitation  | Payment Frequency value should 10 to 21  | Payment Frequency value should 10 to 21  |
| Percentage_Payment_Validation  | The Percentage of sold booking to be paid should be more than 50 and less than 90  | The Percentage of sold booking to be paid should be more than 50 and less than 90  |
| SalesCommissionCoboneCutValidation  | Please provide either sales commission or cobone cut  | Please provide either sales commission or cobone cut  |
| ValidationForPaymentTermsAndHoldBackReq  | Please select appropriate Applicable Contract Type, Payment Terms and Hold back Percentage if you wish to override default payment terms  | Please select appropriate Applicable Contract Type, Payment Terms and Hold back Percentage if you wish to override default payment terms  |
| VenuesValidation  | Partner should have atleast one venue to create contract. Go back to the account and create a new venue on the venues list.  | Partner should have atleast one venue to create contract. Go back to the account and create a new venue on the venues list.  |

##### 3.8.4	Workflow Rule Information
| Workflow Name  | Workflow Event | Action(s)  |  Description |
|:-:|:-:|:-:|:-:|
| ContractTypeWorkflow  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: ContractTypeToC  | Update Applicable contract type to contract C.  |
| ContractTypeWorkflowToA  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: ContractTypeToA  | Update Applicable contract type to contract A.  |
| ContractTypeWorkflowToB  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: ContractTypeToB  | Update Applicable contract type to Contract B.  |
| SetDefaultContractBHoldBackAndPaymentTerms  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: ContractBHoldBack, ContractBPaymentTerms, ContractTypeToB  | Update contract hold back percentage, payment terms and applicable contract type.  |
| SetDefaultContractCHoldBackAndPaymentTerms  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: ContractCHoldBack, ContractCPaymentTerms, ContractTypeToC  | Update contract hold back percentage, payment terms and applicable contract type.  |
| SetDefaultHoldBackAndPaymentTerms  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: ContractAHoldBack, ContractAPaymentTerms, ContractTypeToA  | Update contract hold back percentage, payment terms and applicable contract type.  |
| update sales commission and cobone cut  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: update cobone cut, update sales commission  | When Contract record type is Normal, Partnership, Approved Normal Deal, Approved Partnership Contract, update cobone cut and sales commission.  |
| ContractActivationEmailToSalesUser  | Evaluate the rule when a record is created, and every time it’s edited  | Task: Contract Activated, Email Alert: EmailToSalesUserforContractActivation  | When contract status is activated, create task for record creator and send email to contract owner.  |
| SetZeroSalesCommission  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: UpdateSalesCommissionToZero  | When Partnership contract type is variable commission and sales commission is blank, update commission to zero.  |
| Mark as isTriperna  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: Update isTriperna Contract  | When account record type is Account Triperna, update is triperna contract flag as true.  |

##### 3.8.5	Approval Process Information
| Approval Process Name  |
|:-:|
| ContractSalesApproval_New  |
| ContractSalesApproval_Bundled  |
| ContractSalesApproval_Partnership  |
| ContractSalesApproval_Travel  |
| Contract_Redemption_New  |
| ContractSalesApproval_Partner_KSA  |
| ContractSalesApproval_Triperna  |
| Triperna_Contract_Activity_New  |
| Contract_Activity_New  |
| ContractSalesApproval_Triperna - KSA  |
| ContractSalesApproval_New_KSA  |

##### 3.8.6	Buttons Information
| Button Type(Standard / Custom)  | Button Name | Purpose  |
|:-:|:-:|:-:|
| Custom  | Generate Contract  | This button is used for generating Contract Agreement using mail merge.  |
| Custom  | Generate PDF  | This button is used for generating Contract Agreement PDF.  |
| Custom  | New Bundled Contract  | List Button for creating new Contract.  |
| Custom  | New Cobone Activity Contract  | List Button for creating new Contract.  |
| Custom  | New Normal Contract  | List Button for creating new Contract.  |
| Custom  | New Normal Contract - KSA  | List Button for creating new Contract.  |
| Custom  | New Partnership Contract  | List Button for creating new Contract.  |
| Custom  | New PM Contract - KSA  | List Button for creating new Contract.  |
| Custom  | New Redemption Contract  | List Button for creating new Contract.  |
| Custom  | New Travel Contract  | List Button for creating new Contract.  |
| Custom  | New Triperna Activity Contract  | List Button for creating new Contract.  |
| Custom  | New Triperna Contract  | List Button for creating new Contract.  |

##### 3.8.7	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| getCustomerSignedInfo  | Before insert, before update  | This trigger fills info based on customer signed by field on contract and sends an  email if  related account  has send email account = true and makes it false.  |

#### 3.9	Contract Line
##### 3.9.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Contract Line Layout  |

##### 3.9.2	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| MarketPrice_Validation  | Market Price should be more than 0.  | Market Price should be more than 0.  |
| PartnerPrice_Validation  | Partner Price should be more than 0.  | Partner Price should be more than 0.  |

##### 3.9.3	Workflow Rule Information
| Workflow Name  | Workflow Event | Action(s)  |  Description |
|:-:|:-:|:-:|:-:|
| update sales commission and cobone cut- contract line  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: update cobone cut  | Update cobone cut.  |

##### 3.9.4	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| FillContractMailMerge  | After insert, after update, after delete  | Update related contract.  |

#### 3.10	Activities (Tasks / Events)
##### 3.10.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Task Layout  |
| Event Layout  |

##### 3.10.4	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| ActivityTrg (Task)  | After insert  | To update Case status while sending email.  |
| LeadActivityForStatusChange  | After insert, after update  | If task is completed, update lead status.  |

#### 3.11	Cobone API
##### 3.11.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Cobone API Layout  |

##### 3.11.2	Workflow Rule Information
| Workflow Name  | Workflow Event | Action(s)  |  Description |
|:-:|:-:|:-:|:-:|
| makeUnique  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: SetUniqueValue  | When Cobone API active is true, set UniqueId to true.  |
| makeUniqueFalse  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: MakeUniqueFalse  | When Cobone API active is false, set UniqueId to false.  |

##### 3.11.3	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| CoboneAPI_Trigger  | Before insert, before update  |   |

#### 3.12	Conditions and Highlights Master
##### 3.12.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Conditions And Highlights Master Layout  |

##### 3.12.2	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| CategoriesValidation  | Before insert, before update  |   |

#### 3.13	Country
##### 3.13.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Country Layout  |

##### 3.14	Customer
##### 3.14.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Customer Layout  |

#### 3.15	Deal Outlets
##### 3.15.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Deal Outlets Layout  |

##### 3.15.2	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| DealChangeValidation  | Related deal for a venue cannot be changed please delete this venue and create a new deal outlet on required deal.  | Related deal for a venue cannot be changed please delete this venue and create a new deal outlet on required deal.  |
| DealLocationTypeValidation  | Venue outlets are not required for Deal with ALL Location Type selected  | Venue outlets are not required for Deal with ALL Location Type selected  |

##### 3.15.3	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| SyncParentDealVenuesToChild  | After insert, after update  |   |

#### 3.16	Hotel
##### 3.16.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Hotel Layout  |

#### 3.17	Purchase
##### 3.17.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Purchase Layout  |

##### 3.17.2	Workflow Rule Information
| Workflow Name  | Workflow Event | Action(s)  |  Description |
|:-:|:-:|:-:|:-:|
| UpdateCoboneRevenue  | Evaluate the rule when a record is created, and every time it’s edited  | Field Update: UpdateCoboneSalesRevenueValue  | Update cobone sales revenue.  |

##### 3.17.3	Apex Trigger Information
| Apex Trigger Name  | Event(s) | Description  |
|:-:|:-:|:-:|
| trig_Purchase  | Before update  |   |

#### 3.18	Refund/Reward
##### 3.18.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Refund/Reward Layout  |

#### 3.19	Scheduling
##### 3.19.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Scheduling Layout  |

#### 3.20	Score Card
##### 3.20.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Score Card Layout  |

#### 3.21	Venue
##### 3.21.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Venue Layout  |

##### 3.21.2	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| GeoCoordsValidation  | Geo-Cords are not in correct format. Correct format is Latitude range is from -90 to +90, Longitude from -180 to +180.  | Geo-Cords are not in correct format. Correct format is Latitude range is from -90 to +90, Longitude from -180 to +180.  |
| Venue_City_Validation  | City cannot have more than 45 characters  | City cannot have more than 45 characters  |
| VenueCodeValidation  | Venue code cannot be longer than 10 characters.  | Venue code cannot be longer than 10 characters.  |
| VenueNameValidation  | Venue Name cannot be greater than 45 characters.  | Venue Name cannot be greater than 45 characters.  |
| VenueNumberValidation  | Please enter number.  | Please enter number.  |
| Website_Country_Validation  | Please put correct country  | Please put correct country  |

##### 3.21.3	Buttons Information
| Button Type(Standard / Custom)  | Button Name | Purpose  |
|:-:|:-:|:-:|
| Custom  | New Venue  | List button for creating new Venue.  |

#### 3.22	Vertical
##### 3.22.1	Page Layout Information
| Page Layout Name  |
|:-:|
| Vertical Layout  |
| City / Location  |
| Promotion Layout  |

##### 3.22.2	Validation Rule Information
| Validation Rule  | Error Message | Description  |
|:-:|:-:|:-:|
| Invalid combination  | Invalid combination  |   |
| Invalid_Combination2  | Invalid combination  |   |
| Invalid_Combination3  | Invalid combination  |   |

##### 3.22.3	Record Type Information
| Record Type Layout Name  | Assigned Page Layout |
|:-:|:-:|
| Vertical  | Vertical Layout  |

#### 3.23	Security
##### 3.23.1	Org-Wide Default
<p>Administrators can use organization-wide sharing settings to define the default sharing settings for an organization. Organization-wide sharing settings specify the default level of access to records and can be set separately for accounts (including assets and contracts), activities, contacts, campaigns, cases, leads, opportunities, calendars, price books, and custom objects.</p>
<p>For most objects, organization-wide sharing settings can be set to Private, Public Read Only, or Public Read/Write. In environments where the organization-wide sharing setting for an object is Private or Public Read Only, an administrator can grant users additional access to records by setting up a role hierarchy or defining sharing rules. However, sharing rules can only be used to grant additional access—they cannot be used to restrict access to records beyond what was originally specified with the organization-wide sharing defaults.</p>

##### 3.23.2	Role Hierarchy
Depending on your sharing settings, roles can control the level of visibility that users have into your organization’s data. Users at any given role level can view, edit, and report on all data owned by or shared with users below them in the hierarchy, unless your organization’s sharing model for an object specifies otherwise. Specifically, in the Organization-Wide Defaults related list, if the Grant Access Using Hierarchies option is disabled for a custom object, only the record owner and users granted access by the organization-wide defaults receive access to the object's records.

##### 3.23.3	Profiles
A profile contains user permissions and access settings that control what users can do within their organization.

##### 3.23.4	Record Types
<p>Record types allow you to offer different business processes, picklist values, and page layouts to different users. Record types can be used in various ways, for example:</p>
* Create record types for opportunities to differentiate your regular sales deals from your professional services engagements and offer different picklist values for each.
* Create record types for cases to display different page layouts for your customer support cases versus your billing cases.

##### 3.23.5	Queues
| Queue Name  | Queue Email | Available for Objects  |
|:-:|:-:|:-:|
| Service Queue  | test@cobone.com  | Case  |

##### 3.23.6	Profiles
| Profile Name  | User License |
|:-:|:-:|
| Chatter External User  | Chatter External  |
| Chatter Free User  | Chatter Free  |
| Chatter Free User  | Chatter Free  |
| Cloned Sales User  | Salesforce  |
| Contract Manager  | Salesforce  |
| Custom System Admin  | Salesforce  |
| Finance User  | Salesforce  |
| Limited Scheduling User  | Salesforce  |
| Marketing User  | Salesforce  |
| Operations Manager  | Salesforce  |
| Operations Manager - KSA  | Salesforce  |
| Partnership Manager  | Salesforce  |
| Partnership Manager - KSA  | Salesforce  |
| Partnership User  | Salesforce  |
| Partnership User - KSA  | Salesforce  |
| Production User  | Salesforce  |
| Read Only  | Salesforce  |
| Sales Manager  | Salesforce  |
| Sales Manager - KSA  | Salesforce  |
| Sales User  | Salesforce  |
| Sales User - KSA  | Salesforce  |
| Service Manager  | Salesforce  |
| Service User  | Salesforce  |
| Solution Manager  | Salesforce  |
| Standard User  | Salesforce  |
| System Administrator  | Salesforce  |

##### 3.23.7	Role Hierarchy
| Role Name  | Parent Role |
|:-:|:-:|
| Cobone Manager  |   |
| Manager - KSA  | Cobone Manager  |
| Partnership Manager - Jeddah  | Manager - KSA  |
| Partnership Manager - Riyadh  | Manager - KSA  |
| Sales Manager - Jeddah  | Manager - KSA  |
| Sales Executive - Jeddah  | Sales Manager - Jeddah  |
| Sales Manager - Riyadh  | Manager - KSA  |
| Sales Executive - Riyadh  | Sales Manager - Riyadh  |
| Operations Manager  | Cobone Manager   |
| Partnership Manager  | Cobone Manager   |
| Sales Manager  | Cobone Manager   |
| Sales User  | Sales Manager  |
| Sales Manager - Dubai  | Cobone Manager   |
| Sales Executive - Dubai  | Sales Manager - Dubai  |
| Sales Manager - Electronics  | Cobone Manager   |
| Sales Executive - Electronics  | Sales Manager - Electronics  |
| Sales Manager - Fashion  | Cobone Manager   |
| Sales Executives - Fashion  | Sales Manager - Mall  |
| Sales Manager - Mall  | Cobone Manager  |
| Sales Executives - Mall  | Sales Manager - Mall  |
| Sales Manager - Sharjah  | Cobone Manager  |
| Sales Executive - Sharjah  | Sales Manager - Sharjah  |
| Sales Manager - Abu Dhabi  | Sales Manager - Sharjah  |
| Sales Executive - Abu Dhabi  | Sales Manager - Abu Dhabi  |
| Sales Manager - Travel  | Cobone Manager  |
| Sales Executive - Travel  | Sales Manager - Travel  |

##### 3.23.8	Org-Wide Default
| Object  Name  | Default Internal Access | Default External Access  |
|:-:|:-:|:-:|
| Lead  | Private  | Private  |
| Account, Contract and Asset  | Private  | Private  |
| Contact  | Private  | Private  |
| Opportunity  | Private  | Private  |
| Case  | Private  | Private  |
| Campaign  | Public Full Access  | Public Full Access  |
| User  | Public Read Only  | Private  |
| Activity  | Private  | Private  |
| Calendar  | Hide Details and Add Events  | Hide Details and Add Events  |
| Price Book  | Use  | Use  |
| CoboneAPI  | Public Read/Write  | Public Read/Write  |
| Conditions And Highlights Master  | Public Read/Write  | Public Read/Write  |
| Contract Line  | Controlled by Parent  | Controlled by Parent  |
| Country  | Public Read/Write  | Public Read/Write  |
| Customer  | Public Read/Write  | Public Read/Write  |
| Deal Outlets  | Controlled by Parent  | Controlled by Parent  |
| Hotel  | Public Read/Write  | Public Read/Write  |
| Purchase  | Controlled by Parent  | Controlled by Parent  |
| Refund/Reward  | Public Read/Write  | Public Read/Write  |
| Scheduling  | Controlled by Parent  | Controlled by Parent  |
| Score Card  | Public Read/Write  | Public Read/Write  |
| Venue  | Controlled by Parent  | Controlled by Parent  |
| Vertical  | Public Read/Write  | Public Read/Write  |

##### 3.24	Apex Classes
| Apex Class Name  | Description |
|:-:|:-:|
| ApplicationException  | Exception class.  |
| batch_SweepInactiveAccounts  | Batch class to update Email alert flag for all accounts having Activity Level as Inactive Account, Open Account or No Activity.  |
| CallIntegration  | This class is the parent class to call all integrations.  |
| cntl_Integration_ActiveButton  | This class is called by Activate/Inactive button on Opportunity(Deal).  |
| cntl_misc  | Utlity class for creating integration API End point URL.  |
| ctlr_contractNavPage  | This controller is for the intermediate navigation page which directs to the relevant PDF for contract templates.  |
| ctlr_dealContainer  | Deal container class.  |
| ctlr_deal_closing  | This class serves as controller for deal closing VF page where deals can be ended.  |
| ctlr_deal_closingTriperna  | This class serves as controller for deal closing VF page where Triperna deals can be ended.  |
| ctlr_deal_dashboard  | This class is used to display deals dashboard from cool deals.  |
| ctlr_deal_dashboardTriperna  | This class is used to display Triperna deals dashboard from cool deals.  |
| ctlr_deal_location  | This class serves as controller for deal location page where a location is added to deal.  |
| ctlr_deal_planning2  | Controller class for deal scheduling page.  |
| ctlr_deal_planning_Triperna  | Controller class for deal scheduling page Triperna.  |
| ctlr_deal_report  | Main controller for redirecting to csv report.  |
| ctlr_deal_report_csv  | Works as controller for generating report CSV  |
| ctlr_deal_scheduling  | Deal scheduling controller class  |
| ctlr_deal_scheduling_Triperna  | Deal scheduling controller class for Triperna.  |
| Deal  | This class is the main structure of Deal for integration.  |
| DealClosingUtil  | Utiliting class for centralizing methods used in ctlr_deal_closing and ctlr_deal_closingTriperna.  |
| dealHelper  | Deal Helper class used in Trigger.  |
| InvokeUpdateTriggerBatch  | Batch class for updating records to invoke trigger.  |
| Merchant  | This class is the main structure of Merchant for integration.  |
| RelaunchClass  | Class used for Re-launching a deal.  |
| schedule_SweepInactiveAccounts  | Scheduler class for batch_SweepInactiveAccounts.  |

##### 3.25	Visual Force Pages
| Visual Force Page Name  | Visualforce Controller / Extension | Purpose  |
|:-:|:-:|:-:|
| CaseTabVfp  | Standard Controller Case  | This page is used as a tab view for Cases Tab.  |
| con_A  | Standard Controller Contract  | Contract Agreement PDF Page Cobone.  |
| con_activityCobone  | Standard Controller Contract  | Supply Agreement PDF Page Cobone.  |
| con_activityTriperna  | Standard Controller Contract  | Supply Agreement PDF Page Triperna.  |
| con_B  | Standard Controller Contract  | Contract Agreement PDF Page Cobone.  |
| con_bundleA  | Standard Controller Contract  | Contract Agreement PDF Page Cobone.  |
| con_bundleB  | Standard Controller Contract  | Contract Agreement PDF Page Cobone.  |
| con_bundleC  | Standard Controller Contract  | Contract Agreement PDF Page Cobone.  |
| con_C  | Standard Controller Contract  | Contract Agreement PDF Page Cobone.  |
| con_NavPage  | Standard Controller Contract, Extensions ctlr_contractNavPage  | Contract PDF Navigation Page.  |
| con_partnerFixed  | Standard Controller Contract  | Partnership Agreement PDF.  |
| con_partnerVar  | Standard Controller Contract  | Partnership Agreement PDF.  |
| con_Redemption  | Standard Controller Contract  | Supply Agreement PDF Page Cobone.  |
| con_Redemption  | Standard Controller Contract  | Supply Agreement PDF Page Cobone.  |
| con_SaudiaPartArabic  | Standard Controller Contract  | Supply Agreement PDF Page Cobone in Arabic.  |
| con_SaudiaPartEnglish  | Standard Controller Contract  | Supply Agreement PDF Page Cobone in English.  |
| con_travelNet  | Standard Controller Contract  | Travel Supply Agreement PDF Page Cobone.  |
| con_travelVar  | Standard Controller Contract  | Travel Supply Agreement PDF Page Cobone.  |
| con_triperna  | Standard Controller Contract  | Triperna Partnership and Supply Agreement PDF.  |
| dealPlanningCSS  | N/A  | Css for Deal planning page.  |
| dealSchedulingScreenTriperna  | Controller ctlr_deal_planning_Triperna  | Deal scheduling Triperna Page.  |
| deal_closing  | Controller ctlr_deal_closing   | Deal Closing Page.  |
| deal_closingTriperna  | Controller ctlr_deal_closingTriperna  | Deal Closing Page Triperna.  |
| deal_dashboard  | Controller ctlr_deal_dashboard  | Deal dashboard page showing iframe.  |
| deal_dashboardTriperna  | Controller ctlr_deal_dashboardTriperna  | Deal dashboard page showing iframe for Triperna.  |
| deal_location  | Standard Controller Opportunity, Extensions ctlr_deal_location  | Deal Location Page  |
| deal_planning2  | Controller ctlr_deal_planning2  | Deal Planning Page.  |
| deal_report  |   | Deal Report Input dates page.  |
| deal_report_csv  | Deal Report page for downloading CSV Report.  | Deal Report page for downloading CSV Report.  |
| deal_scheduling  | Controller ctlr_deal_scheduling  | Deal Scheduling page.  |
| deal_schedulingTriperna  | Controller ctlr_deal_scheduling_Triperna  | Deal Scheduling page for Triperna.  |
| vfp_dealSchedulingScreen  | Controller ctlr_deal_planning2  | Deal Scheduling page.  |

##### 3.26	Test Classes
| Apex Class Name  | Description |
|:-:|:-:|
| ActivityTrgTestClass  | Test class for activity trigger.  |
| ActivityTrgTestClass  | Test class for CallIntegration.  |
| CallIntegrationUpdateTest  | Test class for CallIntegration.  |
| CaseTrgTestClass  | Test class for CaseTrg.  |
| cntl_Integration_ActiveButtonTest  | Test class for  cntl_Integration_ActiveButton.  |
| test2_deal_planning2  | Test class for ctlr_deal_planning2.  |
| test3_deal_planning2  | Test class for ctlr_deal_planning2.  |
| TestClass_Triggers  | Test class for all triggers.  |
| test_cntl_misc  | Test class for cntl_misc.  |
| test_contractNavPage  | Test class for ctlr_contractNavPage.  |
| test_contractTrig  | Test class for Contract Trigger.  |
| test_DealHelper  | Test class for dealHelper.  |
| test_deal_closing  | Test class for ctlr_deal_closing.  |
| test_deal_closingTriperna  | Test class for ctlr_deal_closingTriperna.  |
| test_deal_dashboard  | Test class for ctlr_deal_dashboard & ctlr_deal_dashboardTriperna.  |
| test_deal_location  | Test class for ctlr_deal_location.  |
| test_deal_planning2  | Test class for ctlr_deal_planning2.  |
| test_deal_report  | Test class for ctlr_deal_report.  |
| MockHttpResponseGenerator  | Test class for Http call to integration API.  |
| MockHttpResponseGeneratorDeal  | Test class for Http call to integration API.  |

