# nexus-oss-2
Nexus Repository Manager OSS 2 Configuration
Latest update: 2.14.2 (2016-12-18) - Replace with later version if needed
VM: Instance runs on AWS Lightsail (Linux rhel fedora 2016.09)

## OSS 2 Installation Summary for AWS Lightsail Instance

### Installation
```
Download or wget (see "OSS Download" below) the bundle.tar.gz from above listed site
tar xvzf nexus-2.14.2-01-bundle.tar.gz
sudo mkdir /app && cd /app (instead of /usr/local since creating a 'nexus' user)
sudo cp nexus-2.14.2-01-bundle.tar.gz .
sudo tar xvzf nexus-2.14.2-01-bundle.tar.gz
sudo ln -s nexus-2.14.2-01 nexus (the sibling directory 'sonatype-work' is also created here)
```

### Setup
```
sudo yum update -y (if needed)
sudo yum install java-1.8.0-openjdk.x86_64 (if needed)
sudo adduser nexus
sudo chown -R nexus:nexus /app/nexus-2.14.2-01 (not the symlink)
sudo chown -R nexus:nexus /app/sonatype-work
export NEXUS_HOME=/app/nexus (or add this to a .bashrc or similar shell script)
Set RUN_AS_USER="nexus" in the $NEXUS_HOME/bin/nexus script
```

### Running
```
cd $NEXUS_HOME
./bin/nexus start (starts the instance by default on port 8081)
"./bin/nexus status" or "./bin/nexus stop" can be executed for daemon status and stopping
If all went well, the UI should come using url http://<ip or localhost>:8081/nexus
The initial credentials are admin/admin123 (click on "profile" to set up user/change password)
```

### Troubleshooting
```
Logs: cd $NEXUS_HOME && tail -f logs/wrapper.log
To change the port edit the "conf/nexus.properties" file and change the "application-port"
Other parameters can be tweaked in the "conf/nexus.properties" (see documentation)
To open a tcp/udp port (or range) consult the iptables (or similar command) documentation
```

### Configure Hosted Yum Repositories

This option is available in the OSS 2 configuration (but only in NRM PRO for v3). Before configuring 
this capability ensure that _createrepo_ and _mergerepo_ are available (usually under /usr/bin). If needed,
_sudo yum install createrepo_ and ensure that the correct path of these commands is referenced in the 
Nexus configuration under _Capabilities -> Yum: Configuration_. To Yum enable repositories simply click 
on the 'Enabled' checkbox under this same location (see also the [Sonatype Docs](https://books.sonatype.com/nexus-book/reference/yum-configuration.html))

## References
* Latest Releases (v2 and 3): https://www.sonatype.com/download-oss-sonatype
* Support Site: https://support.sonatype.com/hc/en-us/articles/213464118-Download-Sonatype-Nexus
* OSS Download: https://download.sonatype.com/nexus/oss/nexus-2.14.2-01-bundler.tar.gz
* Archives for NRM OSS 2: https://support.sonatype.com/hc/en-us/articles/218238798
* Sonatype Installation and Running instructions: https://books.sonatype.com/nexus-book/reference/install.html
