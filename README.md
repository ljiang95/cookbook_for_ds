# Cookbook for Data Science
## Hive
### Bash
submit job via an HQL file
```bash
nohup hive -f query.hql > query.log &
# 'nohup' is a command that ignores the HUP signal. If we want to continue running the process even after logout or disconnection from the current shell, we can use nohup command. 
# '>': If the file exists, it will be replaced. '>>': If the file does not exist, it will be created. If it exists, It will be appended to the end of the file. 
# '&' makes the command run in the background.  
```
submit job via an HQL file in order to pull the data
```bash
nohup hive -f query.hql 2> query.log 1> query.txt &
# File descriptor 2 represents standard error, and 1 represents standard output. 
```
submit job via a direct query
```bash
nohup hive -e 'set some_settings=true; select some_columns from some_tables;' > query.log &
```
display data files on HDFS with formating file sizes in a 'human-readable' fashion (e.b 64 M instead of 67108864)
```bash
hdfs dfs -du -h {table_location}
```
display data files on HDFS with showing the names of columns as a header line
```bash
hdfs dfs -du -v {table_location}
# In most of the cases, the first column shows the size of the data files, the second column shows the disk space consumed with all replicas, and the third column shows the full path name. 
```
remove data files on HDFS
```bash
hdfs dfs -rm -R {table_location}
```
move (overwrite) a file from local to HDFS path
```bash
hdfs dfs -put -f {source_location+filename} {target_location+filename}
```
change the permission of an HDFS path
```bash
hadoop fs -chmod -R 1777 {schema_location}
# All files or directories created in this directory will belong to the group that owns the directory. 
# There should be an hdfs command update. 
```
check the list of jobs
```bash
yarn application -list
```
check the status of a job
```bash
yarn application -status {Application-Id}
```
check the log of a job
```bash
yarn logs -applicationId {Application-Id}
# Not recommended as there will be verbose output. 
```
kill a job
```bash
yarn application -kill {Application-Id}
```
### Hive Commands
create a schema
```hiveql
create database {schema_name}
```
create a schema with tentative location
```hiveql
create database {schema_name} {schema_location}
```


## General Linux Bash
display running process
```bash
ps
```
display running process with more info
```bash
ps aux
# a option outpus all running processes of all users in the system. 
# u option provides additional information like memory and CPU usage percentage, the process state code, and the owner of the processes. 
# x option lists all processes not executed from the terminal. A perfect example of this are daemons, which are system-related processes that run in the background when the system is booted up. 
```
display all historical commands
```bash
history
```
