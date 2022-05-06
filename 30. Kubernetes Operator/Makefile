install-golang:
	curl -OL https://golang.org/dl/go1.16.3.linux-amd64.tar.gz
	sudo tar -C /usr/local -xvf go1.16.3.linux-amd64.tar.gz
	export GOPATH=/usr/local/go

install-kubectl:
	curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl` 
	chmod +x ./kubectl
	sudo mv ./kubectl /usr/local/bin/kubectl

install-docker:
	sudo apt-get update && sudo apt-get install docker.io -y
	sudo groupadd docker
	sudo usermod -aG docker $USER
	newgrp docker

install-minikube:
	curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
	sudo apt install conntrack

install-operator-sdk:
	export ARCH=$(case $(uname -m) in x86_64) echo -n amd64 ;; aarch64) echo -n arm64 ;; *) echo -n $(uname -m) ;; esac)
	export OS=$(uname | awk '{print tolower($0)}')
	export OPERATOR_SDK_DL_URL=https://github.com/operator-framework/operator-sdk/releases/download/v1.11.0
	curl -LO ${OPERATOR_SDK_DL_URL}/operator-sdk_${OS}_${ARCH}
	chmod +x operator-sdk_linux_amd64 && sudo mv operator-sdk_linux_amd64 /usr/local/bin/operator-sdk

install-kustomize:
	curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh" | bash
	sudo mv kustomize /usr/local/bin

install-gcc:
	sudo apt install build-essential

install-all:
	make install-golang
	make install-kubectl
	make install-docker
	make install-minikube
	minikube start --vm-driver=none
	make install-operator-sdk
	make install-kustomize
	make install-gcc

create-directory:
	cd /usr/local
	sudo chmod -R 777 go
	cd go/src
	mkdir operators && cd operators
	go mod init

run-minikube:
	minikube start --vm-driver=none

init-operator-sdk:
	minikube start init
	operator-sdk init
	operator-sdk create api --version=v1alpha1 --kind=Traveller
