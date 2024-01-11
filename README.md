В рамках выполнения заданий для лабораторных работ, была выбрана предметная область фармакология, а именно Аптеки и Лекарственные препараты.
Для хранения данных была реализована база данных (PostgreSQL), хранящая таблицу Аптеки (Pharmacy) и таблицу Лекарства (Drug), при этом связь таблицы аптеки к таблице лекарств реализована как многие ко многим.
Для реализации программного модуля на языке java, была выбрана интегрированная среда разработки программного обеспечения для многих языков программирования, в частности Java, разработанная компанией JetBrains — IntelliJ IDEA (и отдельная её версия IntelliJ IDEA Ultimate, которая предоставляет все необходимое «из коробки», включая встроенные инструменты разработчика, такие как инструменты баз данных и профилировщики, веб-платформы и корпоративные платформы, удаленную разработку и многое другое).
В качестве системы контроля версий был использован GitHub — крупнейший веб-сервис для хостинга IT-проектов и их совместной разработки.


# ЛР №1
Для работы со спецификациями Java EE (Jakarta EE — набор спецификаций и соответствующей документации для языка Java, был подгружен автоматически средствами среды разработки IntelliJ IDEA), был выбран сервер приложений с открытым исходным кодом — GlassFish.
Для обозначения с сущностей БД была использована аннотация (@Entity) и (@Table).
Сущности и связи имеют общих предков (BaseLinc и BaseEntity, соответственно)
Для работы с сущностями были были написаны сервисы, один работает с таблицей аптек и лекарств, другой только с лекарствами.
Для организации обмена данными с клиентской и серверной частью приложения были написаны сервлеты, они позволяют организовать доступ к (JSP)страницам всех аптек, всех лекарств, страницам создания лекарств и аптек, странице просмотра сведений о конкретной аптеке (адрес, название, телефон и т.д + данные о лекарственных средствах, доступных для покупки в этой аптеке).
# ЛР №2
Для выполнения задания по реализации веб-приложения, был создан проект, включающий Spring Boot (расширение, которое упрощает и ускоряет работу со Spring). Боюсь с чистым спрингом не сдали бы и к концу магистратуры лабы.
![image](https://github.com/Kusakina/README/assets/74459357/5699b2ff-0fd1-4342-847b-a55861fb4cee)

Логика работы программы и состав сущностей аналогичен ЛР№1.
Были применены аннотации @GetMapping (составная версия @RequestMapping аннотации, которая действует как ярлык для файлов @RequestMapping(method = RequestMethod.GET)) и 
@PostMapping (составная версия @RequestMapping аннотации, которая действует как ярлык для файлов @RequestMapping(method = RequestMethod.POST).
Методы аннотированные таким образом, обрабатывают гет и пост запросы по соответствующему значению URL.

Были реализованы методы производных запросов, Spring умеет в различное автоматическое генерирование базовых запросов типа (findBy, findAll).
Сервлеты заменены сервисами.

# ЛР №3

В рамках лр были реализованы следующие API:
__GET:__
GET /api/v2/pharmacy/all
GET /api/v2/pharmacy/{id}
GET /api/v2/drug/all
GET /api/v2/drug/{id}

__POST__
POST /api/v2/pharmacy/create
POST /api/v2/pharmacy/delete/{id}
POST /api/v2/drug/create
POST /api/v2/drug/delete/{id}

Для выполнения задания по созданию RESTful приложения была выбрана технология Spring REST, потому то:
 ***
 Spring REST является частью Spring Framework и тесно интегрирован с другими компонентами Spring, так как 2 лр была написана на Спринге (а писать её было значительно легче, чем 1), было решено выбрать именно данную реализацию.
  ***
  Различных туториалов по вопросам применения, интеграции и исправления ошибок, связанных с Spring REST намного больше, чем для JAX-RS, отчасти потому, что использование JavaEE сильно ограничено, разработчики отдают предпочтения Spring, так как он проще (хороший программист - ленивый программист)
  ***
Spring REST обладает гибкой системой конфигурации с использованием аннотаций, что упрощает процесс разработки и поддержки кода. Он также предоставляет множество готовых решений и соглашений для упрощения задач, таких как обработка запросов, валидация данных и другие.
 ***
Еще мог закончиться пробный период IntelliJ IDEA Ultimate, а на Community JavaEE не подключается.
# ЛР №4
 В рамках выполнения задания созданы классы:
***
 Producer
***
 ConsumerMail
 ***
 ConsumerLog
 ***
 Producer — объект, создающий сообщения (LogEvent на создание и удаление), которые формируют несколько очередей (для ConsumerMail и ConsumerLog соответственно).
 ConsumerLog заполняет таблицу логов (записями об изменениях), а ConsumerMail заполняет табличку адресами и условиями отправки сообщений (address, condition).
