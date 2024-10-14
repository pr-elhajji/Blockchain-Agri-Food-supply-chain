 
<div align="center">

# ⚡️Optimization of Agrifood Supply Chains using Hyperledger Fabric Blockchain Technologyw⚡️

[[Paper]](https://www.sciencedirect.com/science/article/pii/S0168169924008949)

</div>


# Abstruct 
Blockchain technology shows significant promise for addressing challenges within the agri-food supply chain. However, the effective application of blockchain platforms in this context is still an area of research. This study proposes a blockchain-based system that uses Hyperledger Fabric to manage agri-food supply chains based builder design patterns. The main focus is on preserving relationships, authorizations, and accurate traceability of food products throughout the supply chain. The system takes into account the various stakeholders involved in the food supply chain to ensure coordination and efficiency. It integrates multiple security mechanisms to enhance security and enforce adherence to chaincode, preventing unauthorised access to critical data or operations. Additionally, ownership and validity checks are incorporated for agreement issuance and asset generation, providing credentials for the legitimacy of linked agreements and organisational authorisation. The proposed system improves the security and integrity of the supply chain by using one-time agreements, which mitigates the risk of replay attacks or malicious activity. A web platform has been proposed to give users real-time visibility of a package’s movement through the supply chain. This enables access to a detailed chronology of the product’s movement and delivery steps by scanning the package’s QR code. The proposed system is evaluated for performance using the Caliper tool to measure network throughput and transaction latency, which demonstrates the feasibility and efficiency of Hyperledger Fabric in optimising agri-food supply chains.

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


# Citation
Consider giving this repository a star and cite Pyramid Flow in your publications if it helps your research.
```
@article{el2024optimization,
  title={Optimization of agrifood supply chains using Hyperledger Fabric blockchain technology},
  author={El Hajji, Mohamed and Es-saady, Youssef and Addi, Mustapha Ait and Antari, Jilali},
  journal={Computers and Electronics in Agriculture},
  volume={227},
  pages={109503},
  year={2024},
  publisher={Elsevier}
}
```
## Authors
- [@Mustapha AIT ADDI](https://github.com/artiumrexbellator) • [@Mohamed EL HAJJI](https://github.com/pr-elhajji) • [@Youssef ES-SAADY](https://github.com/essaady)

