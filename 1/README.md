1. Install Prometheus Server
- Configuration basic authentication username/password
- Screenhot of login prompt while trying to access prometheus
- Screenshot of prometheus dashboard
Steps:<br/>
Download promethus
```
curl -LO https://github.com/prometheus/prometheus/releases/download/v2.31.1/prometheus-2.31.1.linux-amd64.tar.gz<br/>
```
![install](https://user-images.githubusercontent.com/53372486/144557627-b9ff723c-a02d-40de-be66-91859d79a3d4.png)<br/>

Unzip Prometheus<br/>
```
tar xvf prometheus-2.31.1.linux-amd64.tar.gz
```
![unzip](https://user-images.githubusercontent.com/53372486/144557620-7bd3a842-2e71-4097-b1b7-a130f9906ebc.png)<br/>

Change dir
```
cd prometheus-2.31.1.linux-amd64.tar.gz
```
Add Prometheus services so we can start with systemctl command<br/>
change dir<br/>
```
cd /etc/systemd/system
```
Create prometheus.service <br/>
```
sudo nano prometheus.service
```
Add below code<br/>
```
[Unit]
Description=prometheus service

[Service]
ExecStart=/home/rabindra/prometheus-2.31.1.linux-amd64/prometheus \
           --config.file=/home/rabindra/prometheus-2.31.1.linux-amd64/promethe> \

Restart=always

[Install]
WantedBy=multi-user.target
```
![service](https://user-images.githubusercontent.com/53372486/144557638-a0e3915f-4b32-43d9-ab9f-7651bae414f3.png)<br/>

Reload daemon <br/>
```
sudo systemctl daemon-reload
```
Restart prometheus<br/>
```
sudo systemctl restart prometheus
```
Check status<br/>
```
systemctl status prometheus
```
![status](https://user-images.githubusercontent.com/53372486/144557642-b60ec205-d085-4770-b9af-c94d07a3a711.png)<br/>

Create hash password with python <br/>
```
import bcrypt
hashed_password = bcrypt.hashpw("Rabindra@1".encode("utf-8"), bcrypt.gensalt())
hashed_password.decode()
```

![bcrypt](https://user-images.githubusercontent.com/53372486/144557625-c6c4f6c2-a475-4934-9ff8-326bbb987e06.png)<br/>

Change dir<br/>
```
cd /home/rabindra/prometheus-2.31.1.linux-amd64
```
Creating web.yml<br/>
```
sudo nano web.yml
```
Add below linin web.yml<br/>
```
basic_auth_users:
    admin: $2b$12$WMv749yLoFy2An6pLETYAea4GN2Qc1iH9kJVw3cKUsXY8qEsApBx.
```
Check web.yml<br/>
```
promtool check web-config web.yml 
```
![promtool](https://user-images.githubusercontent.com/53372486/144557635-b5d781c8-4f29-4788-b752-757943fddd9d.png)<br/>

Launching Prometheus<br/>
```
prometheus --web.config.file=web.yml
```
OR add below line in service file and restart service <br/>
```
--web.config.file=/home/rabindra/prometheus-2.31.1.linux-amd64/web.yml> \ 
```
Restart and check status <br/>
```
sudo systemctl daemon-reload
sudo systemctl restart prometheus
systemctl status prometheus
```
![status](https://user-images.githubusercontent.com/53372486/144557642-b60ec205-d085-4770-b9af-c94d07a3a711.png)<br/>

Display with auth<br/>
```
localhost:9090
```
![login](https://user-images.githubusercontent.com/53372486/144557632-36219631-4cf1-429d-92a2-47deec203899.png)<br/>

Dashbord<br/>

![dashbord](https://user-images.githubusercontent.com/53372486/144558327-81e83058-c4a6-47f8-a9fe-fe187d9e40cc.png)




