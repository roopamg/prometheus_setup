### prometheus_setup

### prometheus_setup/Prometheus/tasks/main.yml

### install_prometheus.yml

1. In this playbook, prometheus is downloaded from the repository in the `/root` folder
2. Untar the file in `/root` folder
3. Create Prometheus as a service by copying the content in `/usr/local/bin` folder and service file in `/etc/systemd/system` folder
4. Reload the system daemon 
5. Now, prometheus is installed and running in your system. Access the same in your browser `<IP:9090>`. Make sure the port `9090` is open

### install_node_exporter.yml

1. In this playbook, prometheus node exporter is downloaded from the repository in the `/root` folder
2. Untar the file in `/root` folder
3. Create prometheus node exporter as a service by copying the content in `/usr/local/bin` folder and service file in `/etc/systemd/system` folder
4. Reload the system daemon
5. Now, prometheus node exporter is installed and running in your system. Access the same in your browser `<IP:9100>`. Make sure the port `9100` is open

###  config_prometheus.yml

1. Insert reference of node-exporter as target in `prometheus.yml` file 
2. Copy the rules file in `/usr/local/bin/prometheus` folder
3. Check the syntax of `prometheus_rules.yml` using prom tool
4. Insert reference of `prometheus_rules.yml` file in `prometheus.yml`

### install_alertmanager.yml

1. Download Alert manager in `/root` folder
2. Untar the file and copy it to `/root` folder
3. Copy the content of the `/alertmanager-0.19.0.linux-amd64` and paste it to `/usr/local/bin/alertmanager`
4. Copy the service file(alertmanager.service) from the local system and paste it `/etc/systemd/system` folder
5. Reload the system daemon

### config_alertmanager.yml

1. Insert alert rules in `/usr/local/bin/prometheus/prometheus_rules.yml` 
2. Check the syntax of `prometheus_rule.yml` file using promtool
3. Print the output of the promtool

### email_config.yml

1. Remove the `alertmanager.yml` file
2. Copy the config file of alertmanager(alertmanager.yml) from the local system and paste it to `/usr/local/bin/alertmanager` folder. Change the parameters in the file like email address of sender and reciever.
3. Check the syntax of the config file using amtool
4. Enable alertmanager as target in `/usr/local/bin/promtheus/promentheus.yml` file
5. Now, the email configurations is also set in the `prometheus.yml file`
5. As the alert is set on Instancedown within 10s. Alert will be sent to the desired the mailid after 10 seconds if any Instance which is configured in the prometheus file is down
