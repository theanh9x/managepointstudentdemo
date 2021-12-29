FROM maven:3.5-jdk-8-alpine AS BUILD
WORKDIR /home/app
COPY managepointstudent-api /home/apps/managepointstudent/managepointstudent-api
COPY managepointstudent-client /home/apps/managepointstudent/managepointstudent-client
COPY managepointstudent-service /home/apps/managepointstudent/managepointstudent-service
COPY authz /home/apps/authz

COPY yaml /home/app/yaml
COPY pom.xml /home/app/
RUN mvn clean package -DskipTests

FROM openjdk:8-jdk-alpine
COPY --from=BUILD /home/app/managepointstudent/managepointstudent-service/target/managepointstudent-service-0.0.1.jar managepointstudent-service-0.0.1.jar
ENTRYPOINT ["java","-jar","managepointstudent-service-0.0.1.jar"]