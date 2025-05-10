/*
README for Compliance Checker - Quarkus + Drools

Overview
--------
This Quarkus-based microservice evaluates building design compliance against predefined rule sets (e.g., energy codes, LEED v4.1 prerequisites) using Drools.

Requirements
------------
- Java 17 or later
- Maven 3.6+
- Quarkus 3.x
- Drools KIE API

Build & Run
-----------
1. Create a standard Maven project and add these dependencies to your pom.xml:

```xml
<dependencies>
  <!-- Quarkus dependencies -->
  <dependency>
    <groupId>io.quarkus</groupId>
    <artifactId>quarkus-resteasy-reactive</artifactId>
  </dependency>
  <dependency>
    <groupId>io.quarkus</groupId>
    <artifactId>quarkus-kogito-dmn</artifactId>
  </dependency>
  <!-- Drools KIE -->
  <dependency>
    <groupId>org.drools</groupId>
    <artifactId>drools-core</artifactId>
    <version>8.40.0.Final</version>
  </dependency>
  <dependency>
    <groupId>org.drools</groupId>
    <artifactId>drools-compiler</artifactId>
    <version>8.40.0.Final</version>
  </dependency>
</dependencies>
```

2. Place this file under `src/main/java/com/example/compliance/ComplianceCheckerApp.java`.
3. Run from the project root:

```bash
mvn clean package
java -jar target/*-runner.jar
```

API
---
**POST** `/compliance/check`
- **Request JSON**:
  ```json
  {
    "height": 60.0,
    "area": 1200.0,
    "stories": 6
  }
  ```
- **Response JSON** (list of rule results):
  ```json
  [
    {"ruleName":"Height Compliance","passed":false,"message":"Height exceeds 50m"},
    {"ruleName":"Area Compliance","passed":true,"message":"Area is within limits"},
    {"ruleName":"Stories Compliance","passed":true,"message":"Stories count is compliant"}
  ]
  ```
*/
