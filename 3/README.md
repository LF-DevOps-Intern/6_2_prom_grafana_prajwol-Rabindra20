3. Install grafana server on same server as prometheus 
- Add prometheus data source to grafana, should be connected through basic auth
- Screenshot of working data source config
- Import & apply dashboard for node_exporter
- Screenshot of dashboard of nodes with live metrics shown.<br/>
Step:<br/>
To install the latest OSS release:<br/>
Install the apt-transport-https package on Debian before proceeding<br/>
```
sudo apt-get install -y apt-transport-https
```
![transport](https://user-images.githubusercontent.com/53372486/144652086-45fda948-8684-4d5f-83d6-e236701face4.png)<br/>
```
sudo apt-get install -y software-properties-common wget
```
![wget](https://user-images.githubusercontent.com/53372486/144652090-deaef5c5-96c8-4964-9b92-dc175b38f81f.png)<br/>

Download and install the Public Signing Key<br/>
```
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```
![wget key](https://user-images.githubusercontent.com/53372486/144652088-682c19a7-f2b6-455b-af9c-aef2b3483c4a.png)<br/>

Add this repository for stable releases:<br/>
```
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```
![stable](https://user-images.githubusercontent.com/53372486/144652083-19439396-66ec-4087-9b65-8bfb168887f4.png)<br/>

Update apt-get<br/>
```
sudo apt-get update
```
![apt](https://user-images.githubusercontent.com/53372486/144652042-06b3b32d-5ab2-4310-a68b-f3028afacfdd.png)<br/>

install grafana<br/>
```
sudo apt-get install grafana
```
![install](https://user-images.githubusercontent.com/53372486/144652072-c1790e04-0fb4-458f-9943-0806e670dae5.png)<br/>

Start grafana<br/>
```
sudo systemctl start grafana-server
```
Check status<br/>
```
sudo systemctl status grafana-server
```
![status](https://user-images.githubusercontent.com/53372486/144652084-ab3bb219-1638-4f0e-b7d1-7fdb0219b3fe.png)<br/>

Open grafana in webbrowser<br/>
Login with default username=admin and password=admin<br/>

![login](https://user-images.githubusercontent.com/53372486/144652075-3d72f4cf-ddf8-4bcf-94bb-b102254d1710.png)<br/>

After login change password<br/>

![newpassword](https://user-images.githubusercontent.com/53372486/144652077-977df278-039d-460a-bf06-8c9672791dda.png)<br/>

Now,After click on submit button it will redirect to dashbord<br/>

![dashbord](https://user-images.githubusercontent.com/53372486/144652049-c30204b9-25ad-49fa-ba4c-3d2f50f6bb92.png)<br/>

Click on create datasource and select promtheus<br/>

![add datasource](https://user-images.githubusercontent.com/53372486/144652038-5e66b8d8-356c-481d-972f-4523be277b4f.png)<br/>

Enter name,HTTP and auth and save it.<br/>

![confi data](https://user-images.githubusercontent.com/53372486/144654581-e69c9bce-1e16-411f-ad2e-8f77b9061f43.png)<br/>

Check datasource <br/>
Click on setting > datasource<br/>
![datasourceadd](https://user-images.githubusercontent.com/53372486/144652054-f921c755-50ee-4b94-bcbb-6eadc9ef7a0b.png)<br/>

Take dashbord id from https://grafana.com/grafana/dashboards/1860<br/>

![id](https://user-images.githubusercontent.com/53372486/144652057-fde35ad9-6150-44b0-a9bd-dd9f8d780acc.png)<br/>

Now import id,enter dashbordid and click on load<br/>

![import](https://user-images.githubusercontent.com/53372486/144652063-901b322b-9613-414a-84db-4710d46ca8c2.png)<br/>

After clcik on load it will redirct to importing dashbord page <br/>

![importga](https://user-images.githubusercontent.com/53372486/144652068-82a2730e-86de-46d7-8430-ab6423d4608b.png)<br/>

Dashbord of node exporter<br/>

![nodeexporter](https://user-images.githubusercontent.com/53372486/144652081-9e1df118-677f-4160-acbc-47500aaa814d.png)





