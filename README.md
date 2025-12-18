# projet_kafka
# Kafka Chat Demo

Projet illustrant le fonctionnement d’Apache Kafka à travers un système de messagerie utilisant un producteur et un consommateur.  
L’objectif est de comprendre le rôle du broker Kafka dans la transmission de messages en temps réel.


## Objectif du projet

Mettre en place une architecture où :

- un **producer** publie des messages sur un topic Kafka
- un **consumer** lit ces messages en continu
- Kafka agit comme **système de message broker** permettant l’échange fiable de données

Ce projet permet d’aborder les notions essentielles de Kafka : topics, partitions, consommation en temps réel et communication asynchrone.

## Prérequis
- Docker
- Docker Desktop

## Etapes du projet:

## 1️. Lancer l’environnement

Depuis le dossier du projet :

docker compose up -d

On doit alors voir:
zookeeper   Up
kafka       Up

## 2. Créer le topic Kafka

docker exec -it kafka kafka-topics --create --topic chat-messages --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

On vérifie la création:

docker exec -it kafka kafka-topics --list --bootstrap-server localhost:9092

On lance le consumer dans un nouveau terminale:

docker exec -it kafka kafka-console-consumer --topic chat-messages --bootstrap-server localhost:9092 --from-beginning

On lance le producer encore dans un nouveau terminale:

docker exec -it kafka kafka-console-producer --topic chat-messages --bootstrap-server localhost:9092

Et le chat fonctionne quand les messages que l'on écrit le terminale de producer apparaissent dans le terminale de consumer.

<img width="1414" height="174" alt="image" src="https://github.com/user-attachments/assets/7797e9b2-dcc5-4545-a3ec-0581c0dc663f" />






