# BaSyx Shell Playground Project

This project contains a collection of containers including:

- BaSyx components (registry, repository)
- MQTT Eventing
- AAS Web UI

By default it will also contain a set of example shells.

# How to use
First of all, clone this repository.

## First use
It is recommended to first pull the needed docker images using

```bash
docker compose pull
```

This will download all the images needed and might take a while.

## Starting up
Before using the playground, make sure to add your own shells to the `aas` folder (if you have any - one example is in there already)
After all images are pulled, start the playground by using

```bash
docker compose up -d
```

> The `-d` means that it will run in `detached` mode. If you want to see all the terminal output you can just remove `-d`.

To stop the playground use

```bash
docker compose down
```

> If not in detached mode you might only need to hit `Ctrl` + `C` to stop

## Checking current state

To check the current state of all containers, use 

```bash
docker ps -a
```

which will generate an overview of currently running containers, similar to this:

```
CONTAINER ID   IMAGE                                                   COMMAND                  CREATED      STATUS                   PORTS                                                                                  NAMES
7e4b79edbd12   eclipsebasyx/aas-gui:v2-241006                          "/usr/src/app/entryp…"   2 days ago   Up 2 hours               80/tcp, 0.0.0.0:3000->3000/tcp, :::3000->3000/tcp                                      aas-ui
320058d87bf7   eclipsebasyx/aas-environment:2.0.0-SNAPSHOT             "java -jar basyxExec…"   2 days ago   Up 2 hours (unhealthy)   0.0.0.0:8081->8081/tcp, :::8081->8081/tcp                                              aas-env
427cfef6d702   eclipsebasyx/aas-registry-log-mem:2.0.0-SNAPSHOT        "java -Djava.securit…"   2 days ago   Up 2 hours (healthy)     0.0.0.0:8082->8080/tcp, [::]:8082->8080/tcp                                            aas-registry
8ec91f895afc   eclipsebasyx/submodel-registry-log-mem:2.0.0-SNAPSHOT   "java -Djava.securit…"   2 days ago   Up 2 hours (healthy)     0.0.0.0:8083->8080/tcp, [::]:8083->8080/tcp                                            sm-registry
703896a69763   eclipse-mosquitto:2.0.15                                "/docker-entrypoint.…"   2 days ago   Up 2 hours (healthy)     0.0.0.0:1883->1883/tcp, :::1883->1883/tcp, 0.0.0.0:9001->9001/tcp, :::9001->9001/tcp   mosquitto

```


To check the logs of a single container, use

```bash
docker logs -f --tail 1000 7e4b
```

where `7e4b` needs to be replaced by the first few characters of the `CONTAINER ID` from the container which logs should be printed. In this example, the last 1000 lines of the logs of the aas-gui would be printed.

### Add your own shells

To add your own shells you need to place them within the `/aas` folder.
From what I can tell they have to be an `Environment` and should be in `.json` format.

# Where to find

| What                         | Where                                         |
| ---------------------------- | --------------------------------------------- |
| BaSyx Repository API         | `http://localhost:8081/`                      |
| BaSyx Repository Docs        | `http://localhost:8081/swagger-ui/index.html` |
| BaSyx AAS Registry API       | `http://localhost:8082/`                      |
| BaSyx AAS Registry Docs      | `http://localhost:8082/swagger-ui/index.html` |
| BaSyx Submodel Registry API  | `http://localhost:8083/`                      |
| BaSyx Submodel Registry Docs | `http://localhost:8083/swagger-ui/index.html` |
| AAS Web UI | `http://localhost:3000`

# Credits

This project is based on a configuration made with the [BaSyx Starter Kit](https://basyx.org/)
