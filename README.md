# frappe14-bench


```shell
sudo docker exec -it frappe-bench /bin/bash
bench init --skip-redis-config-generation frappe-bench

cd frappe-bench
bench new-app  demo-app

```
cd sites

set Redis the values in common_site_config.json.

replace all content by 

```shell
{
"background_workers": 1,
 "file_watcher_port": 6787,
 "frappe_user": "frappe",
 "gunicorn_workers": 3,
 "live_reload": true,
 "rebase_on_pull": false,
 "redis_cache": "redis://redis-cache:6379",
 "redis_queue": "redis://redis-queue:6379",
 "redis_socketio": "redis://redis-socketio:6379",
 "restart_supervisor_on_update": false,
 "restart_systemd_on_update": false,
 "serve_default_site": true,
 "shallow_clone": true,
 "socketio_port": 9000,
 "use_redis_auth": false,
 "webserver_port": 8000
}



```
Setup site to database server.

For PostgreSQL database 
```shell

bench new-site mysite.localhost --db-type postgres --db-host pgsql --db-root-username postgres --db-root-password frappe --db-name frappe   --admin-password admin 

```

bench --site mysite.localhost  reinstall  --db-root-username postgres --db-root-password frappe --db-name frappe   --admin-password admin 


or 

For MariaDB database (Recommend)

bench new-site mysite.localhost --db-host [custom-db-host-ip] --db-port [custom-db-port] --db-root-password frappe --db-name frappe --admin-password admin

```shell
 bench new-site mysite.localhost --db-host mariadb  --db-root-password rootdocker --db-name frappe --admin-password admin

```

If your db server config not match please rollback and try again.
If sites/mysite.localhost exist, please delete before bench new-site again.


Example apps, you can download by bench command.

- payments
- healthcare
- payments
- erpnext
- hrms
- lms
- frappedesk
- insights

bench get-app healthcare payments erpnext

bench --site mysite.localhost install-app frappe erpnext

folder sites/mysite.localhost is created.

in sites folder create file currentsite.txt by your sitename

[ currentsite.txt ]

mysite.localhost

or use bench command

```
bench use mysite.localhost
```

```
bench start  
```
You can access by browser at port 8000

or  

```
bench serve  --port 8001
```
You can access by browser at port 8001

```
sudo lsof -nP -iTCP -sTCP:LISTEN | grep 8001
```
Inspect running process 

username : administrator

password : admin

FAQ : 
1) After docker-compose down, frappe can't connect because internal docker ip was changed.
new ip is frappe@(new ip) in error message.

Solution is connect mariadb server and change ip in tables 

global_priv(host)

db(host)

and run "flush privileges" command
