# Cookbook for Data Science
## Hive
### Bash
submit job via an HQL file
```bash
nohup hive -f query.hql > query.log &
```
submit job via an HQL file in order to pull the data
```bash
nohup hive -f query.hql 2> query.log 1> query.txt &
```
submit job via a direct query
```bash
nohup hive -e 'set some_settings=true; select some_columns from some_tables;' > query.log &
```
