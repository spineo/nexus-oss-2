# nexus-oss-2
Nexus Repository Manager OSS 2 Configuration
Latest update: 2.14.2 (2016-12-18)
VM: Instance runs on AWS Lightsail (Linux rhel fedora 2016.09)

## References
* Latest Releases (v2 and 3): https://www.sonatype.com/download-oss-sonatype
* Support Site: https://support.sonatype.com/hc/en-us/articles/213464118-Download-Sonatype-Nexus
* Archives for NRM OSS 2: https://support.sonatype.com/hc/en-us/articles/218238798
* Installing and Running instructions: https://books.sonatype.com/nexus-book/reference/install.html

## OSS 2 Installation Summary for AWS Lightsail Instance

### Installation
```
1. Download the bundle.tar.gz from above listed site
2. tar xvzf nexus-2.14.2-01-bundle.tar.gz
3. sudo cp nexus-2.14.2-01-bundle.tar.gz /usr/local
4. cd /usr/local
5. sudo tar xvzf nexus-2.14.2-01-bundle.tar.gz
6. sudo ln -s nexus-2.14.2-01 nexus
```

### Setup
```
1. export NEXUS_HOME=/usr/local/nexus (or add this to a .bashrc or similar shell script)

```
