# Frontend Setup: Install Node.js on Ubuntu

This guide explains how to install **Node.js** on **Ubuntu** for frontend development.  
Two recommended methods are included:

- **Method 1:** Install Node.js (LTS) using NodeSource (simple & fast)
- **Method 2:** Install Node.js using NVM (best for managing multiple versions)

---

## Prerequisites

- Ubuntu 20.04 / 22.04 (or later)
- Terminal access
- `sudo` privileges

Update system packages first:

```bash
sudo apt update && sudo apt upgrade -y


                                           ----
** Method 1: Install Node.js (LTS) Using NodeSource**
**Step 1: Install required packages**
```                                           
sudo apt install -y ca-certificates curl gnupg
```
Step 2: Add NodeSource repository (LTS version)
```                                           
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
```
Step 3: Install Node.js
```
sudo apt install -y nodejs
```
Step 4: Verify installation
```
node -v
npm -v
```
## Method 2: Install Node.js Using NVM (Recommended for Frontend Devs)

## NVM (Node Version Manager) allows switching between Node.js versions easily.

*Step 1: Install NVM
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```
Step 2: Reload terminal
```                                           
source ~/.bashrc
```
Step 3: Install Node.js (LTS)
```                                           
nvm install --lts
```
Step 4: Use LTS version
```                                           
nvm use --lts
```
Step 5: Verify installation
```                                           
node -v
npm -v
```
Optional: Install Yarn (Popular Frontend Package Manager)
```                                           
npm install -g yarn
```

Verify:
```
yarn -v
```
Common Frontend Tools (Optional)
```                                           
npm install -g vite create-react-app @angular/cli
```
Troubleshooting

If node command not found:
```
source ~/.bashrc
```
- Check installed versions:
```bash
nvm ls
```

# Middleware Setup: Install JDK and Maven on Ubuntu

Step 1: Install JDK (OpenJDK)
Option A: Install OpenJDK 17 (Recommended – LTS)
```
                                           sudo apt install -y openjdk-17-jdk
```
Option B: Install OpenJDK 11 (If project requires it)
```
                                           sudo apt install -y openjdk-11-jdk
```
Step 2: Verify Java Installation
                                           ```
java -version
javac -version
```                                           


Expected output example:

openjdk version "17.x.x"

Step 3: Set JAVA_HOME Environment Variable
Find Java installation path
                                           ```
sudo update-alternatives --config java
```

Example path:
```
/usr/lib/jvm/java-17-openjdk-amd64
```
Set JAVA_HOME

Edit profile file:
```
nano ~/.bashrc
```

Add the following lines (adjust path if needed):

export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin


Apply changes:

source ~/.bashrc


Verify:

echo $JAVA_HOME

Step 4: Install Apache Maven
                         ```
sudo apt install -y maven
```
Step 5: Verify Maven Installation
```
                         mvn -version
```
## https://www.digitalocean.com/community/tutorials/install-maven-linux-ubuntu

Step 7: Test Maven with Sample Project
mvn archetype:generate \
  -DgroupId=com.example \
  -DartifactId=demo-app \
  -DarchetypeArtifactId=maven-archetype-quickstart \
  -DinteractiveMode=false


Build the project:

cd demo-app
mvn clean package

--
Step 1: Prepare AWS RDS PostgreSQL
1. RDS Configuration Checklist

Engine: PostgreSQL

Port: 5432

Public or Private access (based on architecture)

Security Group:

Allow inbound TCP 5432 from middleware IP / VPC

Database name, username, password created

Example:

DB Name: appdb
Username: appuser
Port: 5432
Endpoint: mydb.xxxxxx.ap-south-1.rds.amazonaws.com      


Step 2: Install PostgreSQL Client on Middleware (Optional but Recommended)
sudo apt install -y postgresql-client

Test RDS Connectivity
psql -h mydb.xxxxxx.ap-south-1.rds.amazonaws.com \
     -U appuser \
     -d appdb \
     -p 5432


                         ### go to this localtion springapp/src/main/resources/application.properties
spring.application.name=springapp
spring.datasource.url=${SPRING_DATASOURCE_URL:jdbc:postgresql://10.24.1.10:5432/eventdb} ## < provide DB endpoint>
spring.datasource.username=${SPRING_DATASOURCE_USERNAME:admin}  # db username
spring.datasource.password=${SPRING_DATASOURCE_PASSWORD:Admin@123} # db pasword
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.open-in-view=false
server.port=8082                         
                         
