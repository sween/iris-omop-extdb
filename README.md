# OMOP

![My Test Image](assets/h243-odsi-logo-with-text.png)


## Dependencies
```
install.packages("DatabaseConnector")
install.packages("SqlRender")
```

Here

```
CommonDataModel::buildRelease(cdmVersions = "5.4",
                              targetDialects = "postgresql",
                              outputfolder = "/home/sween/Desktop/OMOP/iris-omop-extdb/ddl/postgres/rds")
```

## Jars
```
Sys.setenv("DATABASECONNECTOR_JAR_FOLDER" = "/home/sween/Desktop/OMOP/iris-omop-extdb/jars")
```

## Load CDM5.4
```
cd <- DatabaseConnector::createConnectionDetails(dbms = "postgresql",
                                                 server = "extrdp-ops.cebtem2mjzus.us-east-2.rds.amazonaws.com/OMOPCDM54",
                                                 user = "postgres",
                                                 password = "REDACTED",
                                                 pathToDriver = "/home/sween/Desktop/OMOP/iris-omop-extdb/jars"
                                                 )

CommonDataModel::executeDdl(connectionDetails = cd,
                            cdmVersion = "5.4",
                            cdmDatabaseSchema = "omopcdm54"
                            )
```


