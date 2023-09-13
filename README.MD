Container for SQLServer19 on Ubuntu20.04

## Non root user container for SQL Server
- root
- mssql

## Install
<p>docker build -t sqlsrv . <br>
docker run -e "ACCEPT_EULA=Y" -e "Testing1122" -p 1433:1433 --name sql1 -h sql1 -d sqlsrv</p>

## Other way to make sql server container based on Ubuntu
https://dbafromthecold.com/2020/07/17/sql-server-and-docker-compose/

## Change SA Password
<p>docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd 
   -S localhost>br> 
   -U SA -P "YourStrong@Passw0rd"
   -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong@Passw0rd>'"</p>

## bash shell and sqlcmd
<p>docker exec -it sql1 "bash"<br>
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "YourNewStrong@Passw0rd"</p>


## Restore backup
<p>/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "Testing1122"<br>
1> RESTORE DATABASE OD3DSDB_In2Guide<br>
2> FROM DISK = '/var/opt/mssql/backup/OD3DSDB.BAK'<br>
3> WITH MOVE 'OD3DSDB_In2Guide' TO '/var/opt/mssql/data/OD3DSDB.mdf',<br>
4> MOVE 'OD3DSDB_In2Guide_log' TO '/var/opt/mssql/data/OD3DSDB.ldf'<br>
5> go</p?>