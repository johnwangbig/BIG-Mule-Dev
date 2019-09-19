# This is exercise part 2 - BATCH

- running result log file: under logs/ there are 2  log files customized in log4j2.xml. One file for each batch job instance execution reporting and one for reporting each record processing.

- configuration files: salsforce and MySQL connection properties uas encrpted. Also, the file name is enviroment specic with PROPERTY_FILE.${env}.yaml. env is default to "local"

- Batch job applied aggreagtor steps for DB insert/update. aggregator size defined in properties

- Each batch job instance will only handle limited records to avoid long running batch process - which defined in properties file also

- High Watermark enforced with Salesforce Account record LastModifiedDatetime field.

- Batch job will first check recored existence and set the flag.

- For account insertion step, step acceptance policy/exprssion will choose only those not exsitence account and use bulk insert

- for account updates step, same as above logic

- For any failured processing recores, Failre step was added with accept policy = FAILURE_OMLY and report all error details in file.

- Each job instance will emit CBE at start and end