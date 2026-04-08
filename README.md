Exp 11
Got you. Let’s reset and do this clean from absolute beginning → till tests run (green). No confusion, no missing steps.
________________________________________
🚀 STEP 0: What you need (already mostly done)
•	VS Code
•	Java installed (JDK)
•	Extension Pack for Java
👉 If VS Code already running Java → you’re good
________________________________________
⚙️ STEP 1: Create Proper Java Project
1.	Open VS Code
2.	Press:
Ctrl + Shift + P
3.	Type:
Java: Create Java Project
4.	Select:
No build tools
5.	Choose location (Documents)
6.	Name:
JUnitDemo
________________________________________
📁 STEP 2: Project structure (IMPORTANT)
You should see:
JUnitDemo/
 ├── src/
 ├── lib/
 ├── bin/
If this exists → perfect ✅
________________________________________
🧾 STEP 3: Create Main Java File
Right-click src → New File → Calculator.java
Paste:
public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public int subtract(int a, int b) {
        return a - b;
    }

    public int multiply(int a, int b) {
        return a * b;
    }

    public int divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("Cannot divide by zero");
        }
        return a / b;
    }
}
________________________________________
📦 STEP 4: Add JUnit (VERY IMPORTANT)
🔹 Download JUnit
Download this file:
👉 https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/1.10.0/junit-platform-console-standalone-1.10.0.jar
________________________________________
🔹 Add to project
1.	Put that .jar file inside:
lib/
2.	Go back to VS Code
3.	Press:
Ctrl + Shift + P
4.	Type:
Java: Clean Java Language Server Workspace
5.	Reload
________________________________________
🧪 STEP 5: Create Test File
Right-click src → New File → CalculatorTest.java
Paste this (IMPORTANT: THIS IS FINAL CORRECT CODE):
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    Calculator calc = new Calculator();

    @Test
    void testAddition() {
        assertEquals(10, calc.add(7, 3));
    }

    @Test
    void testSubtraction() {
        assertEquals(4, calc.subtract(9, 5));
    }

    @Test
    void testMultiplication() {
        assertEquals(20, calc.multiply(4, 5));
    }

    @Test
    void testDivision() {
        assertEquals(5, calc.divide(10, 2));
    }

    @Test
    void testDivideByZero() {
        assertThrows(ArithmeticException.class, () -> {
            calc.divide(10, 0);
        });
    }
}
________________________________________
⚠️ STEP 6: Check errors
If you see:
package org.junit.jupiter.api does not exist
👉 Means JUnit not added properly
→ redo Step 4
________________________________________
▶️ STEP 7: Run Tests
Now you will see:
Option 1:
•	Green ▶ icon near each method
Option 2:
•	Above method:
Run Test | Debug Test
________________________________________
✅ Click ▶
________________________________________
🎯 EXPECTED OUTPUT
•	All tests run
•	Green checkmarks ✅
•	No errors
________________________________________
🧠 COMMON MISTAKE (YOU DID THIS EARLIER)
❌ WRONG:
calc.add(a: 7, b: 3);
✔ CORRECT:
calc.add(7, 3);
________________________________________
💥 FINAL FLOW (REMEMBER FOR EXAM)
1.	Create Java project
2.	Write main class
3.	Add JUnit jar
4.	Write test class
5.	Run tests
6.	Verify output
________________________________________
🔥 If anything fails
Send screenshot → I’ll fix it fast
________________________________________
If you want next:
•	Viva questions
•	Or explanation of each JUnit function
You’re basically done with the experiment now.

Exp 12
Experiment 12: Running JUnit Tests with Maven
🎯 Aim
To configure a Maven project and run JUnit test cases using Maven build tool.
________________________________________
⚙️ STEP 1: Create Maven Project
Open terminal and go to desired location:
cd Documents
Run:
mvn archetype:generate
________________________________________
Enter details:
Choose archetype → select maven-archetype-quickstart  
GroupId → com.example  
ArtifactId → junit-demo  
Version → (press Enter)  
Package → com.example  
Confirm → y  
________________________________________
✅ Project created at:
C:\Users\Midhunraj N P\Documents\junit-demo
________________________________________
📁 STEP 2: Move into Project
cd junit-demo
________________________________________
📂 STEP 3: Project Structure
junit-demo/
 ├── pom.xml
 └── src/
     ├── main/java/com/example/
     └── test/java/com/example/
________________________________________
🧾 STEP 4: Write Main Program
📄 File:
src/main/java/com/example/Calculator.java
Code:
package com.example;

public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public int subtract(int a, int b) {
        return a - b;
    }

    public int multiply(int a, int b) {
        return a * b;
    }

    public int divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("Cannot divide by zero");
        }
        return a / b;
    }
}
________________________________________
🧪 STEP 5: Write JUnit Test
📄 File:
src/test/java/com/example/CalculatorTest.java
Code:
package com.example;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    Calculator calc = new Calculator();

    @Test
    void testAddition() {
        assertEquals(10, calc.add(7, 3));
    }

    @Test
    void testSubtraction() {
        assertEquals(4, calc.subtract(9, 5));
    }

    @Test
    void testMultiplication() {
        assertEquals(20, calc.multiply(4, 5));
    }

    @Test
    void testDivision() {
        assertEquals(5, calc.divide(10, 2));
    }

    @Test
    void testDivideByZero() {
        assertThrows(ArithmeticException.class, () -> {
            calc.divide(10, 0);
        });
    }
}
________________________________________
📦 STEP 6: Configure pom.xml
📄 Replace entire pom.xml with:
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>junit-demo</artifactId>
    <version>1.0-SNAPSHOT</version>

    <name>junit-demo</name>

    <properties>
        <maven.compiler.release>17</maven.compiler.release>
    </properties>

    <!-- JUnit 5 Dependency -->
    <dependencies>
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <version>5.10.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <!-- Plugin to run tests -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.0.0</version>
            </plugin>
        </plugins>
    </build>

</project>
________________________________________
▶️ STEP 7: Run Tests
In terminal:
mvn clean test
________________________________________
✅ OUTPUT
Running com.example.CalculatorTest
Tests run: 5, Failures: 0, Errors: 0

BUILD SUCCESS

🧪 Experiment 13: Integrating JUnit with Jenkins
🎯 Aim
To integrate JUnit testing with Jenkins and execute automated test cases using Maven in a CI environment.
________________________________________
🧠 Overview Flow
Java Code → Maven → GitHub → Jenkins → Run Tests → Generate Report
________________________________________
⚙️ STEP 1: Create Maven Project
Open terminal:
mvn archetype:generate
Enter:
GroupId: com.example  
ArtifactId: junit-demo  
Package: com.example  
________________________________________
📁 STEP 2: Project Structure
junit-demo/
 ├── pom.xml
 └── src/
     ├── main/java/com/example/
     └── test/java/com/example/
________________________________________
🧾 STEP 3: Write Main Java Code
📄 Calculator.java
package com.example;

public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public int subtract(int a, int b) {
        return a - b;
    }

    public int multiply(int a, int b) {
        return a * b;
    }

    public int divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException();
        }
        return a / b;
    }
}
________________________________________
🧪 STEP 4: Write JUnit Test
📄 CalculatorTest.java
package com.example;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    Calculator calc = new Calculator();

    @Test
    void testAddition() {
        assertEquals(10, calc.add(7, 3));
    }

    @Test
    void testSubtraction() {
        assertEquals(4, calc.subtract(9, 5));
    }

    @Test
    void testMultiplication() {
        assertEquals(20, calc.multiply(4, 5));
    }

    @Test
    void testDivision() {
        assertEquals(5, calc.divide(10, 2));
    }

    @Test
    void testDivideByZero() {
        assertThrows(ArithmeticException.class, () -> {
            calc.divide(10, 0);
        });
    }
}
________________________________________
📦 STEP 5: Configure pom.xml
<dependencies>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>5.10.0</version>
        <scope>test</scope>
    </dependency>
</dependencies>

<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>3.0.0</version>
        </plugin>
    </plugins>
</build>
________________________________________
▶️ STEP 6: Run Locally (VERY IMPORTANT)
mvn clean test
✔ Output:
BUILD SUCCESS
________________________________________
🌐 STEP 7: Push Project to GitHub
Using GitHub
git init
git add .
git commit -m "JUnit project"
git branch -M main
git remote add origin https://github.com/your-username/junit-demo.git
git push -u origin main
________________________________________
🔧 STEP 8: Create Jenkins Job
Using Jenkins
1.	Click New Item 
2.	Enter name: JUnit-Jenkins-Demo 
3.	Select Freestyle Project 
4.	Click OK 
________________________________________
🔗 STEP 9: Configure GitHub in Jenkins
•	Source Code Management → Git 
•	Repository URL: 
https://github.com/your-username/junit-demo.git
•	Branch: 
*/main
________________________________________
⚙️ STEP 10: Configure Build
•	Add Build Step: 
Invoke top-level Maven targets
•	Goals: 
clean test
________________________________________
📊 STEP 11: Add Test Report
•	Post-build action: 
Publish JUnit test result report
•	Path: 
target/surefire-reports/*.xml
________________________________________
▶️ STEP 12: Run Build
Click:
Build Now
________________________________________
📊 STEP 13: View Output
✔ Console Output
Tests run: 5, Failures: 0
BUILD SUCCESS
________________________________________
✔ Test Report (IMPORTANT)
Build → Test Result
Shows:
•	Total tests 
•	Passed 
•	Failed 
________________________________________
📁 STEP 14: Report Location
Physical file:
target/surefire-reports/*.xml

🧪 Experiment 14: Test Coverage using JaCoCo
________________________________________
🎯 Aim
To generate and analyze code coverage reports using JaCoCo in a Maven-based project.
________________________________________
🧠 Overview Flow
Java Code → JUnit Tests → Maven → JaCoCo → Coverage Report
________________________________________
⚙️ STEP 1: Create Maven Project
Open terminal:
mvn archetype:generate
Enter:
GroupId: com.example  
ArtifactId: junit-demo1  
Package: com.example  
________________________________________
📁 STEP 2: Project Structure
junit-demo1/
 ├── pom.xml
 └── src/
     ├── main/java/com/example/
     └── test/java/com/example/
________________________________________
🧾 STEP 3: Write Main Java Code
📄 Calculator.java
package com.example;

public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public int subtract(int a, int b) {
        return a - b;
    }

    public int multiply(int a, int b) {
        return a * b;
    }

    public int divide(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException();
        }
        return a / b;
    }
}
________________________________________
🧪 STEP 4: Write JUnit Test
📄 CalculatorTest.java
package com.example;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    Calculator calc = new Calculator();

    @Test
    void testAddition() {
        assertEquals(10, calc.add(7, 3));
    }

    @Test
    void testSubtraction() {
        assertEquals(4, calc.subtract(9, 5));
    }

    @Test
    void testMultiplication() {
        assertEquals(20, calc.multiply(4, 5));
    }

    @Test
    void testDivision() {
        assertEquals(5, calc.divide(10, 2));
    }

    @Test
    void testDivideByZero() {
        assertThrows(ArithmeticException.class, () -> {
            calc.divide(10, 0);
        });
    }
}
________________________________________
📦 STEP 5: Modify pom.xml (IMPORTANT STEP)
❌ BEFORE (your original issues)
<version>com.example</version>   ❌ wrong
<dependencyManagement> ... </dependencyManagement> ❌ unnecessary
junit-jupiter-api + params ❌ incomplete setup
No JaCoCo plugin ❌
________________________________________
✅ AFTER (correct working pom.xml)
<dependencies>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>5.10.0</version>
        <scope>test</scope>
    </dependency>
</dependencies>
________________________________________
✅ Added JaCoCo Plugin
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.11</version>
    <executions>

        <execution>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
        </execution>

        <execution>
            <id>report</id>
            <phase>test</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>

    </executions>
</plugin>
________________________________________
🔥 EXACT CHANGES YOU MADE (WRITE THIS)
✔ 1. Fixed version
com.example → 1.0-SNAPSHOT
________________________________________
✔ 2. Removed
<dependencyManagement>
________________________________________
✔ 3. Simplified dependencies
junit-jupiter (single dependency)
________________________________________
✔ 4. Added JaCoCo plugin
👉 This is the main step of experiment
________________________________________
✔ 5. Added Surefire plugin (optional but good)
maven-surefire-plugin
________________________________________
▶️ STEP 6: Run Project
mvn clean test
✔ Output:
BUILD SUCCESS
________________________________________
📁 STEP 7: Locate Coverage Report
Go to:
target/site/jacoco/index.html
________________________________________
🌐 STEP 8: Open Report
Open index.html in browser
________________________________________
📊 STEP 9: Analyze Report
You will see:
•	Line coverage 
•	Branch coverage 
•	Method coverage 
________________________________________
Color meaning:
•	🟢 Green → Covered 
•	🔴 Red → Not covered 
•	🟡 Yellow → Partial 
________________________________________
🎯 Output
•	JaCoCo coverage report generated 
•	Code coverage percentage displayed 
•	Visual analysis of tested code 
________________________________________
📁 Report Files
target/site/jacoco/index.html
target/site/jacoco/jacoco.xml

Experiment 15: Introduction to Docker and Basic Commands
________________________________________
🎯 Aim
To install Docker and execute basic commands to run and manage containers.
________________________________________
🧠 Overview
Docker → Pull Image → Run Container → Manage Containers
________________________________________
⚙️ STEP 1: Install Docker
1.	Download Docker Desktop from:
https://www.docker.com/products/docker-desktop/
2.	Install and restart system if required 
3.	Open Docker Desktop 
________________________________________
✅ Verify Installation
Open terminal:
docker --version
✔ Expected Output:
Docker version XX.X.X
________________________________________
▶️ STEP 2: Start Docker
•	Open Docker Desktop 
•	Wait until: 
Docker is running
________________________________________
🐳 STEP 3: Run First Container
docker run hello-world
________________________________________
✅ Output:
Hello from Docker!
This message shows that your installation appears to be working correctly.
________________________________________
📥 STEP 4: Pull an Image
docker pull ubuntu
👉 This downloads Ubuntu image
________________________________________
▶️ STEP 5: Run Ubuntu Container
docker run -it ubuntu
👉 Output:
root@container-id:/#
________________________________________
🔹 Exit container
exit
________________________________________
📦 STEP 6: List Containers
🔹 Running containers
docker ps
________________________________________
🔹 All containers
docker ps -a
________________________________________
📁 STEP 7: List Images
docker images
________________________________________
▶️ STEP 8: Start and Stop Container
docker start <container_id>
docker stop <container_id>
________________________________________
❌ STEP 9: Remove Container
docker rm <container_id>
________________________________________
🗑 STEP 10: Remove Image
docker rmi <image_id>
________________________________________
🌐 STEP 11: Run Web Server (Nginx)
docker run -d -p 8080:80 nginx
________________________________________
🔹 Open browser:
http://localhost:8080
👉 Output:
•	Nginx welcome page 
________________________________________
📊 STEP 12: Check Running Container
docker ps

Experiment 16: Creating Docker Images using Dockerfile
________________________________________
🎯 Aim
To create a Docker image using a Dockerfile and run it as a container.
________________________________________
🧠 Overview Flow
Application → Dockerfile → Docker Image → Container → Output
________________________________________
⚙️ STEP 1: Create Project Folder
Create a folder:
docker-demo
________________________________________
🧾 STEP 2: Create Application
📄 File: app.py
print("Hello from Docker Container!")
________________________________________
🧾 STEP 3: Create Dockerfile
Inside same folder, create file:
Dockerfile
________________________________________
✍️ Dockerfile code:
# Base image
FROM python:3.9

# Set working directory
WORKDIR /app

# Copy files
COPY . .

# Run application
CMD ["python", "app.py"]
________________________________________
🧠 Explanation of Dockerfile
•	FROM → base image 
•	WORKDIR → working directory 
•	COPY → copies files 
•	CMD → runs program 
________________________________________
▶️ STEP 4: Build Docker Image
Open terminal inside folder:
docker build -t my-python-app .
________________________________________
✅ Output:
Successfully built image
________________________________________
▶️ STEP 5: Run Container
docker run my-python-app
________________________________________
✅ Output:
Hello from Docker Container!
________________________________________
📦 STEP 6: Verify Image
docker images
________________________________________
📦 STEP 7: Verify Container
docker ps -a
________________________________________
❌ STEP 8: Remove Container
docker rm <container_id>
________________________________________
🗑 STEP 9: Remove Image
docker rmi my-python-app
Experiment 17: Docker Volumes and Port Mapping
________________________________________
🎯 Aim
To demonstrate Docker port mapping and volumes for external access and data persistence.
________________________________________
🧠 Overview
Docker Container → Port Mapping → Browser Access
Docker Container → Volume → Persistent Storage
________________________________________
⚙️ STEP 1: Verify Docker Installation
Open terminal:
docker --version
✔ Confirms Docker is installed
________________________________________
🌐 PART 1: PORT MAPPING
________________________________________
▶️ STEP 2: Run Nginx Container
docker run -d -p 8090:80 nginx
________________________________________
🧠 Explanation
-p 8090:80
•	8090 → Host port 
•	80 → Container port 
________________________________________
🌐 STEP 3: Access Application
Open browser:
http://localhost:8090
________________________________________
✅ Output
•	Nginx welcome page is displayed 
________________________________________
📊 STEP 4: Verify Running Container
docker ps
________________________________________
💾 PART 2: DOCKER VOLUMES
________________________________________
📦 STEP 5: Create Volume
docker volume create myvolume
________________________________________
📊 Verify Volume
docker volume ls
________________________________________
▶️ STEP 6: Run Container with Volume
docker run -d -p 8091:80 -v myvolume:/usr/share/nginx/html nginx
________________________________________
🧠 Explanation
-v myvolume:/usr/share/nginx/html
•	myvolume → Docker volume 
•	/usr/share/nginx/html → container directory 
________________________________________
✍️ STEP 7: Modify Data in Container
docker exec -it <container_id> bash
Then:
echo "Hello Volume Data" > /usr/share/nginx/html/index.html
exit
________________________________________
🌐 STEP 8: Access Updated Output
Open browser:
http://localhost:8091
________________________________________
✅ Output
Hello Volume Data
________________________________________
🔁 STEP 9: Verify Data Persistence
Stop and remove container:
docker stop <container_id>
docker rm <container_id>
________________________________________
Run container again:
docker run -d -p 8091:80 -v myvolume:/usr/share/nginx/html nginx
________________________________________
🌐 Open again:
http://localhost:8091
________________________________________
✅ Output
Hello Volume Data
👉 Data persists → volume works
________________________________________
📊 Key Commands Summary
docker run -d -p 8090:80 nginx
docker volume create myvolume
docker run -d -p 8091:80 -v myvolume:/usr/share/nginx/html nginx
docker exec -it <id> bash
docker stop <id>
docker rm <id>
Experiment 18: Docker Image Push to Docker Hub
________________________________________
🎯 Aim
To create, tag, and push a Docker image to Docker Hub for image distribution.
________________________________________
🧠 Overview
Application → Dockerfile → Build Image → Tag → Push → Verify
________________________________________
⚙️ STEP 1: Verify Docker
docker --version
________________________________________
🧾 STEP 2: Create Application
Create folder:
docker-demo
Create file: app.py
print("Hello from Docker Container!")
________________________________________
🧾 STEP 3: Create Dockerfile
Create file: Dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
CMD ["python", "app.py"]
________________________________________
▶️ STEP 4: Build Docker Image
docker build -t my-python-app .
________________________________________
✅ Verify image
docker images
✔ Output:
my-python-app   latest
________________________________________
🔐 STEP 5: Login to Docker Hub
docker login
Enter:
•	Username: midhunrajnp 
•	Password 
✔ Output:
Login Succeeded
________________________________________
🏷 STEP 6: Tag Image (VERY IMPORTANT)
docker tag my-python-app midhunrajnp/docker_demo:latest
________________________________________
✅ Verify again
docker images
✔ You should see:
midhunrajnp/docker_demo   latest
________________________________________
🚀 STEP 7: Push Image
docker push midhunrajnp/docker_demo:latest
________________________________________
✅ Output:
Pushed successfully
________________________________________
🌐 STEP 8: Verify on Docker Hub
Go to:
👉 https://hub.docker.com/
•	Open your account 
•	Go to Repositories 
•	You will see: 
docker_demo
________________________________________
📥 STEP 9: Pull Image (Verification)
docker pull midhunrajnp/docker_demo:latest
________________________________________
▶️ STEP 10: Run Image
docker run midhunrajnp/docker_demo
________________________________________
✅ Output:
Hello from Docker Container!
________________________________________
❗ IMPORTANT ERRORS (MUST WRITE)
________________________________________
❌ 1. No images found
docker images
✔ Fix:
docker build -t my-python-app .
________________________________________
❌ 2. Tag does not exist
tag does not exist
✔ Reason:
•	Wrong name used in push 
✔ Fix:
docker images
docker push correct_name
________________________________________
❌ 3. Access denied
✔ Fix:
docker login
________________________________________
❌ 4. Wrong tag format
✔ Correct format:
username/repository:tag
________________________________________
📊 Command Summary
docker build -t my-python-app .
docker images
docker login
docker tag my-python-app midhunrajnp/docker_demo:latest
docker push midhunrajnp/docker_demo:latest
docker pull midhunrajnp/docker_demo:latest
docker run midhunrajnp/docker_demo


Experiment 19: Jenkins and Docker Integration
________________________________________
🎯 Aim
To integrate Jenkins with Docker and automate the process of building Docker images.
________________________________________
🧠 Overview
GitHub → Jenkins → Docker Build → Image → Container Output
________________________________________
⚙️ STEP 1: Prerequisites
Ensure the following are installed:
•	Docker 
•	Jenkins 
•	Git 
Docker and Jenkins should be running.
________________________________________
🧾 STEP 2: Create Project Files
Create a folder (e.g., docker-demo)
________________________________________
📄 Create app.py
print("Hello from Jenkins Docker Build!")
________________________________________
📄 Create Dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
CMD ["python", "app.py"]
________________________________________
🌐 STEP 3: Push Project to GitHub
Initialize Git:
git init
git add .
git commit -m "Docker Jenkins project"
git branch -M main
git remote add origin https://github.com/your-username/docker-demo.git
git push -u origin main
________________________________________
✅ Verify on GitHub
Ensure the repository contains:
•	Dockerfile 
•	app.py 
________________________________________
🔧 STEP 4: Create Jenkins Job
Open Jenkins:
http://localhost:8080
Steps:
1.	Click New Item 
2.	Enter name: Docker-Jenkins-Demo 
3.	Select Freestyle Project 
4.	Click OK 
________________________________________
🔗 STEP 5: Configure GitHub in Jenkins
In Source Code Management:
•	Select Git 
•	Enter repository URL: 
https://github.com/your-username/docker-demo.git
•	Branch: 
*/main
________________________________________
⚙️ STEP 6: Configure Build Step
Click:
Add Build Step → Execute Windows batch command
________________________________________
Enter command:
docker build -t jenkins-docker-image .
________________________________________
🧹 STEP 7: Clean Workspace (Important)
•	Click Workspace 
•	Click: 
Wipe Out Current Workspace
________________________________________
▶️ STEP 8: Run Build
Click:
Build Now
________________________________________
📊 STEP 9: Check Console Output
You should see:
Cloning repository ✔
docker build -t jenkins-docker-image . ✔
Successfully built ✔
________________________________________
📦 STEP 10: Verify Docker Image
Open terminal:
docker images
________________________________________
✅ Output:
jenkins-docker-image   latest
________________________________________
▶️ STEP 11: Run Docker Image
docker run jenkins-docker-image
________________________________________
✅ Output:
Hello from Jenkins Docker Build!
________________________________________
📊 FINAL OUTPUT
•	Jenkins successfully fetched code from GitHub 
•	Docker image built automatically 
•	Image verified using docker images 
•	Container executed successfully
Experiment 20: Simple End-to-End CI/CD Pipeline
________________________________________
🎯 Aim
To implement a complete CI/CD pipeline using GitHub, Jenkins, JUnit testing, and Docker.
________________________________________
🧠 Overview Flow
GitHub → Jenkins → Run Tests → Build Docker Image → Run Container
________________________________________
⚙️ STEP 1: Prepare Project
Create a project folder with:
________________________________________
📄 app.py
print("CI/CD Pipeline Successful!")
________________________________________
📄 test_app.py (simple test)
def test_sample():
    assert True
________________________________________
📄 Dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
CMD ["python", "app.py"]
________________________________________
🌐 STEP 2: Push to GitHub
git init
git add .
git commit -m "CI/CD pipeline project"
git branch -M main
git remote add origin https://github.com/your-username/cicd-demo.git
git push -u origin main
________________________________________
✅ Verify repo contains:
•	app.py 
•	test_app.py 
•	Dockerfile 
________________________________________
🔧 STEP 3: Create Jenkins Job
Open Jenkins:
http://localhost:8080
Steps:
1.	Click New Item 
2.	Name: CI-CD-Demo 
3.	Select Freestyle Project 
4.	Click OK 
________________________________________
🔗 STEP 4: Connect GitHub
•	Source Code Management → Git 
•	Repo URL: 
https://github.com/your-username/cicd-demo.git
•	Branch: 
*/main
________________________________________
⚙️ STEP 5: Configure Build Steps
Click:
Add Build Step → Execute Windows batch command
________________________________________
✍️ Add commands:
echo Running Tests...
python -m pytest

echo Building Docker Image...
docker build -t cicd-image .

echo Running Container...
docker run cicd-image
________________________________________
▶️ STEP 6: Run Build
Click:
Build Now
________________________________________
📊 STEP 7: Check Console Output
You should see:
Running Tests... ✔
Building Docker Image... ✔
Successfully built ✔
Running Container... ✔
CI/CD Pipeline Successful!
________________________________________
📦 STEP 8: Verify Docker Image
docker images
________________________________________
▶️ STEP 9: Run Again (optional)
docker run cicd-image
________________________________________
✅ Output:
CI/CD Pipeline Successful!

