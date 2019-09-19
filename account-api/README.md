# This is exercise part 1 

- Basic Auth: there are 2 users defined in file security-beans.xml. Only user admin/admin is authorized cal the API

- HTTPS: exposed on port 8082. Related TLS/JCEKS under src/main/resources/tls/server.jks. The TLSContext related properties defined in file src/main/resources/secure-config.local.yaml. password related entry are encrypted.

- Custom Business Events: All transaction ID set to message correlationId. There is CBE at begining of the HTTP listener and also at the end of HTTP response fase, no matter success or exception

- Exception handling: APIKit defined exception are customized to return message compliant with RAML 400/500. 
Besides, 401/BasicAuth processed.
API implementation flow will throw customized exception and handled there 

- Munit: implemented for create account. There are 2 test case defined: One for 201 creted and other for 400. Each test case will mock the Salesforce Connector and assert response contents. For 201, assert Location header and empty payload; for 400, assert status code and payload message subcode.

- Postman collection: under folder postman. Each request attached 1 example.

- global properties: All secured properties defined in secure-config.local.yaml. Gloabl config(non secured) are defined in global-config.local.yaml.
global env/key are defined and set default env=local

- log4j: customized log categories with 2 log files. One for API invocation which will record each HTTP request/response. See files under logs/account-api-tx.log
The other one is audit log to record who is making the API request. See file under logs/account-api-audit.log



