FROM openjdk:17-oracle
LABEL authors="Rashmit Pankhania"

WORKDIR /app

COPY /target/service2-0.0.1-SNAPSHOT.jar /app

EXPOSE 8081

CMD ["java", "-jar", "service2-0.0.1-SNAPSHOT.jar"]