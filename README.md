# For setting up an ec2 t3.medium machine with Amazon AMI 2

1) in Route 53, create a record set for the chosen domain name that points to the machine's IP address
2) ssh to the machine as ec2-user
3) sudo yum update
4) sudo yum install emacs
5) wget https://dl.eff.org/certbot-auto
6) sudo mv certbot-auto /usr/local/bin/certbot-auto
7) sudo chown root /usr/local/bin/certbot-auto
8) sudo chmod 0755 /usr/local/bin/certbot-auto
9) in /usr/local/bin/certbot-auto, replace the line `elif [ -f /etc/issue ] && grep -iq "Amazon Linux" /etc/issue ; then` with `elif grep -i "Amazon Linux" /etc/issue > /dev/null 2>&1 || grep 'cpe:.*:amazon_linux:2' /etc/os-release > /dev/null 2>&1; then`
10) sudo /usr/local/bin/certbot-auto certonly --standalone --debug 
