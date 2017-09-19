# Cloud_Assignment1
How to Run file

Step 1: Start the hadoop server by navigating on the folder which consists of the pem key, on your local machine. 
	ssh -i "HadoopKey1.pem" ubuntu@public_IP_DNS
Step 2: Open a new Terminal window and upload the code onto the hadoop server
	scp -i "HadoopKey1.pem" <jar file> ubuntu@public_IP_DNS:
Step 3: After the file has been successfully uploaded, open the ubuntu server and type in the following command. The jar file can be viewed there.
	ls
Step 4: Run the Task1.jar file
	hadoop jar Assign2.jar /input /output/output1
Step 5: After successful map and reduce of the program, an output1 file will be created. 
	hdfs dfs -ls /output
Step 6: To view the contents of the output file type in the following command:
hdfs dfs -cat /output/output1/output1-partr-00000
Step 7: Repeat the above steps for Task2 and Task3.
 

To view datanode information
Open your browser and type in the following:
masternode@public_DNS_IP:50070

Common HDFS Commands
List all files and folder in directory
hdfs dfs -ls <folder name>
Make a directory on HDFS
hdfs dfs -mkdir <folder name>
Copy a file from the local machine (namenode) into HDFS
hdfs dfs -copyFromLocal <local folder or file name>
Delete a file on HDFS
hdfs dfs -rm <file name>
Delete a directory on HDFS
hdfs dfs -rmdir <folder name>

HDFS Examples

# create local dummy file to place on HDFS
namenode$ echo "Hello this will be my first distributed and fault-tolerant data set\!" | cat >> my_file.txt

# list directories from top level of HDFS
namenode$ hdfs dfs -ls /

# This should display nothing but a temp directory
# create /user directory on HDFS
namenode$ hdfs dfs -mkdir /user
namenode$ hdfs dfs -ls /
Found 1 items
drwxr-xr-x — ubuntu supergroup 0 2015–05–06 22:41 /user

# copy local file a few times onto HDFS
namenode$ hdfs dfs -copyFromLocal ~/my_file.txt /user
namenode$ hdfs dfs -copyFromLocal ~/my_file.txt /user/my_file2.txt
namenode$ hdfs dfs -copyFromLocal ~/my_file.txt /user/my_file3.txt

# list files in /user directory
namenode$ hdfs dfs -ls /user
Found 1 items
-rw-r — r — 3 ubuntu supergroup 50 2015–05–06 22:43 /user/my_file.txt
-rw-r — r — 3 ubuntu supergroup 50 2015–05–06 22:43 /user/my_file2.txt
-rw-r — r — 3 ubuntu supergroup 50 2015–05–06 22:43 /user/my_file3.txt

# clear all data and folders on HDFS
namenode$ hdfs dfs -rm /user/my_file*
15/05/06 22:49:06 INFO fs.TrashPolicyDefault: Namenode trash configuration: Deletion interval = 0 minutes, Emptier interval = 0 minutes.
Deleted /user/my_file.txt
15/05/06 22:49:06 INFO fs.TrashPolicyDefault: Namenode trash configuration: Deletion interval = 0 minutes, Emptier interval = 0 minutes.
Deleted /user/my_file2.txt
15/05/06 22:49:06 INFO fs.TrashPolicyDefault: Namenode trash configuration: Deletion interval = 0 minutes, Emptier interval = 0 minutes.
Deleted /user/my_file3.txt
namenode$ hdfs dfs -rmdir /user


References
The following link was used to build the Hadoop Clusters:

https://blog.insightdatascience.com/spinning-up-a-free-hadoop-cluster-step-by-step-c406d56bae42


