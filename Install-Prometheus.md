## Download Prometheus Server
```
$ cd /tmp
$ wget -c https://github.com/prometheus/prometheus/releases/download/v2.14.0/prometheus-2.14.0.linux-amd64.tar.gz
```

## Extract Prometheus Server
```
$ tar -xzvf prometheus-2.14.0.linux-amd64.tar.gz
```

## Move to /opt directory
```
$ sudo mv prometheus-2.14.0.linux-amd64 /opt/prometheus-server
$ cd /opt/prometheus-server
```

## Edit configuration file 
```
$ sudo vim prometheus.yml
```

## Configure Systemd Service for Prometheus Service
```
$ cat << EOF | sudo tee -a /etc/systemd/system/prometheus.service
[Unit]
Description=Prometheus Server
 
[Service]
User=root
ExecStart=/opt/prometheus-server/prometheus --config.file=/opt/prometheus-server/prometheus.yml --web.external-url=http://ip_server:9090/

[Install]
WantedBy=default.target
EOF
```

## Activate prometheus service
```
$ sudo systemctl daemon-reload
$ sudo systemctl enable prometheus.service
$ sudo systemctl start prometheus.service
```
## Verification prometheus service
```
$ sudo systemctl status prometheus.service
```
