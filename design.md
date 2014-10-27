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
| Chatter  |  Chatter is a Salesforce collaboration application that helps you connect with people and share business information securely and in real time.
Chatter, Profile, People, Groups, and Files tabs are available by default in the Chatter app.
 | Native  |
| User  | In Salesforce, every user is identified by a username, password, and a single profile. The profile determines what tasks users can perform, what data they see, and what they can do with the data.
You can control a user's access to data in several ways:
->To control access to applications and objects, including fields and record types within objects, use profiles and permission sets.
->To control access to specific records, use sharing settings and rules.
  | Native  |
| Lead  | A lead is a prospect or potential opportunity - a person you met at a conference who expressed interest or someone who filled out a form on your company’s website.   |  Native |
| Account  | Accounts are your organization’s customers, competitors, and partners. Each account stores information such as name, address, and phone numbers. For each account, you can store related information such as opportunities, activities, cases, partners, contracts, and notes.  |  Native |
|  Contact | Contacts are the people associated with your business accounts that you need to track in Salesforce. For each contact, you can store various kinds of information, such as phone numbers, addresses, titles, and roles in a deal.  |  Native |
| Opportunity (Deal)  | Opportunities refer to deals information in salesforce.  |  Native |
| Cases  | Represents a case, which is a customer issue or problem.   |  Native |
| Contract  | Contracts are agreements between you and your customers for a type of customer support.   |  Native |
| Contract Line  |   | Custom  |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
|   |   |   |
