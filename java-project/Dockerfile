FROM codesignal/java:new

# Pulling things from the maven central repository into maven's cache at ~/.m2

# Argument explanation:
# -Dartifact=groupId:artifactId:version[:packaging][:classifier]
#   specifies the target artifact. Packaging is default `jar` but might be `pom`
RUN mvn dependency:get -Dartifact=junit:junit:4.12 \
    && mvn dependency:get -Dartifact=com.fasterxml.jackson.core:jackson-core:2.8.11 \
    && mvn dependency:get -Dartifact=org.javassist:javassist:3.21.0-GA \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-dependency-plugin:3.1.0 \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-compiler-plugin:3.1 \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-compiler-plugin:3.2 \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-resources-plugin:3.1.0 \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-resources-plugin:2.7 \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-resources-plugin:2.6 \
    && mvn dependency:get -Dartifact=junit:junit:3.8.2 \
    && mvn dependency:get -Dartifact=org.junit.jupiter:junit-jupiter-engine:5.1.0 \
    && mvn dependency:get -Dartifact=org.hibernate:hibernate-agroal:5.3.7.Final:pom \
    && mvn dependency:get -Dartifact=com.h2database:h2:1.4.197 \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-surefire-plugin:2.17 \
    && mvn dependency:get -Dartifact=org.apache.maven.plugins:maven-surefire-plugin:2.18.1 \
    && mvn dependency:get -Dartifact=org.apache.maven.surefire:surefire-junit4:2.17 \
    && mvn dependency:get -Dartifact=org.apache.maven.surefire:surefire-junit4:2.18.1 \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-parent:2.1.0.RELEASE:pom \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-parent:1.5.15.RELEASE:pom \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-actuator:2.1.0.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-actuator:1.5.15.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-maven-plugin:2.1.0.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-maven-plugin:1.5.15.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-data-jpa:2.1.0.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-data-jpa:1.5.15.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-web:2.1.0.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-web:1.5.15.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-test:2.1.0.RELEASE \
    && mvn dependency:get -Dartifact=org.springframework.boot:spring-boot-starter-test:1.5.15.RELEASE
