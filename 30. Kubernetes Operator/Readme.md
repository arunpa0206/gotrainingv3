# Operator SDK 

###  Prerequisites
Golang  v**1.16.3**

Kubectl

Docker

Minikube v**1.25.2**

Operator-Sdk v**1.11.0**

Kustomize

gcc


### Installation Instructions
*Step 1 - Install Golang v1.16.3*
	
	curl -OL https://golang.org/dl/go1.16.3.linux-amd64.tar.gz
	sudo tar -C /usr/local -xvf go1.16.3.linux-amd64.tar.gz
	
*Step 2 - Set the path for golang*

	sudo nano ~/.profile
At the end of the file add this following line -
	export PATH=$PATH:/usr/local/go/bin
	source ~/.profile
Export GOPATH
	export GOPATH=/usr/local/go
	
*Step 3 - Check the go version*

	go version

*Step 4 - Installing Kubectl*

	curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
	chmod +x ./kubectl
	sudo mv ./kubectl /usr/local/bin/kubectl

*Step 5 - Installing Docker*

	sudo apt-get update && sudo apt-get install docker.io -y
	sudo groupadd docker
	sudo usermod -aG docker $USER
	newgrp docker

*Step 6 - Check Docker is Running*

	docker run hello-world
If you are not able to see "Hello World from Docker" run the following command -	
	reboot

*Step 7 - Installing Minikube*

	curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
	sudo apt install conntrack

*Step 8 - Run Minikube*

	minikube start --vm-driver=none
	
*Step 9 - Installing Operator SDK v1.11.0*

	export ARCH=$(case $(uname -m) in x86_64) echo -n amd64 ;; aarch64) echo -n arm64 ;; *) echo -n $(uname -m) ;; esac)
	export OS=$(uname | awk '{print tolower($0)}')
	export OPERATOR_SDK_DL_URL=https://github.com/operator-framework/operator-sdk/releases/download/v1.11.0
	curl -LO ${OPERATOR_SDK_DL_URL}/operator-sdk_${OS}_${ARCH}
	chmod +x operator-sdk_linux_amd64 && sudo mv operator-sdk_linux_amd64 /usr/local/bin/operator-sdk

*Step 10 - Installing Kustomize*

	curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash
	sudo mv kustomize /usr/local/bin

*Step 11 - Installing GCC*

	sudo apt install build-essential
	
*Step 12 - Create Directory at the right path and initialise operator*

Go to /usr/local
	cd /usr/local
Change the permission of GO Folder
	sudo chmod -R 777 go
Go to go/src
	cd go/src
Make a operators directory and go inside it
	mkdir operators && cd operators
Run go mod init inside operators folder
	go mod init

*Step 13 - Initialising Operator SDK*

Start minikube
	minikube start init
Initialise Operator SDK
	operator-sdk init
Create APIs and Custom Resource
	operator-sdk create api --version=v1alpha1 --kind=Traveller

*Step 14 - Download the dependencies*

	go mod tidy
	go mod vendor
	
*Step 15 - Modify controller, deployment and service*

	Controller File Link - `https://github.com/arunpa0206/gotrainingv3/blob/main/30.%20Kubernetes%20Operator/traveller_controller.go`
	Deployment File Link - `https://github.com/arunpa0206/gotrainingv3/blob/main/30.%20Kubernetes%20Operator/deployment.go`
	Service File Link - `https://github.com/arunpa0206/gotrainingv3/blob/main/30.%20Kubernetes%20Operator/service.go`
	
*Step 15 - Installing CRD*

	make install
	
*Step 16 - Deploy a CRD instance*

	kustomize build config/samples | kubectl apply -f -

*Step 17 - Spin up the controller*

	make run
Keep it running in separate tab	

*Step 18 - Check the pods status*

Run the following command in separate tab	
	kubectl get all
	
*Step 19 - Exposing the service*

	minikube service backend-service

*Step 20 - Open localhost:30685*
	Check on port 30685.


