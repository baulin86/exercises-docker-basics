FROM amazoncorretto:8

# Устанавливаем tar и gzip, необходимые для работы Maven Wrapper
RUN yum install -y tar gzip && yum clean all

WORKDIR /app

# Копируем файлы Maven Wrapper и pom.xml для кэширования зависимостей
COPY .mvn/ .mvn/
COPY mvnw pom.xml ./

# Даём права на выполнение и скачиваем зависимости
RUN chmod +x mvnw && ./mvnw dependency:go-offline -B

# Копируем исходный код и собираем проект
COPY src ./src
RUN ./mvnw package -DskipTests

# Открываем порт 8080
EXPOSE 8080

# Запускаем приложение согласно README
ENTRYPOINT ["java", "-jar", "./target/docker-example-1.1.3.jar"]
