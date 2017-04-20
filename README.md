# elk

elasticsearch kibana logstash (beats)

```
# Start elasticsearch, kibana, and logstash
docker-compose up

# Ship elasticsearch logs to elasticsearch
docker logs -f  elasticsearch | ./filebeat-5.3.0-darwin-x86_64/filebeat -c filebeat.elasticsearch.yml -e

# Ship kibana logs to elasticsearch
docker logs -f kibana | ./filebeat-5.3.0-darwin-x86_64/filebeat -c filebeat.kibana.yml -e

# The rest of these commands are run from within the beat's subdir. For the ones which need root -- packetbeat and metricbeat -- you will need to chown the config file first as well...

sudo ./packetbeat -c packetbeat.yml -e
sudo ./metricbeat  -c metricbeat.yml -e
./heartbeat  -c heartbeat.yml -e
./filebeat -c filebeat.yml -e
```

Then browse to [http://localhost:5601/](http://localhost:5601/)
