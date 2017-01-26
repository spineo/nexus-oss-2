# nexus-oss-2
Nexus Repository Manager OSS 2 Configuration
Latest update: 2.14.2 (2016-12-18) - Replace with later version if needed
VM: Instance runs on AWS Lightsail (Linux rhel fedora 2016.09)

## References
* Latest Releases (v2 and 3): https://www.sonatype.com/download-oss-sonatype
* Support Site: https://support.sonatype.com/hc/en-us/articles/213464118-Download-Sonatype-Nexus
* OSS Download: https://download.sonatype.com/nexus/oss/nexus-2.14.2-01-bundler.tar.gz
* Archives for NRM OSS 2: https://support.sonatype.com/hc/en-us/articles/218238798
* Installing and Running instructions: https://books.sonatype.com/nexus-book/reference/install.html

## OSS 2 Installation Summary for AWS Lightsail Instance

### Installation
```
Download or wget (see "OSS Download" above) the bundle.tar.gz from above listed site
tar xvzf nexus-2.14.2-01-bundle.tar.gz
sudo mkdir /app && cd /app (instead of /usr/local since creating a 'nexus' user)
sudo cp nexus-2.14.2-01-bundle.tar.gz .
sudo tar xvzf nexus-2.14.2-01-bundle.tar.gz
sudo ln -s nexus-2.14.2-01 nexus (the sibling directory 'sonatype-work' will also be created here)
```

### Setup
```
sudo yum update -y (if needed)
sudo yum install java-1.8.0-openjdk.x86_64 (if needed)
sudo adduser nexus
sudo chown -R nexus:nexus /app/nexus
export NEXUS_HOME=/app/nexus (or add this to a .bashrc or similar shell script)
```
