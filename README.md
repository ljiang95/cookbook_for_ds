# Cookbook for Data Science
## Hive
### Bash
submit job via an HQL file
```bash
nohup hive -f query.hql > query.log &
# 'nohup' is a command that ignores the HUP signal. If we want to continue running the process even after logout or disconnection from the current shell, we can use nohup command. 
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
check data files on HDFS
```bash
hdfs dfs -du -h {table_location}
```
remove data files on HDFS
```bash
hdfs dfs -rm -R {table_location}
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
