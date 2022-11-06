# frappe14-bench


```shell
sudo docker exec -it frappe-bench /bin/bash
bench init --skip-redis-config-generation frappe-bench

cd frappe-bench
bench new-app  demo-app
bench new-site mysite.localhost --db-type postgres --db-host pgsql --db-root-username postgres --db-root-password frappe --db-name frappe   --admin-password admin 

```

bench --site mysite.localhost  reinstall  --db-root-username postgres --db-root-password frappe --db-name frappe   --admin-password admin 



bench get-app healthcare.payments erpnext

bench --site mysite.localhost install-app frappe erpnext

Edit  currentsite.txt by your sitename

bench serve  --port 8001

sudo lsof -nP -iTCP -sTCP:LISTEN | grep 8001
