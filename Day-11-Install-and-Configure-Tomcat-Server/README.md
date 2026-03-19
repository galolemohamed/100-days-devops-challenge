#  Day 11 – Tomcat Server Installation and Configuration

##  Task Overview

In this task, I installed and configured an Apache Tomcat server on **App Server 2 (stapp02)**, deployed a Java-based application, and verified that it is accessible via the browser using a custom port.

---

##  Objectives

* Install Tomcat on App Server 2
* Configure Tomcat to run on a custom port (**8089**)
* Deploy a Java application using a `ROOT.war` file
* Ensure the application is accessible from the base URL

---

##  Steps Performed

### 1. Installed Tomcat

Used the system package manager to install Tomcat on the server.

```bash
sudo yum install -y tomcat
```

---

### 2. Configured Custom Port

Updated the Tomcat configuration file:

```bash
sudo vi /etc/tomcat/server.xml
```

Changed the default port to:

```xml
<Connector port="8089" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
```

---

### 3. Deployed Application

* Copied `ROOT.war` from the jump host to App Server 2
* Moved it to the Tomcat webapps directory

```bash
scp thor@jump-host:/tmp/ROOT.war /tmp/
sudo cp /tmp/ROOT.war /var/lib/tomcat/webapps/
```

---

### 4. Restarted Tomcat

```bash
sudo systemctl restart tomcat
sudo systemctl enable tomcat
```

---

### 5. Verified Deployment

Tested the application using:

```bash
curl http://stapp02:8089
```

---

##  Result

The application was successfully deployed and accessible at:

```
http://stapp02:8089
```

Output:

```html
<h2>Welcome to xFusionCorp Industries!</h2>
```

---

##  Key Learnings

* How to configure Tomcat on a custom port
* Deploying Java applications using `.war` files
* Importance of `ROOT.war` for base URL access
* Troubleshooting connectivity and deployment issues

---

##  Notes

* Using `ROOT.war` ensures the app loads directly without a context path
* Always restart Tomcat after configuration changes
* Verify service status if the app fails to load


