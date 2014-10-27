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
| Chatter  |  Chatter is a Salesforce collaboration application that helps you connect with people and share business information securely and in real time. Chatter, Profile, People, Groups, and Files tabs are available by default in the Chatter app. | Native  |
| User  | In Salesforce, every user is identified by a username, password, and a single profile. The profile determines what tasks users can perform, what data they see, and what they can do with the data. You can control a user's access to data in several ways: a) To control access to applications and objects, including fields and record types within objects, use profiles and permission sets. b) To control access to specific records, use sharing settings and rules.  | Native  |
| Lead  | A lead is a prospect or potential opportunity - a person you met at a conference who expressed interest or someone who filled out a form on your company’s website.   |  Native |
| Account  | Accounts are your organization’s customers, competitors, and partners. Each account stores information such as name, address, and phone numbers. For each account, you can store related information such as opportunities, activities, cases, partners, contracts, and notes.  |  Native |
| Contact | Contacts are the people associated with your business accounts that you need to track in Salesforce. For each contact, you can store various kinds of information, such as phone numbers, addresses, titles, and roles in a deal.  |  Native |
| Opportunity (Deal)  | Opportunities refer to deals information in salesforce.  |  Native |
| Cases  | Represents a case, which is a customer issue or problem.   |  Native |
| Contract  | Contracts are agreements between you and your customers for a type of customer support.   |  Native |
| Contract Line  |   | Custom  |
| Activities (Tasks)  | Activities include tasks, calendar events, and requested meetings. User can define and track activities for many different objects, including leads, accounts, contacts, opportunities and custom objects.  |  Native |
| Activities (Events)  | Activities include tasks, calendar events, and requested meetings. User can define and track activities for many different objects, including leads, accounts, contacts, opportunities and custom objects.  |  Native |
| Notes& Attachments  | User can create, view, and edit notes and add attachments from the Notes and Attachments related list on selected detail pages such as accounts, contacts, leads, opportunities, and custom objects. The size limit for an attached file is 5 MB when attached directly to the related list, including a file attached to a solution. When a file is attached to a record’s Chatter feed it’s added to the Notes and Attachments related list as a feed attachment and the file size limit is 2 GB. The size limit for all files attached to an email is 10 MB.  |  Native |
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
| Global search and feed search are automatically enabled when Chatter is enabled. However, enabling Chatter disables sidebar search and advanced search. Search for salesforce.com records and tags using: **Sidebar Search:** From the sidebar search box you can search a subset of objects and fields. You can use wildcards and filters to refine your search. **Advanced Search:** Click Advanced Search... in the sidebar to search a subset of objects in combination and more fields than sidebar search, including custom fields and long text fields such as descriptions, notes, and task and event comments. You can use wildcards, operators, and filters to refine your search. **Global Search:** From the header search box you can search more objects than sidebar search and advanced search, including articles, documents, products, solutions, and Chatter feeds, files, groups, topics, and people. You can also search more fields than sidebar search, including custom fields, and long text fields such as descriptions, notes, and task and event comments. You can use wildcards, operators, and filters to refine your search. Global search keeps track of which objects you use and how often you use them, and arranges the search results accordingly. Search results for the objects you use most frequently appear at the top of the list. |

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