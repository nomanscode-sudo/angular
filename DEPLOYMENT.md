\# Guide de d�ploiement de l'application



Ce document explique comment d�ployer l'application en environnement de production.



\## Pr�requis



\- Docker 20.10+

\- Un compte sur Docker Hub

\- Acc�s au serveur de production



\## �tapes de d�ploiement manuel



1\. Construire l'image Docker

&nbsp;  ```bash

&nbsp;  docker build -t angular-app:latest .

&nbsp;  

Tester l'image localement

docker run -p 4200:80 angular-app:latest

Pousser l'image vers Docker Hub

docker tag angular-app:latest username/angular-app:latest

docker push username/angular-app:latest

D�ployer sur le serveur

ssh user@production-server

docker pull username/angular-app:latest

docker stop angular-app || true

docker rm angular-app || true

docker run -d --name angular-app -p 80:80 username/angular-app:latest



