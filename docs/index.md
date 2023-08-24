![](media/image1.jpeg){width="1.5104166666666667in"
height="1.0729166666666667in"}

UpdateVOIPLineMigrationStatus

Revision: 1

Middleware Service Specification

Author: **Ali Kamal**

raja.alikamal@virginmedia.co.uk

Date: **30-Apr-2019**

Document Version: **1.0**

Status: **Issued**[[[[]{#_Toc182625567 .anchor}]{#_Toc182625192
.anchor}]{#_Toc103152334 .anchor}]{#_Toc103152294 .anchor}

Document Purpose

The Service Specification document is a subjective document which
describes the interface, operations and implementation of a single
service.

It is produced by the Middleware Solution Designer and is the key input
to the Middleware Development Team.

It also serves the purpose of an as-built reference to describe the
production service and, as such, forms part of the SOA development
deliverables. Every service that is delivered to the SOA platform must
have an accompanying Service Specification which describes the service.

There must at all times be a base-lined version of each Service
Specification which is aligned with the latest production version of the
physical service.

There may also be one or (in the case of parallel development) more
working copies of a Service Specification which have been created as
part of an overall Solution Design for an objective purpose such as a
project. As new versions of a service are delivered to production the
relevant Service Specification would then become the base-lined version
and replace the previous version.

 {#section .Heading1-NC}

\
Table of Contents {#table-of-contents .Heading1-NC}
=================

1 Document Control 4

1.1 Document Information 4

1.2 Document History 4

1.3 SOA Governance Approval 4

1.4 For Review By 4

1.5 Distribution 4

1.6 References 4

1.7 Contributors to this document 6

1.8 Glossary 6

2 Introduction 6

2.1 Document Purpose 6

2.2 Audience 6

3 Integration Flow 7

4 Service Specification 8

4.1 Service Overview 8

**4.1.1** Function(s) 8

**4.1.2** Service Interface Definition 9

**4.1.3** Revision History 10

4.2 Operations 11

**4.2.1** POST 11

4.3 Basic Sanity Checks/Tests 20

**4.3.1** Header Validation Checks 20

**4.3.2** Functionality Checks 20

5 Technical Specification 21

5.1 Operations 21

**5.1.1** POST 21

6 Non-functional requirements 23

6.1 Security Requirements 23

6.2 Configuration Requirements 23

**6.2.1** Timeouts 23

6.3 Performance and Capacity Planning Requirements 23

7 Appendix 24

7.1 Stored Procedure 24

8 Troubleshooting 25

\
Document Control
================

Document Information
--------------------

  ------------------------------ ------------------------------------------------------------------
  **Title**                      UpdateVOIPLineMigrationStatus (Middleware Service Specification)
  **Author / (Last saved by)**   Ali Kamal / (Khan, Saleem)
  **Status**                     Issued
  ------------------------------ ------------------------------------------------------------------

Document History
----------------

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Version**   **Description / Change Comments**                                                                                                                           **Who**          **Date**
  ------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------- -------------------
  0.1           Initial draft – released for internal review.                                                                                                               Saleem Khan      24^th^ May 2018
                                                                                                                                                                                             
                Pending tasks includes:                                                                                                                                                      
                                                                                                                                                                                             
                -   JIRA Ticket (awaiting Project to be created in JIRA).                                                                                                                    
                                                                                                                                                                                             
                -   Performance Status to be updated.                                                                                                                                        
                                                                                                                                                                                             

  0.2           Updated – Internal review comments addressed. Track changes enabled.                                                                                        Saleem Khan      31^st^ May 2018

  0.3           Phone number validation added to the service.                                                                                                               Saleem Khan      05^th^ Jun 2018

  0.4           Reference to the ‘Data Design’ added to this document.                                                                                                      Saleem Khan      21th Jun 2018

  0.5           Header field ‘VMMD-OriginatorURI’ is to be treated as a mandatory field.                                                                                    Saleem Khan      09th July 2018

  0.6           Mapping updated for error code 10008.                                                                                                                       Saleem Khan      18^th^ July 2018

  0.7           Mapping updated for ‘Date Format’ for SP (parameter 'in\_timestamp’). Updated format 'YYYY-MM-DD mm:ss:nn' is to be used.                                   Saleem Khan      03^rd^ Sept 2018

  0.8           Telephone Number validation has been removed from this service. There is no requirement for this service to perform field validation on telephone Number.   Fawad Sikandar   14^th^ Sept 2018

  0.9           Mapping fields ('in\_responsecode' & 'in\_statusreason' swapped to make it in sync with the SP signature.                                                   Saleem Khan      18^th^ Sept 2018

  1.0           Service document “Issued”. Timestamp mapping has been removed. (See Service Limitations)                                                                    Ali Kamal        20^th^ April 2019
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

SOA Governance Approval
-----------------------

***The SOA Governance Authority is required to sign off this service
specification, and ensure that it adheres to SOA standards, before any
further sign off can be sought.***

  **Name**     **Title / Department**   **Approval (Y/N)**
  ------------ ------------------------ --------------------
  Steve King   SOA Governance           

Where the reviewer is not approving the document explain what changes
are needed.

For Review By
-------------

  **Name**                 **Title / Department**              **Approval (Y/N)**
  ------------------------ ----------------------------------- --------------------
  Steve King               Middleware Solution Design Lead     
  Lee Doel                 Middleware Development Lead         
  David Mortimer           Middleware Technical Architecture   
  Steve King               SOA Governance Representative       
  Andrew Zielinski         MW Support Lead                     
  Satishkumar Ponnuswamy   Project Solution Designer           
  Sunil Kumar              Project Solution Designer           
  VMTS Test Team           VMTS Test Team                      

Distribution
------------

Distribution is to the reviewer list above plus the following:

  **Name**   **Title / Department**
  ---------- ------------------------
             
             

References
----------

  ------------------------- --------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Reference**             **Document**                                                    **Link / Path**
  []{#Ref01 .anchor}Ref01   SOA Principles and Policies                                     [SOA Principles and Policies](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Standards/Governance/SOA%20Principles%20and%20Policies.doc)
  []{#Ref02 .anchor}Ref02   SOA Integration Architecture                                    [SOA Integration Architecture](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Standards/Governance/SOA%20Integration%20Architecture.doc)
  []{#Ref03 .anchor}Ref03   SOA Blueprint                                                   [SOA Blueprint](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Standards/Governance/SOA%20Solution%20Blueprint.doc)
  []{#Ref04 .anchor}Ref04   Master Service Error Code List                                  [Master Error List](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Development/Master%20Service%20Error%20Code%20List.xls)
  Ref05                     Performance Sheet                                               [Performance](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Configuration%20Management/Service%20Performance%20and%20Capacity.xls)
  Ref06                     Single Customer Migration Solution Design                       [Link](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Project%20Documentation/21CV/21CV%20Single%20Customer%20Migration/21CV_MaD_SCM_SD_v0%205.docx)
  Ref06                     Data Design Doc (Section 5.6.2 and Section 7.11 are relevant)   [Link](../../Project%20Documentation/Forms/AllItems.aspx?RootFolder=%2fsites%2fsupport%2fTechnology%2fdevsupport%2fsolutiondesign%2fCCMSD%2fSOA%2fProject%20Documentation%2f21CV%2f21CV%20Single%20Customer%20Migration&FolderCTID=&View=%7bD55DC126%2d017E%2d4D1E%2dB111%2d1F2345C4CF38%7dhttp://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Project%20Documentation/21CV/21CV%20Single%20Customer%20Migration/Data%20Delivery%20Document%20-%2021CV%20-%20MaD%20-%20SCM%20and%20MiDaS%20Phase%201%20-%20v0.5.docx)
  ------------------------- --------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[[[[[]{#_Toc183235881 .anchor}]{#_Toc103152502 .anchor}]{#_Toc103152333
.anchor}]{#_Toc103152293 .anchor}]{#_Toc103151773 .anchor}***\
***

Contributors to this document
-----------------------------

The following people provided input into this document.

  --------------- ----------------------------
  **Name**        **Role / Company**
  Nikhil Sharma   Middleware Solution Design
  Madhavi Gude    Middleware Solution Design
  --------------- ----------------------------

Glossary
--------

  --------------------------------- --------------------------------------------------------------------
  **Term **                         **Description**
  Shall                             Mandatory
  Should                            Highly desirable, but not mandatory
  []{#_Ref252190675 .anchor}MiDaS   Migration Data Store – used to track migration related activities.
  --------------------------------- --------------------------------------------------------------------

Introduction
============

Document Purpose
----------------

The Service Specification document is a subjective document which
describes the interface, operations and implementation of a single
service.

It also serves the purpose of an as-built reference to describe the
production service and, as such, forms part of the SOA development
deliverables. Every service that is delivered to the SOA platform must
have an accompanying Service Specification which describes the service.

Audience
--------

This document is created for the following audience:

-   Governance Team

-   Design Team

-   Development Team

-   Testing Team

-   Support Team

\
Integration Flow
================

The UpdateVOIPLineMigrationStatus service is part of the integration
flow “Resource Provisioning”. Please refer to the SOA Blueprint document
\[[Ref03](#Ref03)\] for details of the flow.

 {#section-1 .ListParagraph}

Service Specification 
======================

Service Overview
----------------

### Function(s)

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Operation Name**              **RESTFul Style Operation**   **Function(s)**                                                                                                                                                                                                                                                                                                              **Limitations**
  ------------------------------- ----------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  UpdateVOIPLineMigrationStatus   POST                          This service will facilitate the migration process by allowing consumers to update customer’s migration status in ‘Migration Data Store’ aka ‘MiDaS’.                                                                                                                                                                        The service has in the interface a node for activity.timestamp which is not used. It has been kept in place for backward compatibility but is not used and is not passed to the backend.
                                                                                                                                                                                                                                                                                                                                                                                             
                                                                This service doesn’t perform any transformation logic on input data. It will call the backed Stored Procedure for the data update assuming consumers should have provided the correct data. In case of failure when received from backend this service will wrap the banked failure in its ‘System’ or ‘Business’ failure.   
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Service Interface Definition

The JSON schemas can be found in the below
[location](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Service%20Documentation/UpdateVOIPLineMigrationStatus/UpdateVOIPLineMigrationStatusRequest.json)

-   UpdateVOIPLineMigrationStatusRequest.json

-   UpdateVOIPLineMigrationStatusResponse.json

The policies for RESTful interface as mentioned in Section 3 of [SOA
Principles and
Policies](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Standards/Governance/SOA%20Principles%20and%20Policies.doc)
must be adhered to.

#### Other Details

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                    **Dependencies**                                                               
  -------------------- ---------------------------- ---------------------- ------------------------------------ ------------------ ----------------------------- -------------------------------------------------------------------- --------------------------------------------------------------------------------------- --------------------------------------
  **Operation Name**   **Operation Type**           **Back end systems**   **Other VM SOA platform services**   **Message Type**   **Binding Information**       **Message Exchange Pattern**(Sync – SRR, Async- Define explicitly)   **RESTFul Service EndPoint **                                                           **HTTP Response codes**
                                                                                                                                                                                                                                                                                                                              
                       (Basic, Composed, Process)                                                               (XML/JSON/Other)   (SOAP, RESTFul, JMS, Other)                                                                                                                                                                

  POST                 Basic                        MiDaS                                                       JSON               RESTFul                       Sync – SRR                                                           http(s)://&lt;serverHost&gt;:&lt;serverPort&gt;/restapi/UpdateVOIPLineMigrationStatus   200 (Success) , 400,404,500(failure)
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Revision History

*This section tracks each revision of the service. This is different to
the document version number which may be incremented many times during
design and review stages for a particular service revision. The
intention of the section is to clearly document the delta between
revisions of the same service. This will only be used where the service
has been extended in a backward compatible way.*

There must at all times be a base-lined reversion of each Service
Specification which is aligned with the latest production version of the
physical service.

There may also be one or (in the case of parallel development) more
working copies of a Service Specification Versions and Revisions which
have been created as part of an overall Solution Design for an objective
purpose such as a project. As new versions and revisions of a service
are delivered to production the relevant Service Specification would
then become the base-lined version and replace the previous version.

  **Revision**   **Purpose**        **Description of Changes**
  -------------- ------------------ ------------------------------------------------------------------------------------------
  1              Initial revision   Implemented to updated customer’s migration status in ‘Migration Data Store aka ‘MiDaS’.

 {#section-2 .ListParagraph}

Operations
----------

### POST

#### Business Process

Diagram below highlights the business logic associated with the POST
operation.

![H:\\My Documents\\Project Folder\\21stCV Project\\Single Customer
Migration
Solution\\UpdateVOIPLineMigrationStatus\\UpdateVOIPLineMigrationStatus
Business Response.bmp](media/image3.png){width="6.456944444444445in"
height="6.512561242344707in"}

#### Request

##### Request header

The standard HTTP request headers should contain the following values:

-   content-type: application/json; charset=utf-8

The below set of custom HTTP headers are also to be passed.

![RequestHeader.2.2\_JSON](media/image4.png){width="3.134738626421697in"
height="7.4959995625546805in"}

##### Request Body

![H:\\My Documents\\Project Folder\\21stCV Project\\Single Customer
Migration
Solution\\UpdateVOIPLineMigrationStatus\\UpdateVOIPLineMigrationStatusRequest.png](media/image5.png){width="6.4622626859142605in"
height="8.98113188976378in"}

#### \
Response

##### Response Header

**HTTP Status code**: 200, 400, 404 or 500

![RESTResponse](media/image6.png){width="3.5119991251093614in"
height="8.24799978127734in"}

##### Response Body

![H:\\My Documents\\Project Folder\\21stCV Project\\Single Customer
Migration
Solution\\UpdateVOIPLineMigrationStatus\\UpdateVOIPLineMigrationStatusResponse.png](media/image7.png){width="6.456944444444445in"
height="7.912395013123359in"}

#### Fault

![Fault\_2](media/image8.png){width="3.21875in" height="8.15625in"}

#### Validation Rules

Request must be validated against JSON Schema. Besides that there is no
other validation.

***Header Validations:***

Perform Header Validation on RequestHeader&lt;2.2&gt;.

> *Missing Mandatory elements:*
>
> Throw “10686 - System Exception”.
>
> Nested Exception- “10007 Schema Validation Exception”.

All above Exception will have HTTP Status Code set to 400

***JSON body and URI query parameters Validations:***

> *Missing Mandatory elements:*

Throw “10686 - System Exception“

Nested Exception- “10007 Schema Validation Exception”.

> In addition, perform the following field validations.

-   The ‘task.timeStamp’ should be validated against the pattern
    ‘YYYY-MM-DDT00:00:00Z’.

> *For invalid ‘Phone Number’ and ‘*timeStamp’*:*
>
> Throw 10685 Business Exception
>
> Nested Exception- “10008 Field Validation Exception”.

All above Exception will have HTTP Status Code set to 400

***HTTP Standard Header Validations:***

> *Missing Mandatory elements OR Value in header not as specified:*

Throw “10686 - System Exception“

Nested Exception- “10000 Header Validation Exception”.

HTTP Status Code set to 415

#### Errors

All SOA errors can be found in the SOA Master Error List \[Ref04\]. The
following are the errors that are initiated by this service:

  ------------------------------------------------------------------------------
  **Type**   **Code**   **Severity**   **Description**      **Source**
                                                            
                                                            **System**
  ---------- ---------- -------------- -------------------- --------------------
  SYSTEM     10686      CRITICAL       System Exception     Middleware

  BUSINESS   10685      ERROR          Business Exception   Middleware/Backend
  ------------------------------------------------------------------------------

#### Sample Test Cases

##### Test Case 1 – Success response

###### Purpose of Test

The purpose of this test is where a valid request for
UpdateVOIPLineMigrationStatus ‘POST’ request is passed and a success
response is received.

###### Request

###### Expected Response

Http Code: 200- OK

##### Test Case 2 – Schema Validation Exception 

###### Purpose of Test

The purpose of this test is where the request does not validate/has
schema validation error. {{Mandatory field not passed / invalid data
type}}.

###### Request

###### Expected Response

Http Code: 400- Bad Request

##### Test Case 3 – Backend System Exception 

###### Purpose of Test

The purpose of this test is where there is a business exception during
Stored Procedure invocation.

###### Request

###### Expected Response

Http Code: 500 Internal Server Error

##### Test Case 4 – Backend Timeout Exception 

###### Purpose of Test

The purpose of this test is where there is a timeout exception during
Stored Procedure invocation.

.

###### Request

###### Expected Response

Http Code: 400 Bad Request

##### Test Case 5 – Unexpected Exception 

###### Purpose of Test

The purpose of this test is where there is a system exception.

###### Expected Response

Http Code: 500 Internal Server Error

Basic Sanity Checks/Tests
-------------------------

The test team/individual testing this service should ensure the below
scenarios are covered as minimum in addition to project/solution
specific test scenarios.

### Header Validation Checks

**Testing team** to perform checks to ensure the following header
elements are passed by consumer to middleware service in the Request
Header.

**This is a contractual agreement for consumers but not for development
(i.e. code doesn’t throw any exceptions) **

VMMD-activityName, VMMD-conversationID, VMMD-requestID,
VMMD-requestTimeStamp, VMMD-senderURI, **VMMD-originatorURI**,
VMMD-userid

*Note: ‘VMMD-originatorURI’ must be presented in the request as this is
required for the backend call, an exception must be returned if this
value is not presented.*

The below header elements could be passed when invoking this service.

VMMD-version, VMMD-service, VMMD-operation

**Perform checks to ensure the following header elements are returned in
response Header**

VMMD-conversationId (if passed in the request), VMMD-requestId,
VMMD-requestTimeStamp, VMMD-responseTimeStamp, VMMD-responseStatus,
VMMD-messageID (if passed in the request)

### Functionality Checks

  1   Perform scenarios for mandatory and non-mandatory request elements
  --- -----------------------------------------------------------------------------------------
  2   Perform scenarios for all error codes of the service
  3   Perform scenarios to check configuration changes if any
  4   Perform scenarios to check mandatory response elements (non-mandatory where applicable)
  6   Perform test with invalid SP credentials (user/pwd or SP name).
  7   Perform test with invalid Activity and tasks.

***NOTE:  The above scenarios are just to cover the basic features of
this service. ***

***The service test cases created should cover the above AT LEAST, but
NOT just that.***

Solution specific and Project specific scenarios are in addition to the
above and needs to be identified by the test team and created in their
test plan.

\
Technical Specification
=======================

Operations
----------

### POST

#### Technical Process

![H:\\My Documents\\Project Folder\\21stCV Project\\Single Customer
Migration
Solution\\UpdateVOIPLineMigrationStatus\\UpdateVOIPLineMigrationStatus
Technical Response.bmp](media/image18.png){width="6.45599956255468in"
height="7.576000656167979in"}

##### Perform Request Validation

-   Upon receiving service request, perform request validation as
    specified in validation section (section –
    [4.2.1.4](#validation-rules)).

-   If the request validation fails, send a failure response to the
    consumer.

-   To build the response refer to ’To Response (Failure)’ tab in the
    Data Mapping Sheet (section – [5.1.1.2](#data-mapping-sheet)).
    **Operation returns to calling client.**

##### Invoke Database function to retrieve the ‘Provisioning Status’

-   Using Data Mapping sheet call the following database function:

    -   Function Name: update\_migration\_status

-   In case of a failure invoking the backend, build a failure response
    – refer to ’To Response (Failure)’ tab in the Data Mapping Sheet.
    **Operation returns to calling client.**

##### Process the Database Response

-   *For any failure received from backend build the failure response
    object for the consumer. Where errors codes returned from backend
    are available as per the configuration* (section –
    [5.1.1.2](#data-mapping-sheet)) build a business error, in case
    corresponding error code is not available in the configuration this
    is to be treated as technical error. Refer to ’To Response
    (Failure)’ tab in the Data Mapping Sheet. **Operation returns to
    calling client.**

#### Data Mapping Sheet

[]{#_MON_1598428312 .anchor}

\
Non-functional requirements
===========================

Security Requirements
---------------------

Follow BAU security standards, this is no service specific
requirement/standards to implement.

Configuration Requirements
--------------------------

### Timeouts

#### Backend Stored Procedure Timeout

Read timeout for calling the Stored Procedure.

  **Time in Seconds**   **Database Function**
  --------------------- ---------------------------
  3                     update\_migration\_status

Performance and Capacity Planning Requirements
----------------------------------------------

**Note:** Performance and capacity requirements are held in associated
UpdateVOIPLineMigrationStatus configuration and
[Performance](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Configuration%20Management/Service%20Performance%20and%20Capacity.xls)
document.

-   Expected number of service invocations per day: 1,00,000/day and
    *5000*/hr

-   Expected peak concurrent service invocations: 60 concurrent

-   95^th^ percentile response time: &lt; 0.75 second

Appendix
========

Stored Procedure
----------------

Below document describes the Stored Procedure signature and sample
values to be used for updating the MiDaS data.

PROCEDURE update\_migration\_status(

in\_telephonenumber IN VARCHAR2,

in\_migrationphase IN VARCHAR2,

in\_migrationtask IN VARCHAR2,

in\_taskstatus IN VARCHAR2,

in\_responsecode IN VARCHAR2,

in\_statusreason IN VARCHAR2,

in\_notes IN VARCHAR2,

in\_sourcesystem             IN VARCHAR2,

in\_timestamp IN VARCHAR2,

out\_return\_code             OUT NUMBER,

out\_return\_message     OUT VARCHAR2)

 {#section-3 .ListParagraph}

Troubleshooting
===============

Following table can be used to investigate the errors which could be
returned from this service, their root cause, potential resolution and
monitoring options.

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Symptom**                                                   **Cause**                                                                                                                                         **Resolution**                                             **Monitoring Method**
  ------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------- ------------------------------------------------------------------
  Operation is returning error code 10685 in HTTP 400 payload   Business Exception. The backend service could have thrown business exception.                                                                     Review the middleware logs and investigate error details   Watch the service log file for any instance of error code 10685.
                                                                                                                                                                                                                                                                             
                                                                There may be validation errors                                                                                                                                                                               

  Operation is returning error code 10686 in HTTP 500 payload   System Exception.                                                                                                                                 Review the middleware logs and investigate error details   Watch the service log file for any instance of error code 10686
                                                                                                                                                                                                                                                                             
                                                                The backend service could have thrown System exception. It is also possible that there is system or validation exception in the service itself.                                                              
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
