# Lambda School Web API: Java Course

## Software installations for Week 3

<details><summary>For All Operating Systems</summary>
<p>

### Nothing to install that is NOT operating system specific. See your OS link for installation instructions

</p>
</details>

<details><summary>For Windows 10 Operating System</summary>
<p>

### Install Heroku CLI on a Windows 10 based computer

[![Video to Install Heroku CLI](http://img.youtube.com/vi/s6QI9rHUd9E/0.jpg)](http://www.youtube.com/watch?v=s6QI9rHUd9E)

- Create a free Heroku Account at [https://www.heroku.com](https://www.heroku.com)
- Download and install the Heroku CLI software from [https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)
- To test, from a command prompt type
  `heroku login`

---

### Install Tomcat on a Windows 10 based computer

[![Video to Install Tomcat](http://img.youtube.com/vi/ujTiDoTkcQ4/0.jpg)](http://www.youtube.com/watch?v=ujTiDoTkcQ4)

- Download and install the software from [https://tomcat.apache.org/download-90.cgi](https://tomcat.apache.org/download-90.cgi)
- Tomcat by default installs as a Windows Service running on port 8080
- To test surf to localhost:8080 and see the Tomcat opening page appear

---

</p>
</details>

<details><summary>For Mac OS</summary>
<p>

### Install Heroku CLI on a Mac OS Computer

[![Video to Install Heroku CLI](http://img.youtube.com/vi/ty5xkk-P8qs/0.jpg)](http://www.youtube.com/watch?v=ty5xkk-P8qs)

Create a free Heroku account at the website [https://www.heroku.com](https://www.heroku.com)

Install the Heroku CLI. At a terminal prompt, enter  
`brew tap heroku/brew && brew install heroku`

Test Heroku by entering a terminal prompt  
`heroku login`

---

### Install Tomcat on a Mac OS Computer

[![Video to Install Tomcat](http://img.youtube.com/vi/vM0TDbm09LM/0.jpg)](http://www.youtube.com/watch?v=tvM0TDbm09LM)

To install the software

- brew install tomcat
- brew services start tomcat
  The configuration file can be found at  
  `/usr/local/Cellar/tomcat/9.0.17/libexec/conf`

---

</details>

<details><summary>For Linux specifically Ubuntu 18</summary>
<p>
  
### Install Heroku CLI on a Linux Computer

[![Video to Install Heroku CLI](http://img.youtube.com/vi/6Wm2Oo2ixXI/0.jpg)](http://www.youtube.com/watch?v=6Wm2Oo2ixXI)

Create a free Heroku account at the website https://www.heroku.com

Install the Heroku CLI. At a terminal prompt, enter  
`sudo snap install --classic heroku`

Test Heroku by entering a terminal prompt  
`heroku login`

---

### Install Tomcat on a Linux Computer

[![Video to Install Tomcat](http://img.youtube.com/vi/PbFgS2SfaZE/0.jpg)](http://www.youtube.com/watch?v=PbFgS2SfaZE)

To install Apache Tomcat, enter the following from a terminal prompt:

- sudo groupadd tomcat
- sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
- cd /opt/
- sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.27/bin/apache-tomcat-9.0.27.tar.gz
- sudo tar -xzvf apache-tomcat-9.0.27.tar.gz
- sudo mv apache-tomcat-9.0.27/ tomcat/
- sudo chown -hR tomcat:tomcat /opt/tomcat
- sudo chmod +x /opt/tomcat/bin/
- sudo nano ~/.bashrc

  - Add the following line  
    `export CATALINA_HOME=/opt/tomcat`
  - exit nano

- source ~/.bashrc
- echo \$CATALINA_HOME  
  You should see /opt/tomcat

- cd /etc/systemd/system/
- sudo nano apache-tomcat.service
  - enter the following 18 lines
  - be sure to change your java version on line 9

```
[Unit]
Description=Apache Tomcat 9 Servlet Container
After=syslog.target network.target

[Service]
User=tomcat
Group=tomcat
Type=forking
Environment=JAVA_HOME=/usr/lib/jvm/java-YOUR JAVA VERSION GOES HERE-oracle
Environment=CATALINA_PID=/opt/tomcat/tomcat.pid
Environment=CATALINA_HOME=/opt/tomcat
Environment=CATALINA_BASE=/opt/tomcat
ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

- exit nano

- sudo chown -hR tomcat:tomcat /opt/tomcat
- sudo chmod +x /opt/tomcat/bin/

- systemctl daemon-reload
- systemctl start apache-tomcat.service
- systemctl enable apache-tomcat.service
- systemctl status apache-tomcat.service
  - IF ALL WENT WELL YOU SHOULD SEE A GREEN "active (running)" message.
- To test Tomcat, surf to localhost:8080
  - You should see the Tomcat default webpage
  - Tomcat defaults to listening on port 8080

---

</p>
</details>
