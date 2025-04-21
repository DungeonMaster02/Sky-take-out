# Sky Takeout - Learning Project

## 1. Introduction

This is a learning project called **Sky Takeout**, designed to help you practice the full development workflow of an enterprise-level takeout ordering platform using modern Java backend technologies and frontend frameworks.

## 2. Tech Stack

- **Frontend**: Vue, Element UI  
- **Backend**: Spring Boot, MyBatis Plus  
- **Middleware**: Nginx, Redis  
- **Database**: MySQL  

## 3. Getting Started

### 3.1 Frontend Setup

1. Run `nginx.exe` located in the `nginx-1.20.2` folder to launch the Nginx service.  
2. Open your browser and visit [http://localhost:9090](http://localhost:9090) to access the frontend interface.

### 3.2 Database

The database schema and initial data are provided in the SQL file:
/database/sky.sql

To set up the database:

Launch MySQL Workbench and connect to your local MySQL instance (e.g., localhost:3306 with user root).

Click "Server" > "Data Import"

Select Import from Self-Contained File, then choose:

sky.sql

(Under Default Target Schema, select or create a schema named sky_take_out.)

Click Start Import to load the schema and data.

#### ⚠️ Admin Login Reminder

The default admin password stored in the database is **MD5-hashed**.

- **Stored in DB**: `e10adc3949ba59abbe56e057f20f883e`
- **Actual password to input**: `123456`

✅ No need to hash it manually — the backend encrypts it automatically when you log in.

### 3.3 Backend Structure

The backend consists of a multi-module Maven project. Below is the structure and purpose of each module:

#### (1) `sky-take-out` (Parent Project)

Acts as the Maven **parent project**, responsible for **centralized dependency version management** and **aggregation of all sub-modules**.  
It contains the shared `pom.xml` configurations used by the entire project.

#### (2) `sky-common` (Common Module)

A shared module that contains **reusable components**, such as:

- Utility classes  
- Constants  
- Custom exceptions  

This module is used across other sub-modules to promote code reuse and consistency.

#### (3) `sky-pojo` (POJO Module)

This module contains **Java entity classes**, including:

- **POJOs** (Plain Old Java Objects)  
- **DTOs** (Data Transfer Objects)  
- **VOs** (View Objects)  

It defines the data models used throughout the application for database mapping, API responses, and inter-layer communication.

**Sub-packages include:**

- `entity/`: Contains basic entity classes that map to database tables.  
- `dto/`: Defines data transfer objects used to receive or send data between layers.  
- `vo/`: Holds view objects used to shape data sent to the frontend.  
- `pojo/`: Contains simple plain Java objects used across different layers, including the three types above.

#### (4) `sky-server` (Backend Service Module)

This is the **main backend module** of the project. It contains the core business logic following standard Spring Boot architecture, including:

- Configuration files (e.g., `application.yml`)  
- Controllers (for handling HTTP requests)  
- Services (business logic layer)  
- Mappers (MyBatis Plus for database access)

#### ⚠️ Change the password in application-dev.yml to your SQL password. If it is a numeric password, you need to use " "


Compile sky-take-out and Run sky-server\src\main\java\com\sky\SkyApplication.java, switch on the backend