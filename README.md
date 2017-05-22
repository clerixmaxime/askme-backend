# askme-backend
Backend for the Accenture askme application

Classic build using S2I NodeJS official image. /!\ Created service listen on port 8080 instead of 8081 (To check) Interne et externe
```
oc new-build nodejs~https://github.com/clerixmaxime/askme-backend.git --to=askme-backend --name=askme-backend
```
Launching backend, specifying the location of the database with DB_PORT_3306_TCP_ADDR env variable
```
oc new-app askme/askme-backend --name=backend -e DB_PORT_3306_TCP_ADDR='database'
```

/!\ When creating the backend via `oc new-app`, it will create a service that listens on port 8080 and expose the port 8080 it should be replace by port 8081. You could the following to change the service:
```
oc delete svc backend 
oc expose dc/backend --port=8081 --target-port=8081
```
