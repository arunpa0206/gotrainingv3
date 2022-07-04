INSTALLATION INSTRUCTIONS OF GOLANG IN WINDOWS, MAC AND LINUX


Installation in windows

step 1. install chocolatey using the following command:
     open windows powershell with admin access
     Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))


step 2. install make using the following command:
        choco install make
        make --version

step 3. install-git using following command:
        choco install git
        Restart the terminal 

Step 4 . Install golang :
          
         Recommended Way : Go to their official website and download and install the latest version - https://go.dev/dl/
         
         Other way using Choco :
                              choco install golang (Might not install the latest version)

                              Install specific version of golang
                              choco install golang --version=1.16.6 --allow-downgrade -y


        Make a project Folder
        And run the command to initialise GO
                go mod init (module_name)
        
        Write .go files and run with:
                        go run (file_name).go

Step 5:
        Install protoc
        choco install protoc

Step 6:
        Install mysql
        choco install mysql
        ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass';

Step 7:
        Install docker
        choco install docker-desktop

Installation in MAC

step 1. Install homebrew uisng following command:
         ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

step 2. Install make using following command
        brew install make
        make --version

step 3. Install git using following command
        brew install git
        git --version

step 4. Install go in MAC
        brew install go

        Install specific version of Golang
        brew install postgresql@1.16.6

        Make a project Folder
        And run the command to initialise GO
                go mod init (module_name)
        
        Write .go files and run with:
                        go run (file_name).go

Step 5:
        Install protoc
        brew install protoc-gen-go

Step 6:
        Install mysql
        brew install mysql
       
Step 7:
        Install docker
        brew cask install docker

Installation in Linux

Step 1 :- Install GO
                sudo wget https://golang.org/dl/go1.17.3.linux-amd64.tar.gz
                sudo tar -C /usr/local -xzf go1.17.3.linux-amd64.tar.gz
                export PATH=$PATH:/usr/local/go/bin
                source ~/.bashrc (optional)
                go version
        
        Make a project Folder
        And run the command to initialise GO
                go mod init (module_name)
        
        Write .go files and run with:
                        go run (file_name).go

Step 2:
        Install protoc
        sudo apt update
        sudo apt install snapd
        sudo snap install protobuf --classic

Step 6:
        Install mysql
        sudo apt install mysql-server

Step 7:
        Install docker
        sudo snap install docker
