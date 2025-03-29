
# Reverse Proxy WebSocket avec microservice gRPC


Ce projet illustre l'utilisation de Protocol Buffers (Protobuf) et gRPC pour créer un système de chat avec un reverse proxy WebSocket.

## 📋 Description
- **Protobuf** : Format de sérialisation de données structurées multiplateforme
- **gRPC** : Framework RPC haute performance développé par Google
- **Fonctionnalités** :
  - Service de chat avec streaming bidirectionnel
  - Gestion des utilisateurs
  - Reverse proxy WebSocket pour l'interfaçage client

## ⚙️ Installation

1. Cloner le dépôt et installer les dépendances :
```bash
mkdir grpc-ws-reverse-proxy
cd grpc-ws-reverse-proxy
npm init -y
npm install @grpc/grpc-js @grpc/proto-loader ws
```

## 🏗️ Structure du projet

```
grpc-ws-reverse-proxy/
├── chat.proto            # Définition des services Protobuf
├── server.js            # Serveur gRPC
├── proxy.js             # Reverse proxy WebSocket
└── package.json
```

## 🚀 Lancement

1. Démarrer le serveur gRPC :
```bash
node server.js
```

2. Démarrer le reverse proxy WebSocket :
```bash
node proxy.js
```

## 🔧 Fonctionnement

### Serveur gRPC
- Écoute sur `0.0.0.0:50051`
- Implémente 2 méthodes :
  1. `GetUser` - Récupère les informations d'un utilisateur
  2. `Chat` - Gère le streaming bidirectionnel de messages

### Reverse Proxy WebSocket
- Écoute sur `ws://localhost:8080`
- Relaye les messages entre clients WebSocket et le service gRPC

## 🧪 Test avec Postman

1. Se connecter à `ws://localhost:8080`
2. Envoyer un message au format JSON :
```json
{
  "chat_message": {
    "id": "msg1",
    "room_id": "room1",
    "sender_id": "client1",
    "content": "Hello World !"
  }
}
```

## 📝 Travail à faire

### 1. Historique des messages
- Ajouter une méthode `GetChatHistory` dans `chat.proto`
- Implémenter le stockage des messages dans `server.js`
- Adapter le proxy pour gérer cette nouvelle méthode

### 2. Client Web (Bonus)
Créer une page HTML avec :
- Formulaire d'envoi de messages
- Affichage des messages en temps réel
- Connexion WebSocket à `ws://localhost:8080`

## 📚 Ressources
- [Protobuf Documentation](https://developers.google.com/protocol-buffers)
- [gRPC Documentation](https://grpc.io/docs/)
- [WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)

**Auteure : Rania Mrad**  
