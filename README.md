# Ansible role mesos on AWS

## Machine as Mesos slave/agent

To make a EC2 instance a Mesos slave/agent add the following to the user-data.

```bash
# Set properties
sudo /opt/mesos/set-slave-config.sh attributes purpose:lb
sudo /opt/mesos/set-slave-config.sh containerizers docker

# Make instance Mesos slave and connect to zookeeper
sudo /opt/mesos/make-slave-master-on-aws.sh ZK://host-to-zookeeper/mesos
```

For slave/agent properties look [here](http://mesos.apache.org/documentation/latest/configuration/agent/)

## Machine as Mesos master

To make a EC2 instance a Mesos master add the following to the user-data.

```bash
# Set properties
sudo /opt/mesos/set-master-config.sh attributes purpose:lb

# Make instance Mesos slave and connect to zookeeper
sudo /opt/mesos/make-slave-master-on-aws.sh ZK://host-to-zookeeper/mesos
```

For master properties look [here](http://mesos.apache.org/documentation/latest/configuration/master/)