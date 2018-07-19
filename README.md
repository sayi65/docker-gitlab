# docker-gitlab

### centos6.7

$ sudo yum update

$ sudo tee /etc/yum.repos.d/docker.repo <<- 'EOF'

[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/$releasever/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
EOF

$ sudo yum install docker-engine
$ docker -v

## dockerをdaemon起動させる

$ sudo chkconfig docker on

$ sudo tee /etc/sysconfig/docker <<- 'EOF'
other_args="-H tcp://127.0.0.1:4243 -H unix:///var/run/docker.sock"
EOF

$ sudo service docker start
$ sudo usermod -aG docker vagrant
