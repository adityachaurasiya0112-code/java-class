<div align="center">

# ☕ Java Programming Lab

### A hands-on collection of every major Java technology — from Swing GUIs to distributed computing and full-stack Spring Boot.

<br/>

![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Maven](https://img.shields.io/badge/Apache-Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.4.5-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Jakarta](https://img.shields.io/badge/Jakarta-Servlet_6.1-00758F?style=for-the-badge&logo=servlet&logoColor=white)

![Experiments](https://img.shields.io/badge/Experiments-07-blue?style=flat-square)
![Projects](https://img.shields.io/badge/Projects-01-success?style=flat-square)
![Education](https://img.shields.io/badge/Purpose-Educational-lightgrey?style=flat-square)
![Made with ❤](https://img.shields.io/badge/Made%20with-❤-ff69b4?style=flat-square)

<br/>

<sub><b>Aditya Chaurasiya</b> · Roll No. <b>24EGJCS011</b> · B.Tech (CSE)</sub>
<br/>
<sub><a href="https://github.com/adityachaurasiya0112-code/java-class">github.com/adityachaurasiya0112-code/java-class</a></sub>

</div>

---

## 📑 Table of Contents

- [About](#-about)
- [Student Details](#-student-details)
- [Tech Stack](#-tech-stack)
- [Experiments at a Glance](#-experiments-at-a-glance)
- [Detailed Walkthrough](#-detailed-walkthrough)
- [Capstone Project](#-capstone-project)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Key Takeaways](#-key-takeaways)
- [Roadmap](#-roadmap)
- [Author](#-author)
- [License](#-license)

---

## 📖 About

This repository is the complete record of my **Java Programming Lab** coursework. It is not a collection of toy snippets — each experiment is a working, self-contained project that applies a different corner of the Java ecosystem to a real problem.

The journey starts with a desktop GUI form and ends with a full-stack web application:

> **Core Java → Swing → JDBC → RMI → Networking → Servlets → JSP → Spring Boot**

The goal is simple: understand *why* Java is still used everywhere — write once, run anywhere — and prove it by building things that actually run.

---

## 🎓 Student Details

<table>
<tr><td>

| Field | Details |
| :--- | :--- |
| **Name** | **Aditya Chaurasiya** |
| **Roll Number** | **24EGJCS011** |
| **Course** | B.Tech |
| **Branch** | Computer Science and Engineering |
| **Subject** | Java Programming Lab |

</td><td>

| Connect | Link |
| :--- | :--- |
| **GitHub** | [@adityachaurasiya0112-code](https://github.com/adityachaurasiya0112-code) |
| **Repository** | [java-class](https://github.com/adityachaurasiya0112-code/java-class) |
| **Language** | Java 17 |
| **Build Tool** | Apache Maven |

</td></tr>
</table>

---

## 🛠 Tech Stack

<table>
<tr>
<td width="50%">

**Core & Desktop**
- Java 17 (OOP, exceptions, collections)
- Java Swing — GUI forms, event handling
- GridBagLayout & custom theming
- `java.io` · `java.util` · `java.text`

**Data & Persistence**
- JDBC with MySQL Connector/J 9.5.0
- Prepared statements & SQL DDL/DML
- H2 in-memory database (JPA)

</td>
<td width="50%">

**Distributed & Networking**
- Java RMI — remote interfaces & stubs
- TCP sockets (`ServerSocket`, `Socket`)
- Multithreading — thread-per-client

**Web & Enterprise**
- Jakarta Servlet 6.1.0 (HTTP handling)
- JSP — dynamic view rendering
- Filters, Listeners, Sessions
- Spring Boot 3.4.5 — Web, JPA, Thymeleaf

</td>
</tr>
</table>

---

## 📊 Experiments at a Glance

| # | Experiment | Core Technology | Type |
|:-:|:---|:---|:---|
| 01 | [Registration Form](#experiment-01--student-registration-form) | Swing + JDBC + MySQL | Desktop GUI |
| 02 | [Database Operations](#experiment-02--database-operations-with-jdbc) | JDBC | Console |
| 03 | [MVC Calculator](#experiment-03--mvc-pattern-calculator) | Swing + MVC | Desktop GUI |
| 04 | [Distributed Calculator](#experiment-04--distributed-calculator-with-rmi) | Java RMI | Distributed |
| 05 | [TCP Client-Server](#experiment-05--multithreaded-tcp-client--server) | Sockets + Threads | Networking |
| 06 | [HTTP Request Handling](#experiment-06--http-request-handling-with-servlets) | Jakarta Servlets | Web |
| 07 | [Student Portal](#experiment-07--web-based-student-portal) | JSP + Servlets | Web (MVC) |
| 🛒 | [E-Commerce Platform](#-capstone-project) | Spring Boot + JPA | Full Stack |

---

## 🔍 Detailed Walkthrough

### Experiment 01 · Student Registration Form

A polished desktop registration form that writes directly into a MySQL database.

**What it does**
- Collects name, roll number, branch, semester, gender, mobile, email, date of birth and address
- Branch and semester are dropdowns — no free-text typos
- Validates input before saving (roll number must be numeric, email format, terms checkbox required)
- `Preview` shows a summary, `Reset` clears the form, records insert into the `students` table

**Key implementation points**
- `GridBagLayout` with `JComboBox`, `JRadioButton`, `JCheckBox`, `JTextArea`
- Connection via `jdbc:mysql://localhost:3306/student` using a `PreparedStatement` (SQL-injection safe)
- Bundled schema: [`registration portalstudent_database.sql`](<Experiment-01-Registration-Form-Using-Java/registration portalstudent_database.sql>)

```bash
# 1. Create the schema first
mysql -u root -p < "Experiment-01-Registration-Form-Using-Java/registration portalstudent_database.sql"

# 2. Compile and run (MySQL driver must be on the classpath)
cd Experiment-01-Registration-Form-Using-Java
javac -cp ".:mysql-connector-j-9.5.0.jar" "registration portalStudentRegistrationSystem.java"
java  -cp ".:mysql-connector-j-9.5.0.jar" StudentRegistrationSystem

# On Windows, replace ":" with ";" in the classpath above
```

---

### Experiment 02 · Database Operations with JDBC

A console CRUD application that manages its own database lifecycle.

**What it does**
- Auto-creates the `college` database and `students` table on first run
- Interactive menu for inserting and listing student records
- Demonstrates the full JDBC flow: load driver → connect → execute → close

**Key implementation points**
- `Class.forName("com.mysql.cj.jdbc.Driver")` explicit driver loading
- Separate connections for server-level (`CREATE DATABASE`) and database-level (`CREATE TABLE`) operations
- `try-with-resources` everywhere, so `Connection`, `Statement` and `ResultSet` always close

```bash
cd Experiment-02-Database-Operations-With-JDBC
mvn compile exec:java -Dexec.mainClass=Jdbcapp
```

> Default credentials are `root` / `1234` — change them in the source to match your local MySQL setup.

---

### Experiment 03 · MVC Pattern Calculator

The textbook demonstration of the **Model-View-Controller** design pattern, built with Swing.

```
CalculatorView  ──user action──▶  CalculatorController  ──▶  CalculatorModel
      ▲                                    │                       │
      └───────────── repaint ◀─────────────┴─────── result ────────┘
```

| Layer | Class | Responsibility |
|:---|:---|:---|
| **Model** | `model.java` | Pure arithmetic — add, subtract, multiply, divide. No UI knowledge. |
| **View** | `view.java` | JFrame with text fields and operation buttons. Knows nothing about logic. |
| **Controller** | `controller.java` | Implements `ActionListener`, reads input, calls the model, updates the view. |
| **Entry** | `main.java` | Wires the three components together. |

The point of the exercise: each layer can be changed independently — swap Swing for a web UI and the model stays untouched.

```bash
cd Experiment-03-MVC-Pattern-Based-Calculator
javac main.java model.java view.java controller.java
java main
```

---

### Experiment 04 · Distributed Calculator with RMI

Java Remote Method Invocation lets one JVM call methods on an object living in another JVM — across machines, as if it were local.

**The three pieces**

| File | Role |
|:---|:---|
| `calculator.java` | The `Remote` interface — the contract both sides agree on |
| `server.java` | Binds the implementation to the RMI registry |
| `client.java` | Looks up the remote object and invokes methods on it |
| `Sample.java` | Simple usage demonstration |

**Key implementation points**
- `calculator extends Remote`, every method declares `throws RemoteException`
- Only primitives (`int`) cross the network — serializable objects work too
- The registry decouples client from server: neither needs the other's address

```bash
cd Experiment-04-Distributed-Calculator-Using-RMI
javac calculator.java server.java client.java Sample.java

# Terminal 1 — start the registry and server
rmiregistry &
java server

# Terminal 2 — connect and call remote methods
java client
```

---

### Experiment 05 · Multithreaded TCP Client-Server

A chat-style echo server that never blocks on a single client.

**How it works**
1. `Server` opens a `ServerSocket` on **port 5000**
2. Every time a client connects, it spawns a fresh `Thread` and immediately loops back to `accept()`
3. Each connection gets its own `BufferedReader` / `PrintWriter` pair
4. The server echoes back `Server received: <message>` until the client types `exit`

**Why threads matter** — a single-threaded server locks up the moment one client goes silent. Thread-per-client keeps every session independent.

```bash
cd Experiment-05-Multithreaded-TCP-Client-Server
javac Server.java Client.java

# Terminal 1
java Server

# Terminal 2 (and 3, 4, ... — run as many as you like)
java Client
```

---

### Experiment 06 · HTTP Request Handling with Servlets

A servlet-based web application covering the full Jakarta Servlet lifecycle.

**The servlets**

| Servlet | Mapping | Purpose |
|:---|:---|:---|
| `HelloServlet` | `/hello` | Minimal GET request → HTML response |
| `HomeServlet` | `/home` | Landing page routing |
| `LoginServlet` | `/login` | Session creation on authentication |
| `LogoutServlet` | `/logout` | Session invalidation |
| `StudentServlet` | `/student` | POST form handling with `request.getParameter()` |

**The cross-cutting layer**
- `AuthFilter` — rejects unauthenticated requests before they reach a servlet
- `LoggingFilter` — records every request that passes through
- `SessionListener` / `AppListener` — react to session and application lifecycle events

```bash
cd Experiment-06-HTTP-Request-Handling-With-Servlets
mvn clean package
# Deploys as target/servlet.war on any Jakarta Servlet 6.x container
```

---

### Experiment 07 · Web-Based Student Portal

Everything from Experiment 06, upgraded to a proper **MVC web application** by adding JSP as the view layer.

```
Browser ──▶ Servlet (Controller) ──▶ Logic ──▶ JSP (View) ──▶ HTML response
```

**What's new**
- `student.jsp` and `result.jsp` separate presentation from request handling
- `request.setAttribute()` passes data from controller to view
- Auth filter and session listener carry over for protected routes

```bash
cd Experiment-07-Web-Based-Student-Portal/jsp-servlet-student-main
mvn clean package
mvn org.apache.tomcat.maven:tomcat7-maven-plugin:run
```

---

## 🛒 Capstone Project

### E-Commerce Platform — *Nyxora Shop*

The final project ties every concept together into a working online store built on Spring Boot.

| Layer | Technology |
|:---|:---|
| **Web MVC** | `spring-boot-starter-web` + `StoreController` |
| **View** | Thymeleaf templates — `index.html`, `cart.html`, `orders.html` |
| **Persistence** | Spring Data JPA + `ProductRepository` |
| **Database** | H2 in-memory (zero-config, auto-seeded) |
| **Domain** | `Product` entity — name, category, description, price, image, stock |

**Why it matters** — this is where RMI, sockets, servlets and JDBC stop being separate experiments and become one application. JPA replaces raw JDBC, Thymeleaf replaces hand-written HTML, and Spring replaces manual lifecycle management.

```bash
cd Java-Project-E-Commerce-Platform
mvn spring-boot:run
# Visit http://localhost:8080
```

---

## 📁 Project Structure

```
java-class/
│
├── Experiment-01-Registration-Form-Using-Java/
│   ├── registration portalStudentRegistrationSystem.java
│   └── registration portalstudent_database.sql
│
├── Experiment-02-Database-Operations-With-JDBC/
│   ├── jdbcApp.java
│   └── pom.xml
│
├── Experiment-03-MVC-Pattern-Based-Calculator/
│   ├── model.java
│   ├── view.java
│   ├── controller.java
│   └── main.java
│
├── Experiment-04-Distributed-Calculator-Using-RMI/
│   ├── calculator.java          # Remote interface
│   ├── server.java
│   ├── client.java
│   └── Sample.java
│
├── Experiment-05-Multithreaded-TCP-Client-Server/
│   ├── Server.java
│   └── Client.java
│
├── Experiment-06-HTTP-Request-Handling-With-Servlets/
│   ├── pom.xml
│   └── src/main/
│       ├── java/com/servlet/    # 5 servlets, 2 filters, 2 listeners
│       └── webapp/              # hello.html, index.html, student.html
│
├── Experiment-07-Web-Based-Student-Portal/
│   └── jsp-servlet-student-main/
│       ├── pom.xml
│       └── src/main/
│           ├── java/com/servlet/
│           └── webapp/          # student.jsp, result.jsp
│
├── Java-Project-E-Commerce-Platform/
│   ├── pom.xml
│   └── src/main/
│       ├── java/com/nyxora/shop/
│       │   ├── ShopApplication.java
│       │   ├── StoreData.java
│       │   ├── model/Product.java
│       │   ├── repository/ProductRepository.java
│       │   └── controller/StoreController.java
│       └── resources/
│           ├── application.properties
│           └── templates/       # index.html, cart.html, orders.html
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

| Tool | Version | Needed For |
|:---|:---|:---|
| **JDK** | 17+ | Everything |
| **Maven** | 3.8+ | Experiments 02, 06, 07, Capstone |
| **MySQL** | 8.0+ | Experiments 01, 02 |
| **Servlet Container** | Tomcat 10+ (Jakarta) | Experiments 06, 07 |
| **IDE** | IntelliJ IDEA / Eclipse / VS Code | Comfort |

### Clone

```bash
git clone https://github.com/adityachaurasiya0112-code/java-class.git
cd java-class
```

### Run

Every experiment is self-contained — `cd` into it and follow the command shown in its section above.

**Quick sanity check** — for any plain Java file with no dependencies:

```bash
javac <File>.java
java <ClassName>
```

> ⚠️ Experiments 01 and 02 expect MySQL on `localhost:3306` with user `root` / password `1234`. Update the constants at the top of each source file if your setup differs.

---

## 💡 Key Takeaways

| Concept | Where It Was Learned |
|:---|:---|
| Object-oriented design | All experiments |
| Event-driven programming | Experiment 01, 03 — `ActionListener` |
| Layered architecture (MVC) | Experiment 03, 07 |
| Database connectivity & transactions | Experiment 01, 02 |
| Network-transparent method calls | Experiment 04 — RMI |
| Concurrency & thread management | Experiment 05 |
| Request/response lifecycle | Experiment 06 |
| Dependency injection & ORM | Capstone — Spring Boot |

---

## 🗺 Roadmap

- [ ] Add per-experiment screenshots and sample output
- [ ] Write a standalone `README.md` inside each experiment folder
- [ ] Add JUnit tests for the calculator and JDBC layers
- [ ] Replace hardcoded DB credentials with environment variables
- [ ] Containerise the capstone project with Docker
- [ ] Add a GitHub Actions workflow to compile every experiment on push

---

## ✍️ Author

<div align="center">

**Aditya Chaurasiya**

`Roll No. 24EGJCS011` · `B.Tech — Computer Science and Engineering`

[![GitHub](https://img.shields.io/badge/GitHub-adityachaurasiya0112-code-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/adityachaurasiya0112-code)
[![Repository](https://img.shields.io/badge/Repository-java--class-blue?style=flat-square)](https://github.com/adityachaurasiya0112-code/java-class)

</div>

---

## 📄 License

This repository is intended for **educational and academic purposes**. Reuse and redistribution should follow the permissions and licenses of the original dependencies and libraries used.

---

<div align="center">

### ☕ *Learn. Implement. Improve.*

<sub>© 2026 Aditya Chaurasiya · Java Programming Lab · All rights reserved.</sub>

</div>
