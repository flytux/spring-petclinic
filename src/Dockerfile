FROM openjdk:11.0.1-jdk-slim-stretch AS build-env
ARG JAR=spring-petclinic-2.4.2.jar
ADD . /app
WORKDIR /app
RUN sh ./mvnw clean package -DskipTests=true


FROM openjdk:11.0.1-jre-slim-stretch
COPY --from=build-env /app/target/$JAR /app/app.jar
WORKDIR /app
CMD ["java", "-jar", "app.jar"]

EXPOSE 8080
