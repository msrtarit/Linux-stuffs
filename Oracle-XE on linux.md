https://docs.google.com/document/d/1YZV0nwNLMofrdxUS0mmfPYIvFgPEG0nghi3MpBfbJ1M/


## actually I had to do a lot of tiny things on my pc to run linux.I have to do many tweaks every now and then.so I will try to write down them here or atleast their source links here for future uses      ##


Installing oracle-XE 11g on manjaro:
https://gist.github.com/davidmaignan/d0d941cbf761678457b865e6de041af0




### Clone git repository
```
git clone https://aur.archlinux.org/oracle-xe.git
cd oracle-xe
```

### Download oracle-xe-rpm.zip
```
wget http://download.oracle.com/otn/linux/oracle11g/xe/oracle-xe-11.2.0-1.0.x86_64.rpm.zip
```

### Installation (follow instructions)
```
makepkg -si
```
### Run configuration
```
/etc/rc.d/oracle-xe configure
```

### Locate oracle_env.sh - it should be located somewhere in the cloned folder
```
source oracle_env.sh 
```

### Connect to oracle
```
sqlplus /nolog
```

### at sql prompt
```
connect system/password
```

### create a user
```
create user usename identified by password;
```

### Grant permissions
```
grant CREATE SESSION, ALTER SESSION, CREATE DATABASE LINK, CREATE MATERIALIZED VIEW, CREATE PROCEDURE, CREATE PUBLIC SYNONYM, CREATE ROLE, CREATE SEQUENCE, CREATE SYNONYM, CREATE TABLE, CREATE TRIGGER, CREATE TYPE, CREATE VIEW, UNLIMITED TABLESPACE  to username;
```

### Swith to the newly created user
```
connect username/password
```

### Check tables
```
select table_name from user_tables;
```

### Logout 
```
exit
```
### Login
```
sqlplus username/password
```

### Start, stop server
```
/etc/rc.d/oracle-xe {start|stop|restart|force-reload|configure|status|enable|disable}
```

## Ressources
https://aur.archlinux.org/packages/oracle-xe/
https://docs.oracle.com/cd/B25329_01/doc/admin.102/b25107/connecting.htm#CHDJDAJA
https://docs.oracle.com/cd/E17781_01/admin.112/e18585/toc.htm#XEGSG111


