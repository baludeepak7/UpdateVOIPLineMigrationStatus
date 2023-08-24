UpdateVOIPLineMigrationStatus

Service Description
===================

*The UpdateVOIPLineMigrationStatus service is part of the integration
flow “Resource Provisioning”.This service will facilitate the migration
process by allowing consumers to update customer’s migration status in
‘Migration Data Store’ aka ‘MiDaS’.This service doesn’t perform any
transformation logic on input data. It will call the backed Stored
Procedure for the data update assuming consumers should have provided
the correct data. In case of failure when received from backend this
service will wrap the banked failure in its ‘System’ or ‘Business’
failure.*[[]{#scroll-bookmark-2064 .anchor}]{#_Toc256000916 .anchor}

### UpdateVOIPLineMigrationStatus

### Request 

  **Parameter Name**                                       **Type**
  -------------------------------------------------------- ----------
  UpdateVOIPLineMigrationStatus.telephoneNumber            string
  UpdateVOIPLineMigrationStatus.activity                   Object
  UpdateVOIPLineMigrationStatus.activity.name              string
  UpdateVOIPLineMigrationStatus.activity.task              Object
  UpdateVOIPLineMigrationStatus.activity.task.name         string
  UpdateVOIPLineMigrationStatus.activity.task.status       string
  UpdateVOIPLineMigrationStatus.activity.task.reason       string
  UpdateVOIPLineMigrationStatus.activity.task.reasonCode   string
  UpdateVOIPLineMigrationStatus.activity.task.comments     string
  UpdateVOIPLineMigrationStatus.activity.task.timestamp    dateTime

Error response {#error-response .ListParagraph}
--------------

  **Type**   **Code**   **Description**      **Severity**   **Source System**
  ---------- ---------- -------------------- -------------- --------------------
  SYSTEM     10686      System Exception     CRITICAL       Middleware
  BUSINESS   10685      Business Exception   ERROR          Middleware/Backend
