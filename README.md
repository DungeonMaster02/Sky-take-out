1.Introduction
This is a learning project called "Sky Takeout". It aims to practice the full development workflow of an enterprise-level takeout ordering platform. 

2.Tech Stack
- Frontend: Vue, Element UI
- Backend: Spring Boot, MyBatis Plus
- Middleware: Nginx, Redis
- Database: MySQL

3.Getting Started
1.Run `nginx.exe` located in the `nginx-1.20.2` folder to launch the Nginx service. Then open your browser and visit [http://localhost:9090](http://localhost:9090) to access the frontend interface.
2.sky-take-out is the original backend project, including:
(1)sky-take-out: 
  Acts as the Maven **parent project**, responsible for **centralizing dependency version management** and **aggregating all sub-modules**. It contains the shared `pom.xml` configurations used by the entire project.

(2)sky-common: children
 A shared module that contains **reusable components**, such as **utility classes**, **constants**, and **custom exception definitions**. This module is used across other sub-modules to promote code reuse and consistency.


(3)sku-pojo:
 This module contains **Java entity classes**, including **POJOs**, **VOs (View Objects)**, and **DTOs (Data Transfer Objects)**. It defines the data models used throughout the application for database mapping, API responses, and inter-layer communication.

  - **Entity/**: Contains basic entity classes that map to database tables.
  - **DTO/**: Defines Data Transfer Objects used to receive or send data between layers.
  - **VO/**: Holds View Objects used to shape data sent to the frontend.
  - **POJO/**: Contains simple plain Java objects used across different layers, including the three modules above.

 (4)sky-server:
 This is the **main backend module** of the project. It contains the core business logic and typical Spring Boot structure, including Configuration files, Controller, Service, Mapper.etc