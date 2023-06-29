# Дипломный проект по профессии «Тестировщик»
Дипломный проект представляет собой автоматизацию тестирования комплексного сервиса, взаимодействующего с СУБД и API Банка

# Инструкция по запуску автотестов
## 1.Подготовка окружения
### 1.1 Установленное ПО
Git
IntelliJ IDEA
JDK 11
Docker Desktop (https://github.com/netology-code/aqa-homeworks/blob/master/docker/installation.md , обратить внимание на системные требования)
### 1.2 Запуск Docker Desktop
Открыть Docker Desktop
При первом использовании может понадобиться авторизация на Docker Hub
### 1.3 Инициализация контейнеров с СУБД MySQL, PostgreSQL и симулятором банковских сервисов
В IntelliJ IDEA открыть терминал (Alt+F12)
Выполнить команду: ___docker-compose up___
Дождаться сборки контейнера
### 1.4. Запуск SUT с подключением к MySQL
В IntelliJ IDEA открыть дополнительную вкладку с терминалом кликом по кнопке +
Выполнить команду: ___java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar artifacts/aqa-shop.jar___
### 1.5. Запуск SUT с подключением к PostgreSQL
В IntelliJ IDEA открыть дополнительную с терминалом кликом по кнопке +
Выполнить команду: ___java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar artifacts/aqa-shop.jar___
## 2. Запуск автотестов
В IntelliJ IDEA дважды нажать Ctrl и в командной строке «Run Anything» выполнить одну из команд в зависимости от выбранной СУБД:
___MySQL: ./gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app"___
___PostgreSQL: ./gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app"___
## 3. Создание отчёта Allure
В IntelliJ IDEA выполнить команду: ___./gradlew allureServe___
После выполнения всех тестов остановить docker контейнер командой в консоли: docker-compose down
