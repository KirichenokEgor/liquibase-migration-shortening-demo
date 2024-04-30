# liquibase-migration-shortening-demo
This project shows how to reduce the number of changelogs in Liquibase.

version 1
Инструкция для утилиты по сокращению кол-ва миграция liquibase:
1. в pom.xml в pluginManagement для плагина liquibase-maven-plugin устанавливаем параметры url, username, password в соответствии с нужной БД;
2. если хотим сократить кол-во миграций:
   а. только для структуры БД (без данных), то в pom.xml для параметра diffTypes устанавливаем значение tables,views,columns,indexes,foreignkeys,primarykeys,uniqueconstraints ;
   а. для структуры БД и данных, то в pom.xml для параметра diffTypes устанавливаем значение tables,views,columns,indexes,foreignkeys,primarykeys,uniqueconstraints,data ;
3. в командной строке выполняем mvn liquibase:generateChangeLog ;
4. в файле result.xml (или другом, определённом в параметре outputChangeLogFile в pom.xml) получаем результат.

P.S. если хотим работать со структурой БД и со справочными данными, но при этом не хотим трогать бизнесовые данные, необходимо создать отдельную БД и накатить на неё все изначальные миграции

version 2
добавил пример
для запуска
1. накатываем миграции с помощью mvn liquibase:update ;
2. обобщаем их с помощью mvn liquibase:generateChangeLog