mysql 主从配置  
=============  

`1. 注意数据版本,从库版本尽量保持与主库一致!`  

### 1.从库配置  

```properties
# need for slave
server-id = 17                            # 指定唯一id
master-info-repository = file
relay-log-info_repository = file
binlog-format = ROW
gtid-mode = ON                            # 打开gtid模式
enforce-gtid-consistency = true
log-bin = hostname-bin
relay-log = hostname-relay-bin
log-slave-updates
replicate-do-table=bms.bm_charge_detail    # 指定同步库与表
``` 

### 2.重启从库  

### 3.从库设置master库信息  

```sql
change master to
master_host='xxx',
master_user='xxx',
master_port=xxx,
master_password='xxx',         -- master库连接信息
master_log_file='xxx',         
master_log_pos=xxx,            -- master库执行 "flush logs;show master status;"查看
master_auto_position=0;        -- 0||1，1代表自动，0更具指定的${master_log_file}、${master_log_pos}信息同步。
``` 

### 4.开启从库同步线程  

```sql
-- reset slave; 
start slave;
-- stop slave;

-- truncate table mysql.slave_relay_log_info;
-- truncate table mysql.slave_master_info;           -- 重置主从信息
``` 

