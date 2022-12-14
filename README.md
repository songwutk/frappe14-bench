# frappe14-bench


```shell
sudo docker exec -it frappe-bench /bin/bash
bench init --skip-redis-config-generation frappe-bench

cd frappe-bench
bench new-app  demo-app

```

set Redis the values in common_site_config.json.

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

For PostgreSQL database
```shell

bench new-site mysite.localhost --db-type postgres --db-host pgsql --db-root-username postgres --db-root-password frappe --db-name frappe   --admin-password admin 

```

bench --site mysite.localhost  reinstall  --db-root-username postgres --db-root-password frappe --db-name frappe   --admin-password admin 


or 

For MariaDB database
```shell
 bench new-site mysite.localhost --db-host [custom-db-host-ip] --db-port [custom-db-port] --db-root-password frappe --db-name frappe --admin-password admin
```

Example apps

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

Edit  currentsite.txt by your sitename


bench serve  --port 8001

sudo lsof -nP -iTCP -sTCP:LISTEN | grep 8001
