Install Java

> $ sudo apt update; sudo apt install openjdk-11-jdk-headless -y; 

Get JAVA_HOME  


>   \$ dirname \$(dirname \$(readlink -f \$(which java)))  
/usr/lib/jvm/java-11-openjdk-arm64

Create Hadoop HDFS Directories  

> $ sudo mkdir /opt/hdfs  

> $ sudo mkdir /opt/hdfs/{namenode,datanode}    

> $ cd /opt  

Download and Extract Hadoop  

> $ sudo wget https://dlcdn.apache.org/hadoop/common/hadoop-3.3.5/hadoop-3.3.5-aarch64.tar.gz  

> $ sudo tar xzf hadoop-3.3.5-aarch64.tar.gz  

> $ sudo mv hadoop-3.3.5 /opt/hadoop

Create a hadoop user  

> $ sudo useradd -r hadoop -d /opt/hadoop

Change Owner of Hadoop Directories  

> $ sudo chown hadoop:hadoop /opt/{hadoop,hdfs} -R

Change to hadoop user  

> $ sudo su - hadoop

Add JAVA_HOME to end of .bashrc 

> $ nano ~/.bashrc

Add to the bottom of the file

    export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-arm64   

    export HADOOP_HOME=/opt/hadoop  
    export HADOOP_INSTALL=$HADOOP_HOME  
    export HADOOP_MAPRED_HOME=$HADOOP_HOME  
    export HADOOP_COMMON_HOME=$HADOOP_HOME  
    export HADOOP_HDFS_HOME=$HADOOP_HOME  
    export YARN_HOME=$HADOOP_HOME  
    export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native  
    export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin  

Set .profile  

> $ nano ~/.profile

Add this to the bottom of the file  

    PATH=/opt/hadoop/bin:/opt/hadoop/sbin:$PATH

