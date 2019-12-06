## Download the Grafana GPG key and pipe the output to apt-key
```
$ wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```

## Add the Grafana repository
```
$ sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
```

## Refresh APT cache to updatepackage lists
```$ sudo apt update
```
## Install grafana
```
$ sudo apt install grafana
```

### Activate grafana service
```
$ sudo systemctl start grafana-server
```

## Verify that Grafana is running
```
$ sudo systemctl status grafana-server
```

## enable the service to automatically start Grafana on boot:
```
$ sudo systemctl enable grafana-server
```
