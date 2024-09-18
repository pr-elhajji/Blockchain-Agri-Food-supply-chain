 

# Towards and effictive management of Agri-Food supply chain based on Blockchain

# Optimization of Agrifood Supply Chains using Hyperledger Fabric Blockchain Technology
by Mohamed El Hajji1,2, Youssef Es-saady1,3, Mustapha Ait Addi3,  Jilali Antari4
1IRF-SIC Laboratory, Ibnou Zohr University, Agadir, Morocco.
2Regional Center for Education and Training Professions - Souss Massa, Morocco. 
3Polydisciplinary Faculty of Taroudant, Ibnou Zohr University,  Morocco.
4ISIMA Laboratory, Faculty of Taroudant, Ibnou Zohr University,  Morocco.
m.elhajji@crmefsm.ac.ma, y.essaady@uiz.ac.ma, mustapha.aitaddi.00@gmail.com, j.antari@uiz.ac.ma


## Requirements
For mac os,i recommend using homebrew to install prereqs.
Install git,cURL,go,JQ,yarn,node,npm and docker.

## Installation

In order to install the required binaries and docker images for the project run the bootstrap.sh file in its current directory
```bash
  sudo chmod +x bootstrap.sh
```
Execute
```bash
  ./bootstrap.sh
```
To perform network benchmarking move to caliper-benchmarks folder and execute
```bash
  sudo chmod +x install_caliper.sh
  ./install_caliper.sh
```
To install UI packages move to agri_food_UI folder and run
```bash
  yarn
```
## Setup the network
Move to the agri-food directory and start up the network with channel creation
```bash
./network.sh up createChannel
```
To deploy chaincode run the following command
```bash
./network.sh deployCC -ccn basic -ccp ./chaincode/basic -ccl go
```
Now the network is up and it is ready to receive transaction,also the certs and private keys are created using cryptogen tool and located in organizations folder in order to further authentifications in the network.

## Run benchmarks
Read readMe located in caliper-benchmarks folder to understand the folder structure

to run createCommodity benchmarks move to caliper-benchmarks and :
```bash
./caliper.sh -b benchmarks/basicSc/createComConf.yaml -n networks/fabric/farmerNetworkConf.yaml
```

## Run the UI and the server
To run react app move to agri_food_UI and
```bash
yarn dev
```
To run the server
```bash
nodemon server/server.js
```
after that navigate to http://localhost:5173/

for example to connect as farmer use the signed cert at
```bash
organizations/peerOrganizations//farmer.com/users/User1@farmer.com/msp/signcerts/
```
and the private key at
```bash
organizations/peerOrganizations/farmer.com/users/User1@farmer.com/msp/keystore/
```
## Run hyperledger explorer
Hyperledger explorer tool is used to monitor the network (blocks,transactions...)
To run the explorer tool move to agri-food/explorer and
```bash
docker-compose up
```
additional images will be installed
then navigate to http://localhost:8080/ and connect with
exploreradmin/exploreradminpw
## Authors

- [@Mustapha AIT ADDI](https://github.com/artiumrexbellator)
- [@Mohamed EL HAJJI](https://github.com/pr-elhajji)
- [@Youssef ES-SAADY](https://github.com/essaady)

