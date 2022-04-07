# Creating an OpenMRS 3.x distribution for iSantePlus: A Tutorial

In this tutorial, we will:

 - build a 3.x distribution from scratch 
 - add some basic modules to the distribution
 - run the distribution as a standalone application 
 - connect with a running iSantePlus instance


## Useful Links
https://wiki.openmrs.org/display/projects/3.x+Implementer+Documentation#id-3.xImplementerDocumentation-ExampleDistribution

http://o3-dev.docs.openmrs.org/#/main/distribution

## Setup and Prereqs

1. Install Docker: https://docs.docker.com/engine/install/ubuntu/
2. Clone this repository: `git clone https://github.com/IsantePlus/iSantePlus3x.git`

## Instructions

### Create a folder for the repository
```sh
mkdir iSantePlus3x
cd iSantePlus3x
```

### Build App Shell
This command uses the `openmrs` Node.js package that can be found here: https://www.npmjs.com/package/openmrs (published package) and https://github.com/openmrs/openmrs-esm-core/tree/master/packages/tooling/openmrs (code)

```sh
npx openmrs build --spa-path /isanteplus --api-url https://isanteplus.sedish-haiti.org/openmrs --config-url config.json --importmap importmap.json
```

```sh
npx openmrs build --config-url config.json --importmap importmap.json
```

### Create an Import Map using Interactive Tool
```sh
npx openmrs assemble --config ./build-config.json --mode config  
```

### Create an empty Config File
`config.json`
```json
{}
```

### Boot up iSantePlus
```sh
docker-compose up -d 
```