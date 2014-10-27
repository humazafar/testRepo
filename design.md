![Alt Text](https://github.com/humazafar/testRepo/blob/master/Cobone.png?raw=true)

# Technical Design Document

![Alt Text](https://github.com/humazafar/testRepo/blob/master/Raawee.png?raw=true)

<!--BREAK-->

## Document Revision History Log
| Date | Version  | Name  | Changes Description | Sections Impacted  |
|:-:|:-:|:-:|:-:|:-:|
| 08/27/2014  | 1.0  |  Huma Zafar | Initial Draft  |   |
|  09/23/2013 |  1.1 |  Huma Zafar | Updated Apex Classes, Visual force pages and Test classes  |  3.24, 3.25 & 3.26 |

### Table of Contents
Document Overview
Audience
Document Scope
Assumptions
Scope Exceptions
1.	Entity Relation Diagram (ERD)
2.	Object Inventory
3.	Technical Specification
3.1	Require Activations
3.1.1	Activation Information
3.2	Global Search
3.3	Lead
3.3.1	Page Layout Information
3.3.2	Validation Rule Information
3.3.3	Lead Process Information
3.3.4	Record Type Information
3.3.5	Workflow Rule Information
3.3.6	Sharing Rules
3.4	Account
3.4.1	Page Layout Information
3.4.2	Validation Rule Information
3.4.3	Record Type Information
3.4.4	Workflow Rule Information
3.4.5	Sharing Rules
3.5	Contact
3.5.1	Page Layout Information
3.5.2	Validation Rule Information
3.5.3	Apex Trigger Information
3.6	Opportunity (Deal)
3.6.1	Page Layout Information
3.6.2	Sales Process Information
3.6.3	Record Type Information
3.6.4	Validation Rule Information
3.6.5	Workflow Rule Information
3.6.6	Approval Process Information
3.6.7	Buttons Information
3.6.8	Apex Trigger Information
3.7	Cases
3.7.1	Page Layout Information
3.7.2	Support Process Information
3.7.3	Record Type Information
3.7.4	Buttons Information
3.7.5	Case Auto Response Rule
3.7.6	Apex Trigger Information
3.8	Contract
3.8.1	Page Layout Information
3.8.2	Record Type Information
3.8.3	Validation Rule Information
3.8.4	Workflow Rule Information
3.8.5	Approval Process Information
3.8.6	Buttons Information
3.8.7	Apex Trigger Information
3.9	Contract Line
3.9.1	Page Layout Information
3.9.2	Validation Rule Information
3.9.3	Workflow Rule Information
3.9.4	Apex Trigger Information
3.10	Activities (Tasks / Events)
3.10.1	Page Layout Information
3.10.2	Apex Trigger Information
3.11	Cobone API
3.11.1	Page Layout Information
3.11.2	Workflow Rule Information
3.11.3	Apex Trigger Information
3.12	Conditions and Highlights Master
3.12.1	Page Layout Information
3.12.2	Apex Trigger Information
3.13	Country
3.13.1	Page Layout Information
3.14	Customer
3.14.1	Page Layout Information
3.15	Deal Outlets
3.15.1	Page Layout Information
3.15.2	Validation Rule Information
3.15.3	Apex Trigger Information
3.16	Hotel
3.16.1	Page Layout Information
3.17	Purchase
3.17.1	Page Layout Information
3.17.2	Workflow Rule Information
3.17.3	Apex Trigger Information
3.18	Refund/Reward
3.18.1	Page Layout Information
3.19	Scheduling
3.19.1	Page Layout Information
3.20	Score Card
3.20.1	Page Layout Information
3.21	Venue
3.21.1	Page Layout Information
3.21.2	Validation Rule Information
3.21.3	Buttons Information
3.22	Vertical
3.22.1	Page Layout Information
3.22.2	Validation Rule Information
3.22.3	Record Type Information
3.23	Security
3.23.1	Org-Wide Default
3.23.2	Role Hierarchy
3.23.3	Profiles
3.23.4	Record Types
3.23.5	Queues
3.23.6	Profiles
3.23.7	Role Hierarchy
3.23.8	Org-Wide Default
3.24	Apex Classes
3.25	Visual Force Pages
3.26	Test Classes

