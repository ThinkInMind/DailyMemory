## This is just a test

fjifjijfi 

## Miss you so

```
logstash:
    image: docker.elastic.co/logstash/logstash:5.6.11
    ports:
      - 5044:5044
    networks:
      - d1m_cloud_overlay
    volumes:
      - ~/docker-swarm/elk/logstash/config/filebeat.conf:/usr/share/logstash/config/conf.d/logstash.conf
      - ~/docker-swarm/elk/logstash/config/logstash.yml:/usr/share/logstash/config/logstash.yml
    command: -f /usr/share/logstash/config/conf.d/
    deploy:
      mode: replicated
      labels: [APP = els_logstash]
      placement:
        constraints:
          [node.role == worker]




  filebeat-138:
    image: docker.elastic.co/beats/filebeat:5.6.11
    networks:
      - d1m_cloud_overlay
    deploy:
      mode: replicated
      placement:
        constraints:
          - node.hostname==wechat138
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - /data/log:/var/log
      - /data/log:/data/log
      - /data/etc/filebeat/filebeat.yml:/usr/share/filebeat/filebeat.yml
  filebeat-130:
    image: docker.elastic.co/beats/filebeat:5.6.11
    networks:
      - d1m_cloud_overlay
    deploy:
      mode: replicated
      placement:
        constraints:
          - node.hostname==wechat130
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - /data/log:/var/log
      - /data/log:/data/log
      - /data/etc/filebeat/filebeat.yml:/usr/share/filebeat/filebeat.yml
```















































