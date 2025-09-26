
Voici une exemple de structure de projet qui pourrait être utilisé pour chacun des labs / projets

Référencé du [Maven Standard Directory Layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)

```text
(project-name)/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── mycompany (myproject)/
│   │   │           └── myapp/
│   │   │               ├── config/
│   │   │               │   └── AppConfig.java
│   │   │               ├── controller/
│   │   │               │   └── BookController.java
│   │   │               ├── model/
│   │   │               │   └── Book.java
│   │   │               └── service/
│   │   │                   └── BookService.java
│   │   ├── resources/
│   │   │   ├── application.properties
│   │   │   └── log4j2.xml
│   │   ├── webapp/
│   │   │   ├── WEB-INF/
│   │   │   │   └── web.xml
│   │   │   │   └── views/
│   │   │   │       ├── home.jsp
│   │   │   │       └── books.jsp
│   │   │   └── index.jsp
│   │   └── filters/
│   │       └── dev.properties

---- misc

│   ├── test/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── mycompany (myproject)/
│   │   │           └── myapp/
│   │   │               ├── service/
│   │   │               │   └── BookServiceTest.java
│   │   │               └── controller/
│   │   │                   └── BookControllerTest.java
│   │   └── resources/
│   │       ├── test-application.properties
│   │       └── test-data.sql
│   └── it/
│       └── com/
│           └── mycompany (myproject)/
│               └── myapp/
│                   └── integration/
│                       └── LibraryWebAppIT.java
├── LICENSE.txt
├── NOTICE.txt
└── README.txt

```