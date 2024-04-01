# Deploy Fuel Node
what is the fuel network project? Fuel initially describes itself as the first Optimistic rollup for Ethereum launched in 2020. Since then the project has come a long way and is a modular execution layer offering smart contracts on Ethereum using the UTXO model.

## Prerequisites
Linux Ubuntu 22.04 LTS
### Minum Requirements:
CPU: 2 Cores
RAM: 4 GB
Storage: 30 GB

### Recommended Requirements:
CPU: 8 Cores
RAM: 12 GB
Storage: 100 GB

For running a Fuel node, a VPS with reliable performance such as Contabo VPS 2 is recommended.

## Ethereum API Key for Fuel Node
Before installing a Fuel node, you need an Ethereum Sepolia Testnet API key from Alchemy:

## Sign up and verify your account at Alchemy.
Create a new app, name it, provide a description, and select Ethereum Sepolia as the network.
Access your API keys under "View Key" and copy your HTTPS key. It will be required during the Ansible script execution.

## Installing Dependencies
Update your system and install Ansible, Git, and Expect:

```
sudo apt update && sudo apt upgrade -y
sudo apt install ansible git expect -y
```

##  Downloading the Project
Clone the repository to access the Ansible playbook and all necessary files:

```
git clone https://github.com/yourusername/deploy-node-fuel.git
cd deploy-node-fuel
```

##  Executing the Playbook
Launch the installation with the following command, which prompts you for the action to perform (install or remove), the service name for the Fuel node, and your Alchemy Ethereum RPC endpoint:

```
ansible-playbook fuel-node.yml -e node_action="install"
```
Ensure you run the playbook with root privileges.

##  Managing the Fuel Node Service

### Starting Services

After initialization, you can start the Fuel node service with:

```
sudo systemctl start fuel-node
```

## Viewing Logs
To monitor your Fuel node's operation:

```
journalctl -u fuel-node -f -o cat
```

### Stopping Services
Stop the Fuel node service with:

```
sudo systemctl stop fuel-node
```

### Removing the Node
To remove the Fuel node, simply run the playbook again and choose the remove option:

```
ansible-playbook setup_or_remove_fuel_node.yml -e node_action="remove"
```

