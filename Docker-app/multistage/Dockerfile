FROM maven:3.8-openjdk-11 AS build
WORKDIR /app
COPY . .
RUN mvn package -DskipTests

# Stage 2: Deploy to Tomcat
FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build /app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
CMD ["catalina.sh", "run"]
