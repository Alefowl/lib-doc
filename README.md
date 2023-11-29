Alefowl.com: библиотека билингвальных книг

ДОСТУПЫ
- получите у Founder / Product owner доступы к необходимым сервисам, таким как Miro (опционально), GitHub(обязательно)
- зарегистрируйтесь на сайте http://www.alefowl.com)

ДЛЯ НАЧАЛА РАБОТЫ НЕОБХОДИМО
- скачайте и установите базу данных PostgreSQL ( https://www.postgresql.org/ )
- скачайте и установите Postman ( https://www.postman.com/downloads/ )
- скачайте и установите Git ( https://git-scm.com/ )
- скачайте и установите Java версии не ниже 1.8 ( https://www.java.com/ru/download/manual.jsp ) (проверка: java -version)
- скачайте и установите Scala версии 2.13.11 (https://scala-lang.org/download/2.13.11.html)
- скачайте и установите sbt версии 1.5.8 (проверка: sbt -version) (https://www.scala-sbt.org/download.html)
- скачайте и установите Idea* ( https://www.jetbrains.com/ru-ru/idea/ )
    * вместо Idea можно использовать Visual Studio Code, если это удобнее https://code.visualstudio.com/download
ИНСТРУКЦИЯ ДЛЯ ЛОКАЛЬНОГО РАЗВЕРТЫВАНИЯ ПРОЕКТА

СОЗДАНИЕ ЛОКАЛЬНОЙ БД
1) создайте в pgAdmin новую БД под названием 'alefowl', postgres-postgres (эта БД должна иметь такую же структуру, как и удаленная БД).
2) создайте в БД таблицы (для создания таблиц ознакомьтесь с содержимым файлов в директории 'lib-doc/Database' или 'lib-view/sql'')
3) для первого запуска приложения локальная БД может не содержать данных, однако для дальнейшей работы заполните таблицы БД, используя SQL-запросы.

	КАК ДЕЛАТЬ SQL-запросы:
	3.1) откройте query tool
	3.2) введите запрос Insert Into (название таблицы, атрибуты таблицы), value (данные)
	3.3) нажмите Execute

		Если запрос был написан верно, то введенные данные будут добавлены в таблицу, а вы увидите подобное сообщение:
		'Successfully run. Total query runtime: 246 msec. 3 rows affected'

	3.4) на настоящем этапе вводимые данные могут быть любыми, если они удовлетворяют требованиям к типам данных атрибутов таблиц. Файл с данными для заполненеия таблиц должен появиться в ближайшем будущем
	Простой туториал по SQL (https://metanit.com/sql/sqlserver/)
РАЗВЕРТЫВАНИЕ LIB-VIEW
1) в командной строке выполните команду git clone https://github.com/stakap/lib-view.git
2) найдите в склонированном репозитории файл 'build.sbt'
3) скачайте и установите язык Scala той версии, которая указана в строке 'scalaVersion :=' ( https://www.scala-lang.org )
4) найдите и откройте файл 'application.conf' в репозитории 'lib-view'
5) найдите в файле строку 'db = { url = "jdbc:postgresql://localhost:5432/alefowl", login = "postgres", password = "postgres" }' и замените имеющиеся данные БД на данные от Вашей локальной БД (см. раздел 'СОЗДАНИЕ ЛОКАЛЬНОЙ БД')
6) в терминале IDEA или в командной строке запустите lib-view, выполнив команду sbt run (для выполнения в терминале IDEA необходимо сначала открыть проект в IDEA)

	Если Вы все сделали верно, увидите нечто похожее:
	[pool-1-thread-1] INFO  c.z.h.HikariDataSource - HikariPool-1 - Starting...
	[pool-1-thread-1] INFO  c.z.h.HikariDataSource - HikariPool-1 - Start completed.
	[io-compute-11] INFO  o.h.e.s.EmberServerBuilderCompanionPlatform - Ember-Server service bound to address: [::]:8080

8) перейдите на страницу проекта ( http://localhost:80 )

	Вместо порта 80 Вы можете задать другой порт. Для этого:
	8.1) создайте файл 'local.conf' в той же директории, где находится файл 'application.conf' (можно сделать в IDEA)
	8.2) скопируйте содержимое файла 'application.conf' в файл 'local.conf'
	8.3) измените порт в файле 'local.conf' в строке 'port ='
	8.4) при переходе на страницу сайта измените номер порта на указанный в конфигурации в файле 'local.conf' ( http://localhost:'порт' )

Когда будете готовы включиться в работу, а также по любым вопросам, обращайтесь к наставнику или Product owner.
Удачи!