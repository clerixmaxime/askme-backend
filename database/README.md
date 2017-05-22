# Database

Build MySQL Database using officiel mysql5.7 Red Hat image and adding questions.sql script under /var/lib/mysql. Creation of questions user has been removed from questions.sql

```
oc new-build https://github.com/clerixmaxime/askme-backend.git --context-dir=/database --strategy=docker --to=askme-db --name=askme-db
```

Launching mysql database using askme credentials questions/x2YfU8vHqAATS7Sh
```
oc new-app askme-db --name=database -e MYSQL_ROOT_PASSWORD='pass' -e MYSQL_USER='questions' -e MYSQL_PASSWORD='x2YfU8vHqAATS7Sh'
```

Adding deployment-hook that triggers execution of questions.sql
```
oc set deployment-hook dc/database --post -c database -- /bin/sh -c 'hostname && sleep 20 && /opt/rh/rh-mysql57/root/usr/bin/mysql -h database -u root --password=pass -P 3306 < /var/lib/mysql/questions.sql'
```

Redeployment of the database after adding hook.
```
oc rollout latest database
```
