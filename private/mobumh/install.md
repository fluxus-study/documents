설치
==============================
- CentOS 6.5 64bit
- passwd
- yum update -y
- yum install -y wget

- yum install -y curl-devel zlib-devel.x86_64 perl-ExtUtils-MakeMaker.x86_64

- yum groupinstall -y "Development Tools"
- cd /tmp
- wget https://git-core.googlecode.com/files/git-1.9.0.tar.gz
- tar xvfz git-1.9.0.tar.gz
- cd git-1.9.0
- ./configure
- make
- make install
- dev 계정

- adduser dev
- passwd dev
- su - dev

- mkdir ~/local && cd ~/local

- wget http://nodejs.org/dist/v0.10.26/node-v0.10.26-linux-x64.tar.gz
- tar xvfz node-v0.10.26-linux-x64.tar.gz
- cd node-v0.10.26-linux-x64
- vi ~/.bash_profoile
 - 행추가PATH=$PATH:/home/dev/local/node-v0.10.26-linux-x64/bin
. ~/.bash_profile

- cd ~/local
- wget http://fastdl.mongodb.org/linux/mongodb-linux-x86_64-2.4.9.tgz
- tar xvfz mongodb-linux-x86_64-2.4.9.tgz
- cd mongodb-linux-x86_64-2.4.9
- vi ~/.bash_profile
 - 행추가 PATH=$PATH:/home/dev/local/mongodb-linux-x86_64-2.4.9/bin
- mongod --dbpath=/home/dev/data/db
- grunt 에서 오류. 접속불가능으로 보임.
