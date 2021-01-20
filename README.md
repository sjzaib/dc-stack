# dc-stack
docker compose stacks

# How to run

Clone this repo 

```bash
git clone <this repo>
```

build app image

```bash
cd app
docker build -t html-server:1.0 . 
```

build load balancer
```bash
cd load-balancer
docker build -t load-balancer:1.0 .  
```

up this stack using docker-compose
```bash
cd ..
docker-compose up
```

testing - in a separate terminal run
```bash
curl localhost:8080
```

and check docker compose logs or check individual container logs for each app container e.g. 

```bash
docker logs -f <container-id>
```

## Sample Run 

```bash
sjzaib :: dc-stack » docker-compose up
Starting stack_mysql_1 ... done
Starting stack_app_server2_1 ... done
Starting stack_app_server1_1 ... done
Starting stack_nginx_1       ... done
Attaching to stack_mysql_1, stack_app_server1_1, stack_app_server2_1, stack_nginx_1
mysql_1        | 2021-01-20T12:24:47.693399Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.22-13) starting as process 1
app_server2_1  | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
app_server2_1  | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
app_server1_1  | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
app_server1_1  | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
mysql_1        | 2021-01-20T12:24:47.700682Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
app_server1_1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
mysql_1        | 2021-01-20T12:24:47.834295Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
app_server1_1  | 10-listen-on-ipv6-by-default.sh: info: IPv6 listen already enabled
mysql_1        | 2021-01-20T12:24:47.932608Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-address: '::' port: 33060, socket: /var/lib/mysql/mysqlx.sock
app_server1_1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
mysql_1        | 2021-01-20T12:24:47.968019Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
app_server1_1  | /docker-entrypoint.sh: Configuration complete; ready for start up
mysql_1        | 2021-01-20T12:24:47.968198Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
app_server2_1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
app_server2_1  | 10-listen-on-ipv6-by-default.sh: info: IPv6 listen already enabled
mysql_1        | 2021-01-20T12:24:47.985807Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.0.22-13'  socket: '/var/lib/mysql/mysql.sock'  port: 3306  Percona Server (GPL), Release 13, Revision 6f7822f.
app_server2_1  | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
app_server2_1  | /docker-entrypoint.sh: Configuration complete; ready for start up
nginx_1        | /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
nginx_1        | /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
nginx_1        | /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
nginx_1        | 10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
nginx_1        | 10-listen-on-ipv6-by-default.sh: info: /etc/nginx/conf.d/default.conf differs from the packaged version
nginx_1        | /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
nginx_1        | /docker-entrypoint.sh: Configuration complete; ready for start up
app_server1_1  | 172.19.0.1 - - [20/Jan/2021:12:25:30 +0000] "GET / HTTP/1.0" 200 13 "-" "curl/7.58.0" "-"
nginx_1        | 172.19.0.1 - - [20/Jan/2021:12:25:30 +0000] "GET / HTTP/1.1" 200 13 "-" "curl/7.58.0" "-"
app_server2_1  | 172.19.0.1 - - [20/Jan/2021:12:25:32 +0000] "GET / HTTP/1.0" 200 13 "-" "curl/7.58.0" "-"
nginx_1        | 172.19.0.1 - - [20/Jan/2021:12:25:32 +0000] "GET / HTTP/1.1" 200 13 "-" "curl/7.58.0" "-"

```