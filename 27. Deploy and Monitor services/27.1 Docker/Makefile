connect:
	ssh -i "nlp-training.pem" ubuntu@ec2-13-233-121-5.ap-south-1.compute.amazonaws.com
	
#cd gotrainingv3/27.\ Deploy\ and\ Monitor\ services/27.1\ Docker

build:
	sudo docker build -t mydocker .

run:
	sudo docker run -d -p 7000:7000 mydocker

test:
	curl http://localhost:7000/people/1