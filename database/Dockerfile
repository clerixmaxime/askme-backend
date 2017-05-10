FROM registry.access.redhat.com/rhscl/mysql-57-rhel7

# Make a folder for our backend
# RUN mkdir /app

# Attach backend to container
ADD ./questions.sql /docker-entrypoint-initdb.d

ENV MYSQL_ROOT_PASSWORD pass

EXPOSE 3306
