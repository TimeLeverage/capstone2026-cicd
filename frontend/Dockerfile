# 1단계: 빌드 스테이지
FROM eclipse-temurin:17-jdk-jammy AS builder
WORKDIR /app

# 소스코드 복사 및 빌드 실행 (gradle인 경우 ./gradlew 빌드 명령어로 변경)
COPY . .
RUN ./mvnw clean package

# 2단계: 실행 스테이지
FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app

# 빌드 스테이지에서 생성된 jar 파일을 복사
COPY --from=builder /app/target/*.jar app.jar

ENTRYPOINT ["java", "-jar", "/app.jar"]