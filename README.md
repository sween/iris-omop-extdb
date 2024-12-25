# OMOP

![](assets/h243-ohdsi-logo-with-text.png)

<details>
<summary>Dependency Detail</summary>

### OS Dependencies
This may provide some hints to any OS libraries that is needed for the below R packages to successfully
install so I included it here.  My OS is Pop!_OS 24.04 LTS x86_64 (Ubuntu), so the below is what I found
to be necessary installing the R packages... your mileage may vary based on your OS, but may provide some
hints.

```
sudo apt install libcurl4-openssl-dev systemfonts textshaping libharfbuzz libfribidi-dev libfreetype6-dev libpng-dev libtiff5-dev libjpeg-dev r-cran-rjava
```

### R Dependencies
This is straight outta the [OHDSI CDM](https://github.com/OHDSI/CommonDataModel),


```
install.packages("DatabaseConnector")
install.packages("SqlRender")
install.packages("here")
```

### Jars

```
Sys.setenv("DATABASECONNECTOR_JAR_FOLDER" = "/home/sween/Desktop/OMOP/iris-omop-extdb/jars")
```
</details>



### PostgreSQL

```
CommonDataModel::buildRelease(cdmVersions = "5.4",
                              targetDialects = "postgresql",
                              outputfolder = "./ddl/postgres/test")
```

### Amazon RDS

```
cd <- DatabaseConnector::createConnectionDetails(dbms = "postgresql",
                                                 server = "extrdp-ops.cebtem2mjzus.us-east-2.rds.amazonaws.com/OMOPCDM54",
                                                 user = "postgres",
                                                 password = "REDACTED",
                                                 pathToDriver = "./jars"
                                                 )

CommonDataModel::executeDdl(connectionDetails = cd,
                            cdmVersion = "5.4",
                            cdmDatabaseSchema = "omopcdm54"
                            )
```

### Google Cloud SQL

```
cd <- DatabaseConnector::createConnectionDetails(dbms = "postgresql",
                                                 server = "34.59.122.238/OMOPCDM54",
                                                 user = "postgres",
                                                 password = "REDACTED",
                                                 pathToDriver = "./jars"
                                                 )

CommonDataModel::executeDdl(connectionDetails = cd,
                            cdmVersion = "5.4",
                            cdmDatabaseSchema = "omopcdm54"
                            )
```


