# ApplicationDatabases

Do application database creation and destruction reproducibly. Include application logins in that.

```
New-PostgresApplicationDatabase.ps1
Set-PostgresTemplate1DefaultLocale.ps1
New-SqlServerApplicationDatabase.ps1 [WIP, not finished]
```

#### New-PostgresApplicationDatabase.ps1
    
```
SYNOPSIS: Create a Postgres application database and roles for owner, application, and application_readonly   
    
SYNTAX
    New-PostgresApplicationDatabase.ps1 [[-databaseName] <String>] 
    [[-postgresHost] <String>] [[-adminUser] <String>] [[-databaseOwner] <String>] [[-appAccount] <String>] 
    [[-appAccountPassword] <String>] [[-readonlyAppAccount] <String>] [[-readonlyAppAccountPassword] <String>] 
    [[-template] <String>] [-template0] [[-encoding] <String>] [[-locale] <String>] [[-addUUID] <Boolean>] 
    [-addFunctionsForPSAndDropConnections] [-addPlv8] [-addTrigram] [-dryRun] [-help] [-helpAvailableLocales] 
    [-deleteDatabaseAndRoles] [<CommonParameters>]  
    
DESCRIPTION
    Create a Postgres application database and create roles for owner, application, and application_readonly.
    
    - the owner role has no login. the user that runs this script will be assigned to that role
    - the application and application_readonly roles will be login roles with password either specified by you
      or generated by this script. 
    - If the passwords are generated by this script, they will be printed as the first 
      2 lines of output of this script. 
    - If the script scram_postgres_password.py exists in the path, the passwords will be scram encrypted.
    
    - Optionally install common extensions UUID, plv8 and trigram
    - Optionally create functions for view and drop database connections
```

#### Set-PostgresTemplate1DefaultLocale.ps1
```
SYNOPSIS : Update Postgres template1 (which is the default template used by Create Database) to your preferred Locale settings.
    
SYNTAX
    Set-PostgresTemplate1DefaultLocale.ps1 [[-dbLocale] <Object>] 
    [[-postgresHost] <Object>] [[-adminUser] <String>] [[-dbEncoding] <Object>] [-createViewAndDropConnectionFunctions] 
    [-addPlv8] [-addTrigram] [-addUUID] [-dryRun] [<CommonParameters>]

```

#### New-SqlServerApplicationDatabase.ps1 [WIP, not finished]
```  
SYNOPSIS: Create an MS SQL Server application database and roles for owner, application, and application_readonly

SYNTAX
    New-SqlServerApplicationDatabase.ps1 [[-databaseName] <String>] 
    [[-serverInstance] <String>] [[-loginCreatorLogin] <String>] [[-loginCreatorPassword] <String>] [[-databaseOwner] 
    <String>] [[-appLogin] <String>] [[-appLoginPassword] <String>] [[-readonlyappLogin] <String>] 
    [[-readonlyappLoginPassword] <String>] [[-loginLanguage] <String>] [[-databaseCollation] <String>] [-dryRun] [-help] 
    [-deleteDatabaseAndRoles] [<CommonParameters>]
    
    
DESCRIPTION
    Create an MS SQL Server application database and create roles for owner, application, and application_readonly.
    
    - the owner role has no login. the user that runs this script will be assigned to that role
    - the application and application_readonly roles will be login roles with password either specified by you
      or generated by this script. 
    - If the passwords are generated by this script, they will be printed as the first 
      2 lines of output of this script. 
    - If the script scram_postgres_password.py exists in the path, the passwords will be scram encrypted.
    
    - Optionally install common extensions UUID, plv8 and trigram
    - Optionally create functions for view and drop database connections
```
