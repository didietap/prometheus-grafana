## Download the latest node exporter package.
```
$ cd /tmp
$ curl -LO https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz
```

## Unpack the tarball.
```
$ tar -xvf node_exporter-0.18.1.linux-amd64.tar.gz
```

## Move the node export binary to /usr/local/bin
```
$ sudo mv node_exporter-0.18.1.linux-amd64/node_exporter /usr/local/bin/
```

### Create a node_exporter service file under systemd.
```
$ cat << EOF | sudo tee -a /etc/systemd/system/node_exporter.service
[Unit]
Description=Node Exporter
After=network.target

[Service]
User=root
Group=root
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target
EOF
```

## Reload the system daemon and start the node exporter service.
```
$ sudo systemctl daemon-reload
$ sudo systemctl start node_exporter
```

## Check the node exporter status.
```
$ sudo systemctl status node_exporter
```

## Enable the node exporter service to the system startup.
```
$ sudo systemctl enable node_exporter
```
