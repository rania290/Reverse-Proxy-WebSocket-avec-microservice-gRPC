
# 🚀 Chat Temps Réel - Architecture gRPC + WebSocket

![Diagramme d'architecture](docs/architecture.png)

Un système de chat performant combinant la puissance de gRPC pour les microservices et la flexibilité de WebSocket pour les clients web.

## ✨ Fonctionnalités Avancées

| Fonctionnalité | Description | Technologie |
|----------------|------------|-------------|
| **Chat temps réel** | Messages instantanés avec latence minimale | WebSocket |
| **Historique intelligent** | Récupération des messages récents avec pagination | gRPC |
| **Multi-salles** | Support de plusieurs canaux de discussion | Protobuf |
| **Presence** | Suivi des utilisateurs connectés | gRPC Stream |
| **Reconnexion** | Rétablissement automatique de la connexion | WebSocket |

## 🛠 Stack Technique

### Backend
- **Node.js** (v20+) - Runtime principal
- **gRPC** (@grpc/grpc-js) - Communication inter-services
- **Protocol Buffers** - Sérialisation binaire efficace

### Frontend
- **WebSocket API** - Communication full-duplex
- **Vanilla JS** - Pas de framework nécessaire
- **CSS3** - Animations fluides

## � Démarrage Rapide

### Prérequis
- Node.js v20+
- NPM v10+
- Navigateur moderne

```bash
# 1. Cloner le dépôt
git clone https://github.com/votre-user/grpc-websocket-chat.git
cd grpc-websocket-chat

# 2. Installer les dépendances
npm install

# 3. Configurer l'environnement
cp .env.example .env
```

## ▶ Exécution

| Service | Commande | Port | Environnement |
|---------|----------|------|---------------|
| Serveur gRPC | `npm run server` | 50051 | Production |
| Proxy WS | `npm run proxy` | 8080 | Développement |
| Client | Ouvrir `client.html` | - | - |

**Scripts utiles :**
```bash
npm run dev    # Lance les deux services en mode développement
npm run test   # Exécute les tests unitaires
```

## 📚 Documentation API

### Protobuf Interface
```protobuf
service ChatService {
  rpc GetUser(GetUserRequest) returns (GetUserResponse);
  rpc JoinChat(JoinRequest) returns (stream ChatMessage);
  rpc SendMessage(ChatMessage) returns (MessageAck);
  rpc GetHistory(HistoryRequest) returns (HistoryResponse);
}
```

### Messages WebSocket

**Format standard :**
```json
{
  "event": "message|join|leave",
  "data": {
    "user": "string",
    "content": "string",
    "timestamp": "ISO8601"
  }
}
```

## 🧪 Tests & Validation

### Scénarios de test
1. **Test de charge** :
   ```bash
   artillery run load-test.yml
   ```

2. **Test de résilience** :
   ```bash
   npm run stress-test
   ```

3. **Couverture de code** :
   ```bash
   npm run coverage
   ```

## 🚀 Déploiement

### Avec Docker
```bash
docker-compose up --build -d
```

### Sur Kubernetes
```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

## 📊 Métriques

Le système expose des métriques Prometheus sur :
- `/metrics` (serveur gRPC)
- `/ws-metrics` (proxy WebSocket)

## 🤝 Contribution

1. Forker le projet
2. Créer une branche (`git checkout -b feat/nouvelle-fonctionnalite`)
3. Committer (`git commit -am 'Ajout d'une feature'`)
4. Pusher (`git push origin feat/nouvelle-fonctionnalite`)
5. Ouvrir une Pull Request

## 📜 Licence

MIT License - Voir [LICENSE](LICENSE) pour plus de détails.



