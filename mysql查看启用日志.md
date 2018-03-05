
mysql有以下几种日志：  
   错误日志：     -log-err  
   查询日志：     -log  
   慢查询日志:   -log-slow-queries  
   更新日志:     -log-update  
   二进制日志： -log-bin  


是否启用了日志 
mysql>show variables like 'log_%'; 

怎样知道当前的日志 
mysql> show master status; 

顯示二進制日志數目 
mysql> show master logs; 

看二进制日志文件用mysqlbinlog 
shell>mysqlbinlog mail-bin.000001 
或者shell>mysqlbinlog mail-bin.000001 | tail 

在配置文件中指定log的輸出位置. 
Windows：Windows 的配置文件为 my.ini，一般在 MySQL 的安装目录下或者 c:\Windows 下。 
Linux：Linux 的配置文件为 my.cnf ，一般在 /etc 下。 

在linux下： 



Sql代码  收藏代码
1.# 在[mysqld] 中輸入  
2.#log  
3.log-error=/usr/local/mysql/log/error.log  
4.log=/usr/local/mysql/log/mysql.log  
5.long_query_time=2  
6.log-slow-queries= /usr/local/mysql/log/slowquery.log  



windows下: 



Sql代码  收藏代码
1.# 在[mysqld] 中輸入  
2.#log  
3.log-error="E:/PROGRA~1/EASYPH~1.0B1/mysql/logs/error.log"  
4.log="E:/PROGRA~1/EASYPH~1.0B1/mysql/logs/mysql.log"  
5.long_query_time=2  
6.log-slow-queries= "E:/PROGRA~1/EASYPH~1.0B1/mysql/logs/slowquery.log"  



开启慢查询 
long_query_time =2  --是指执行超过多久的sql会被log下来，这里是2秒 
log-slow-queries= /usr/local/mysql/log/slowquery.log  --将查询返回较慢的语句进行记录 

log-queries-not-using-indexes = nouseindex.log  --就是字面意思，log下来没有使用索引的query 

log=mylog.log  --对所有执行语句进行记录