2. Install node exporter on another machine than the server
- Add that machine target to server configuration
- Share screenshot from status->targets to show the available nodes
- Share configuration of node exporter & prometheus server
Steps:<br/>
Download node exporter<br/>
```
curl -LO https://github.com/prometheus/node_exporter/releases/download/v1.3.0/node_exporter-1.3.0.linux-amd64.tar.gz
```
![install](https://user-images.githubusercontent.com/53372486/144643141-1d3b107f-bcaf-4ad2-964f-f1f0ab76a57e.png)<br/>

Unzip node expoter<br/>
```
tar xvfz node_exporter-1.3.0.linux-amd64.tar.gz
```
![unzip](https://user-images.githubusercontent.com/53372486/144643157-23f049f0-8d84-490f-95f2-c82c0bcb93cb.png)<br/>

Change dir<br/>
```
cd node_exporter-1.3.0.linux-amd64
```
Run node exporter<br/>
```
./node_exporter
```
![run node exporter](https://user-images.githubusercontent.com/53372486/144643152-b20a88ad-d628-4858-81f0-831a7c13bbb0.png)<br/>

Check ip <br/>
```
ip a
```
![ip](https://user-images.githubusercontent.com/53372486/144643144-f03cc26b-62f5-4193-9568-408e50ec523c.png)<br/>

Open in webbrowser <br/>
```
http://192.168.141.129:9100/
```
![node web](https://user-images.githubusercontent.com/53372486/144643151-11ec0573-41f5-4f26-aab5-95d33be694e4.png)<br/>

Click on metrics<br/>

![matric](https://user-images.githubusercontent.com/53372486/144643148-4e62be6c-283e-4b68-a5d9-8ec9c0d4261f.png)<br/>

Now,open prometheus.yml file on vm1
```
sudo nano prometheus.yml
```
add below line in prometheus.yml 
```
  - job_name: "node_exporter"
    static_configs:
      - targets: ["192.168.141.129:9100"]
```
![conf](https://user-images.githubusercontent.com/53372486/144643134-26eaaaac-2f62-470f-b263-d8fb90831aa0.png)<br/>

Open prometheus in web browser and Give auth<br/>

Target <br/>
click on status > targets <br/>

![web](https://user-images.githubusercontent.com/53372486/144643161-b47ed7a6-e483-42c3-a752-63f5f77445a3.png)<br/>







