spring.jackson.date-format=dd.MM.yyyy
spring.jackson.time-zone=IST
spring.jackson.serialization.write-dates-as-timestamps=false

spring.mvc.view.prefix=/WEB-INF/view/
spring.mvc.view.suffix=.jsp

spring.datasource.url=jdbc:postgresql://localhost:5433/employees
spring.datasource.username=postgres
spring.datasource.password=samiksha
spring.jpa.show-sql=true
spring.main.allow-bean-definition-overriding=true
## Hibernate Properties
# The SQL dialect makes Hibernate generate better SQL for the chosen database
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.PostgreSQLDialect

# Hibernate ddl auto (create, create-drop, validate, update)
spring.jpa.hibernate.ddl-auto = update
logging.level.org.hibernate.SQL=DEBUG
logging.level.org.hibernate.type=TRACE

spring.jpa.generate-ddl=true
spring.profiles.active=@spring.profiles.active@
