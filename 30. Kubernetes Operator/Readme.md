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
**Golang**
`curl -OL https://golang.org/dl/go1.16.3.linux-amd64.tar.gz`
`sudo tar -C /usr/local -xvf go1.16.3.linux-amd64.tar.gz`
`sudo nano ~/.profile`
At the end of the file add this following line -
`export PATH=$PATH:/usr/local/go/bin`
`source ~/.profile`
`go version`

*Export GOPATH*
`export GOPATH=/usr/local/go`

**Kubectl**
`curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl`
`chmod +x ./kubectl`
`sudo mv ./kubectl /usr/local/bin/kubectl`

**Docker**
`sudo apt-get update && sudo apt-get install docker.io -y`
`sudo groupadd docker`
`sudo usermod -aG docker $USER`
`newgrp docker`
`docker run hello-world`
If you are not able to see "Hello World from Docker" run the following command -
`reboot`

**Minikube**
`curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/`
`sudo apt install conntrack`

*Run Minikube*
`minikube start --vm-driver=none`

**Operator SDK**
`export ARCH=$(case $(uname -m) in x86_64) echo -n amd64 ;; aarch64) echo -n arm64 ;; *) echo -n $(uname -m) ;; esac)`
`export OS=$(uname | awk '{print tolower($0)}')`
`export OPERATOR_SDK_DL_URL=https://github.com/operator-framework/operator-sdk/releases/download/v1.11.0`
`curl -LO ${OPERATOR_SDK_DL_URL}/operator-sdk_${OS}_${ARCH}`
`chmod +x operator-sdk_linux_amd64 && sudo mv operator-sdk_linux_amd64 /usr/local/bin/operator-sdk`

**Kustomize**
`curl -s "https://raw.githubusercontent.com/\
kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash`
`sudo mv kustomize /usr/local/bin`

**GCC**
`sudo apt install build-essential`

### Build a Kubernetes Operator

Go to /usr/local
`cd /usr/local`

Change the permission of GO Folder
`chmod -R 777 go`

Go to /go/src
`cd /go/src`

Make a operators directory and go inside it
`mkdir operators && cd operators`

Run go mod init inside operators folder
`go mod init`

Start minikube
`minikube start init`

Initialise Operator SDK
`operator-sdk init`

Create APIs and Custom Resource
`operator-sdk create api --version=v1alpha1 --kind=Traveller`

Download the dependencies
`go mod tidy`
`go mod vendor`

Install the CRD
`make install`

Deploy a CRD instance
`kustomize build config/samples | kubectl apply -f -`

Spin up the controller
`make run`

Check the state
`kubectl get all`

Exposing the service
`minikube service backend-service`

Check on port 30685.


