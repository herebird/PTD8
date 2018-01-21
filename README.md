# PTD8
ตัวเต็ม pritunl รองรับ Debian 8



nano /etc/apt/sources.list.d/mongodb-org-3.0.list
deb http://repo.mongodb.org/apt/debian wheezy/mongodb-org/3.0 main

nano /etc/apt/sources.list.d/pritunl.list
deb http://repo.pritunl.com/stable/apt jessie main

apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv 7F0CEB10
apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv CF8E292A

apt-get update
apt-get install pritunl mongodb-org

systemctl start mongod pritunl
systemctl enable mongod pritunl

sudo sh -c 'echo "* hard nofile 64000" >> /etc/security/limits.conf'
sudo sh -c 'echo "* soft nofile 64000" >> /etc/security/limits.conf'
sudo sh -c 'echo "root hard nofile 64000" >> /etc/security/limits.conf'
sudo sh -c 'echo "root soft nofile 64000" >> /etc/security/limits.conf'

