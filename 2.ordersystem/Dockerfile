# 첫 번째 스테이지 (빌드 단계)
FROM amazoncorretto:17-alpine as stage1
WORKDIR /app
COPY gradle gradle
COPY src src
COPY build.gradle .
COPY settings.gradle .
COPY gradlew .
RUN chmod +x gradlew
RUN ./gradlew bootJar

# 두 번째 스테이지 (실행 단계) - 이 부분을 수정했습니다!
FROM amazoncorretto:17-alpine 
WORKDIR /app
# 빌드된 jar 파일만 복사
COPY --from=stage1 /app/build/libs/*.jar app.jar

# 실행
ENTRYPOINT ["java", "-jar", "app.jar"]