Kaiburr Task 1 - Java Backend and REST API
This project is a Spring Boot and MongoDB-based REST API that manages and executes user-defined Task objects. Each Task represents a shell command that can be created, listed, searched, deleted, and executed. The project fulfills Task 1 of the Kaiburr Assessment.
Project Overview
The goal of this project is to implement a Java-based application that provides a REST API for creating, deleting, searching, and running Task objects. Each task represents a shell command that can be executed in a Kubernetes pod.
Technologies Used
1. Java 22 with Spring Boot 3
2. MongoDB 6 (using Docker)
3. Maven 3.9 or higher
4. Postman or cURL for API testing
5. Windows-safe command execution support
Prerequisites
1. Java Development Kit (JDK) 17 or higher
2. Apache Maven installed and configured in the system PATH
3. Docker Desktop running on the system
4. Postman installed for API testing
Setup Instructions
Step 1: Start MongoDB
Command: docker run -d --name mongo -p 27017:27017 mongo:6

Step 2: Build and Run the Spring Boot Application
Command:
mvn clean package
mvn spring-boot:run

The application will start at http://localhost:8080
REST API Endpoints
1. GET /api/tasks - Retrieve all tasks or a single task by ID
2. PUT /api/tasks - Create or update a task
3. GET /api/tasks/find?name={name} - Search tasks by name
4. PUT /api/tasks/{id}/execution - Execute the command of a task
5. DELETE /api/tasks/{id} - Delete a task by its ID
Example API Requests
Create a Task:
curl -X PUT http://localhost:8080/api/tasks -H "Content-Type: application/json" -d "{\"name\":\"Print Hello\",\"owner\":\"Ananya\",\"command\":\"echo Hello\"}"

Get All Tasks:
curl http://localhost:8080/api/tasks

Execute a Task:
curl -X PUT http://localhost:8080/api/tasks/<task_id>/execution

Search Task by Name:
curl "http://localhost:8080/api/tasks/find?name=print"

Delete Task:
curl -X DELETE http://localhost:8080/api/tasks/<task_id>
Postman Test Results
All Postman request and response screenshots are available in the outputs folder.
Screenshots include:
1. MongoDB container running
2. Application start confirmation
3. Create Task request and response
4. List Tasks request and response
5. Execute Task output
6. Find Task by name
7. Delete Task confirmation
Security Features
The CommandValidator class ensures that unsafe commands (such as rm -rf, wget, or system file access) are blocked. The ShellRunner class automatically switches between cmd.exe and /bin/sh depending on the operating system.
Author
Prepared by: Ananya Tayi
Course: B.Tech in Computer Science and Engineering
Institution: Amrita School of Engineering, Bengaluru
GitHub: https://github.com/your-GitHub-username
