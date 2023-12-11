FROM openjdk:17-oracle
LABEL authors="Rashmit Pankhania"

WORKDIR /app

COPY /target/service1-0.0.1-SNAPSHOT.jar /app

EXPOSE 8081

CMD ["java", "-jar", "service1-0.0.1-SNAPSHOT.jar"]