# ShellScape Playground Project
This project contains a collection of containers including: 
 - BaSyx components (registry, repository)
 - MQTT Eventing
 - AAS Web UI

By default it will also contain a set of example shells from the truck.

# How to use
## First use
Before using the playground, make sure to clone the repository and add your own shells to the `aas` folder.
Afterwards, pull the needed docker images using 

```bash
docker compose pull
```

This will download all the images needed and might take a while. 

## Starting up
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

# Add your own shells
To add your own shells you need to place them within the `/aas` folder. 
From what I can tell they have to be an `Environment` and should be in `.json` format.