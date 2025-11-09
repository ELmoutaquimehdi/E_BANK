# Étape 1 : Construire le jar avec Maven
FROM maven:3.9.2-eclipse-temurin-17 AS build
WORKDIR /app

# Copier les fichiers Maven
COPY pom.xml .
COPY src ./src

# Construire le projet sans tests
RUN mvn clean package -DskipTests

# Étape 2 : Exécuter le jar avec JDK
FROM eclipse-temurin:17-jdk
WORKDIR /app

# Copier le jar depuis l'étape de build
COPY --from=build /app/target/ebanking-backend-0.0.1-SNAPSHOT.jar app.jar

# Exposer le port de l'application (comme dans application.properties)
EXPOSE 8085

# Variables d'environnement pour MySQL
ENV SPRING_DATASOURCE_URL="jdbc:mysql://mysql:3306/E-BANK?createDatabaseIfNotExist=true"
ENV SPRING_DATASOURCE_USERNAME="root"
ENV SPRING_DATASOURCE_PASSWORD=""
ENV SPRING_JPA_HIBERNATE_DDL_AUTO="create"
ENV SPRING_JPA_SHOW_SQL="true"



# Lancer l'application
ENTRYPOINT ["java", "-jar", "app.jar"]
