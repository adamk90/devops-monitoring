# DevOps - Monitoring

## Preparation
1. Fork the https://github.com/szatmari/devops-monitoring project
2. Start a "DevOps - Docker, Kubernetes" in the BME cloud
3. Expose ports 8088, 9090, 9100, 3000, 9104, 9106
4. If needed: tune the /etc/resolv.conf and add 8.8.8.8 as nameserver
5. Clone the repository to the cloud VM

## SpringBoot MicroMeter
1. Add the MicroMeter dependencies to the build.gradle
 ```
    compile "org.springframework.boot:spring-boot-starter-actuator"
    compile "io.micrometer:micrometer-core"
    compile "io.micrometer:micrometer-registry-prometheus"
```
Add the MicroMeter configuration to ```src/main/resources/application.properties```

```
#Metrics related configurations
management.endpoint.metrics.enabled=true
management.endpoints.web.exposure.include=*
management.endpoint.prometheus.enabled=true
management.metrics.export.prometheus.enabled=true
```

1. Start the webapp
```bash
docker-compose up -d webapp
```

Test the endpoints: http://host:port/actuator

1. Test the Prometheus service
```bash
docker-compose up -d prometheus
```

1. Test the Graphana service
```bash
docker-compose up -d graphana
```

1. Test the other metric exporters
```bash
docker-compose up -d
```
 

