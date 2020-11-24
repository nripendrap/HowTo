# Aws Getting Started






## Amazon ElastiCache

ssh -i elasticachedserver.pem ec2-user@1.1.1.1 

In order to connect to redis cluster, we need to install bit of software quickly.

sudo yum update
sudo yum install gcc - install compiler to your new instance 

download redis client
wget http://download.redis.io/redis-stable.tar.gz

tar xvzf redis-stable.tar.gz
cd redis-stable

make distclean
make

ping simplerediscluster.fsx8yh.0001.apse2.amazonaws.com
10.0.2.10

Connect cluster with this command
src/redis-cli -c -h simplerediscluster.fsx8yh.0001.apse2.amazonaws.com -p 6367

Console be like/Command line value changed to <endpoint:port>
simplerediscluster.fsx8yh.0001.apse2.cache.amazonaws.com:6379>
This indicates you are connected to the server


Connect to Cluster from Outside AWS

We need to create NAT (Network Address Translator) instance 



NAT ec2 public ip
13.211.95.59

ssh -i C:\Users\PradNrip\Downloads\elasticcachedevserver.pem ec2-user@13.211.95.59

sudo yum update

sudo su
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 6379 -j DNAT --to 10.0.2.10:6379
service iptables save -- save that changes  /etc/sysconfig/iptables

add record to an iptable of OUR NAT SERVER

ALL TRAFFIC IT SEES coming through on port 6379 over to our cluster node having given ip address
