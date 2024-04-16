# Install WSL (Windows Subsystem for Linux) on Windows   

## Step 1: Enable the Windows Subsystem for Linux
Abra o PowerShell como administrador e execute:
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

## Step 2 — Enable the Virtual Machine feature
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

## Passo 3— Baixar o pacote de atualização do kernel do Linux
Clique neste https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi para fazer o download do pacote de atualização do kernel do Linux do WSL 2 para computadores x64. Execute o pacote de atualização baixado e finalize a instalação.

## Passo 4 — Definir o WSL 2 como a sua versão padrão
wsl --set-default-version 2

## Restart wsl
wsl --shutdown

## List installed distros
wsl -l -v

## Install distro
wsl install -d {distro}

## List distros to install
wsl --list --online

# Install k3d

wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | TAG=v5.0.0 bash

## Create cluster with k3d
k3d cluster create mycluster
# Delete cluster with k3d
k3d cluster delete mycluster
# Start cluster with k3d
k3d cluster start mycluster
# Stop cluster with k3d
k3d cluster stop mycluster
# List k3d clusters
k3d cluster list
# Import docker image to k3d cluster
k3d image import my-image:1.0 -c mycluster

# instalar o kubectl
sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2 curl
    curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
    echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
    sudo apt-get update
   sudo apt-get install -y kubectl

# instalar o docker

# Instale os pré-requisitos:
sudo apt update && sudo apt upgrade
sudo apt remove docker docker-engine docker.io containerd runc
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

# Adicione o repositório do Docker na lista de sources do Ubuntu:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Instale o Docker Engine
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

# Dê permissão para rodar o Docker com seu usuário corrente:
sudo usermod -aG docker $USER

# Inicie o serviço do Docker
sudo service docker start

# caso dê erro de Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
sudo update-alternatives --config iptables
escolher a opção 1

# caso dê erro de Got permission denied while trying to connect to the Docker daemon socket at
sudo chmod 666 /var/run/docker.sock