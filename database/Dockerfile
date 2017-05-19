FROM registry.access.redhat.com/rhscl/mysql-57-rhel7

# Make a folder for our backend
# RUN mkdir /app

# Attach backend to container
COPY ./questions.sql /var/lib/mysql/questions.sql

EXPOSE 3306
