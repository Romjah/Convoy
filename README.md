# 🚗 Convoy — Rejoins ton crew sur la route

**Convoy** est une application mobile qui permet à un groupe d’amis ou de passionnés d’automobile de **se localiser en temps réel**, **partager les coûts de trajet**, et **rejoindre ensemble un événement** (meet, rallye, roadtrip…).

Développée en complément de **GearConnect**, Convoy vise à rendre les déplacements collaboratifs plus simples, plus fun et plus sociaux.

---

## ✨ Fonctionnalités MVP

- 🔑 Création ou rejoint d’un **groupe de route**
- 🗺️ **Carte live** affichant la position GPS de tous les membres
- 🏁 **Destination commune + checkpoints**
- 💰 **Partage des coûts** (carburant, péages, repas…)
- 👻 **Ghost mode** pour désactiver le partage GPS à tout moment
- ⏱️ **Suppression automatique des données après 24h**

---

## ⚙️ Stack technique

| Composant     | Technologie principale |
|----------------|------------------------|
| Mobile         | React Native + Expo (TypeScript, SDK 54) |
| Backend        | Node.js + Express + MongoDB |
| Temps réel     | Socket.IO |
| Cartes         | Mapbox SDK |
| Authentification | Email magique (mock MVP) + Group Code |
| UI/Design      | Interface inspirée de GearConnect, simple et fluide |

---

## 🧩 Architecture du projet

convoy/
├── app/ → Application mobile Expo (frontend)
│ ├── src/
│ │ ├── screens/ # Auth, Home, Map, Costs, Settings
│ │ ├── components/ # MapView, MemberMarker, ExpenseForm...
│ │ ├── services/ # API, Socket, Location, Storage
│ │ └── state/ # Auth, Group, Event, Positions, Expenses
│ └── app.json
│
├── server/ → Backend Express + Socket.IO
│ ├── src/
│ │ ├── models/ # User, Group, Event, Position, Expense
│ │ ├── routes/ # REST API
│ │ ├── sockets/ # Realtime (positions, checkpoints)
│ │ └── utils/ # Hash, Auth, Config
│ └── tsconfig.json
│
├── .env.example
├── package.json


---

## 🚀 Lancer le projet localement

### 1️⃣ Cloner le dépôt
```bash
git clone https://github.com/Romjah/Convoy.git
cd Convoy
```

### 2️⃣ Installer les dépendances
```bash
npm install
```

### 3️⃣ Configurer l’environnement
Créer un fichier .env à la racine et y coller :
```bash
# Server
MONGO_URL=mongodb://localhost:27017/convoy
JWT_SECRET=dev_secret
JOINCODE_SALT=convoy_salt

# App (Expo)
EXPO_PUBLIC_API_BASE=http://192.168.X.X:4000      # Remplacer par ton IP locale
EXPO_PUBLIC_SOCKET_URL=ws://192.168.X.X:4000
MAPBOX_ACCESS_TOKEN=YOUR_MAPBOX_TOKEN
```


### 4️⃣ Lancer en développement
```bash
npm run dev
```

Le script démarre simultanément :
- le serveur backend (port 4000)
- l’application mobile Expo (ouverture du tunnel sur ton téléphone)


## 🧠 Fonctionnement résumé

1. Un utilisateur crée un groupe Convoy → reçoit un code unique à partager.
2. Les amis rejoignent le groupe → leurs positions apparaissent sur la carte.
3. L’organisateur définit une destination commune et des checkpoints.
4. Chacun peut ajouter ses dépenses → l’app calcule les parts de chacun.
5. À la fin de l’événement, les données sont supprimées automatiquement (TTL 24h).


## 💰 Exemple de calcul de partage des coûts
```bash
• Romain : essence 60 €
• Lucas : péage 20 €
• Thomas : repas 30 €

Total : 110 € / 3 = 36,66 € chacun

→ Romain doit recevoir 23,33 €
→ Lucas doit 16,66 €
→ Thomas doit 6,66 €
```
Export possible via bouton “📋 Copier le résumé”.


## 🔐 Confidentialité et respect des données

- Les positions GPS ne sont jamais stockées de manière permanente
- L’utilisateur peut désactiver le partage à tout moment (“Ghost mode”)
- Toutes les données d’un événement sont supprimées automatiquement après 24h
- Le code d’accès au groupe est haché côté serveur


## 🔮 Roadmap à venir

| Statut | Fonctionnalité                                                |
| :----: | ------------------------------------------------------------- |
|    ✅   | Création / Rejoint de groupe                                  |
|    ✅   | Localisation live via Socket.IO                               |
|    ✅   | Destination & checkpoints                                     |
|    ✅   | Split des coûts                                               |
|    ⏳   | Historique des trajets                                        |
|    ⏳   | Intégration complète GearConnect (import/export d’événements) |
|    ⏳   | Version Premium (groupes illimités, historique cloud)         |
|   🧠   | Suggestions IA d’itinéraires optimisés pour groupes           |


## 👥 Équipe & origine du projet

Développé par Romain Jahier dans le cadre de GearConnect Labs,
une initiative visant à créer des outils numériques pour les passionnés d’automobile.
  “Convoy rend les trajets de groupe aussi fluides que vos virées.”


## 📄 Licence

Ce projet est distribué sous licence MIT — utilisation libre, commerciale et modification autorisées.
Consultez le fichier LICENSE pour plus de détails.


## 📬 Contact

- Twitter : @GearConnect
- Instagram : Quartz Edit Studio
- GitHub : Romjah

### 🚘 Convoy — Parce qu’un roadtrip, c’est mieux quand tout le monde arrive ensemble.
---
Souhaites-tu que je t’ajoute ensuite la **version anglaise équivalente** juste en dessous dans le même README (pour la rendre bilingue sur GitHub) ?
