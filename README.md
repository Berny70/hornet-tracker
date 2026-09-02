# 🐝 Frelon Tracker - PWA v4.0

Une application Progressive Web App pour tracker un frelon en temps réel avec détection de couleur, zoom optique et boussole magnétique.

## 🎯 Fonctionnalités

- ✅ **Flux vidéo optimisé** en niveaux de gris (640×360 @ 60 FPS)
- ✅ **Détection par blob** de couleur orange/jaune précise
- ✅ **Zoom optique du smartphone** pour champ ultra-large
- ✅ **Sélection tactile** : touchez le frelon pour le cibler
- ✅ **Suivi intelligent** : suit le blob sélectionné même en présence d'autres
- ✅ **Boussole magnétique** avec cap en degrés et direction cardinale
- ✅ **Calibrage spatial** pour corriger la distorsion optique
- ✅ **Compteur FPS live** pour diagnostiquer les performances
- ✅ **Mode Debug** pour analyser en temps réel
- ✅ **Fonctionne offline** une fois installée
- ✅ **Installable** sur écran d'accueil (Android + iOS)

## 🚀 Déploiement sur GitHub Pages

### Étape 1 : Créer un nouveau repository GitHub

1. Allez sur [GitHub.com](https://github.com/new)
2. **Repository name** : `hornet-tracker`
3. **Description** : "PWA for real-time hornet tracking with color detection"
4. **Public** : ✓ (obligatoire pour Pages)
5. **Initialize** : Add a README ✓
6. Cliquez sur **Create repository**

### Étape 2 : Uploader les fichiers

#### Option A : Via GitHub Web (facile)

1. Dans votre repo, cliquez sur **Add file** → **Upload files**
2. Sélectionnez tous les fichiers du projet :
   - `index.html`
   - `v4.html`
   - `manifest.json`
   - `sw.js`
   - `README.md`
   - `LICENSE` (optionnel)
3. Cliquez **Commit changes**

#### Option B : Via Git CLI (recommandé)

```bash
# Cloner le repo
git clone https://github.com/VOTRE_USERNAME/hornet-tracker.git
cd hornet-tracker

# Copier les fichiers
cp index.html v4.html manifest.json sw.js README.md ./

# Pousser vers GitHub
git add .
git commit -m "Initial PWA deployment"
git push origin main
```

### Étape 3 : Activer GitHub Pages

1. Allez dans les **Settings** du repo
2. Dans le sidebar, cliquez sur **Pages**
3. **Source** → Choisissez **main** (ou master selon votre branche)
4. **Folder** → Sélectionnez **/ (root)**
5. Cliquez sur **Save**

Attendez ~1 minute. Votre app sera disponible à :
```
https://VOTRE_USERNAME.github.io/hornet-tracker/
```

### Étape 4 : Tester sur smartphone

1. **Ouvrez le lien** sur votre téléphone :
   ```
   https://VOTRE_USERNAME.github.io/hornet-tracker/
   ```

2. **Installez la PWA** :
   - **Android (Chrome)** : Appuyez sur ⋮ → "Ajouter à l'écran d'accueil"
   - **iOS (Safari)** : Appuyez sur ↗️ → "Ajouter à l'écran d'accueil"

3. L'app s'installe comme une app native ! 🎉

---

## 📱 Utilisation

### Lancer l'app

1. **Démarrez la caméra** → Le Pixel 7a active automatiquement son zoom optique ultra-large
2. **Acceptez la permission** d'accès caméra (et capteur d'orientation sur iOS)
3. **Touchez le frelon** sur l'écran → Un cercle vert apparaît pour verrouiller la cible
4. **La pastille magenta suit** le blob sélectionné, même si d'autres objets orange sont présents

### Utiliser la Boussole

La **boussole en bas à droite** affiche :
- **Flèche ⬆️** : Pointe toujours vers le Nord magnétique
- **Cap (0-360°)** : Direction en degrés (0°=N, 90°=E, 180°=S, 270°=O)
- **Direction** : Cardinale (N, NE, E, SE, S, SW, W, NW)

Notez le cap pour tracker la trajectoire du frelon ! 🧭

### Calibrage (optionnel)

Pour corriger la distorsion optique de votre téléphone :

1. Cliquez sur **⚙️ Calibrer**
2. Placez l'abricot aux 4 positions (coins de l'écran)
3. Validez chaque position
4. Les offsets sont sauvegardés automatiquement

**Les offsets persistent dans votre téléphone** même après fermeture ! ✓

### Ajuster la sensibilité (si besoin)

Modifiez les seuils HSL dans le code HTML (~line 335) :

```javascript
const colorThresholds = {
  minH: 15,    // Teinte min (0-360°)
  maxH: 40,    // Teinte max
  minS: 60,    // Saturation min (%) - Augmenter = plus sélectif
  minL: 45,    // Luminosité min (%) - Augmenter = ignore les zones sombres
};
```

### Profils pré-configurés pour couleurs

| Objet | minH | maxH | minS | minL | Notes |
|-------|------|------|------|------|-------|
| **Orange (par défaut)** | 15 | 40 | 60 | 45 | Bien équilibré |
| Orange clair | 15 | 45 | 30 | 40 | Moins sélectif, détecte plus |
| Orange foncé | 10 | 40 | 50 | 25 | Plus sélectif |
| Jaune pur | 45 | 65 | 60 | 50 | Pour objets jaunes |
| Frelon asiatique | 10 | 35 | 45 | 35 | Plus rouge/foncé |

---

## 🏗️ Architecture

```
hornet-tracker/
├── index.html          # Page d'accueil
├── v4.html             # Application v4.0 ⭐ SEULE VERSION
├── manifest.json       # Config PWA
├── sw.js               # Service Worker (cache + offline)
├── README.md           # Cette documentation
├── DEPLOYMENT.md       # Guide de déploiement GitHub Pages
└── LICENSE             # Licence MIT
```

### Technologies utilisées

- **HTML5** - Structure et sémantique
- **CSS3** - Design responsive et animations
- **Canvas API 2D** - Traitement vidéo et détection blob
- **MediaDevices API** - Accès caméra et zoom optique
- **DeviceOrientation API** - Boussole magnétique
- **Service Workers** - Cache intelligent et fonctionnement offline
- **Web App Manifest** - Installation PWA native
- **LocalStorage** - Persistance des paramètres de calibrage

---

## 🔧 Développement local

### Tester en local

```bash
# Avec Python 3
python -m http.server 8000

# Avec Node.js (http-server)
npx http-server

# Ou simplement ouvrir index.html
```

Ouvrez `http://localhost:8000` dans votre navigateur.

### Tester sur téléphone

Pour tester la PWA complète en local :

```bash
# 1. Trouvez votre adresse IP
ipconfig getifaddr en0  # macOS/Linux
ipconfig             # Windows

# 2. Connectez votre téléphone au même WiFi
# 3. Accédez à http://VOTRE_IP:8000 sur votre téléphone
```

⚠️ **Note** : HTTPS est requis pour les Service Workers en production. GitHub Pages le fournit gratuitement.

---

## 🚀 Mise à Jour de votre PWA

Après chaque modification de code :

```bash
git add v4.html index.html sw.js README.md
git commit -m "Description de la mise à jour"
git push origin main
```

**GitHub Pages met à jour automatiquement en ~1-2 minutes.**

---

## 📊 Performance

### Benchmarks (Pixel 7a)

| Métrique | Valeur |
|----------|--------|
| **FPS** | 60 ✓ |
| **Latence détection** | ~16-20ms |
| **Latence suivi** | <50ms |
| **Résolution caméra** | 640×360 (optimisée) |
| **Zoom optique** | Auto (ultra-large) |
| **Taille app** | ~22 KB |
| **Cache offline** | ✓ |
| **Batterie (30 min)** | ~10-12% |

---

## 🐛 Dépannage

### La caméra ne démarre pas
- **Android** : Vérifiez permission d'accès caméra dans Paramètres → Applications
- **iOS** : Allez dans Réglages → Safari → Caméra et acceptez
- Rechargez la page (Ctrl+R ou Cmd+R)
- Essayez un autre navigateur (Chrome recommandé)

### Le zoom optique ne s'active pas
- Disponible uniquement sur certains téléphones (Pixel 7a ✓)
- L'app fonctionnera quand même sans zoom
- Vérifiez la console (Debug) pour voir les capacités détectées

### La boussole n'apparaît pas
- **iOS 13+** : Acceptez la permission "Orientation" quand demandée
- **Android** : Vérifiez que la boussole du téléphone fonctionne
- Testez avec l'app Boussole du téléphone d'abord

### La pastille ne suit pas correctement
1. Activez **🐛 Debug** pour voir le blob détecté
2. Vérifiez que vous touchez **directement** l'objet (cercle vert doit apparaître)
3. Essayez le **Calibrage spatial** (⚙️ Calibrer)
4. Ajustez les seuils HSL si besoin

### FPS très bas (< 30)
- Améliorez l'éclairage (lumière naturelle)
- Fermez les apps en arrière-plan
- Réduisez le nombre d'onglets ouverts
- Vérifiez que votre téléphone n'est pas en mode économie d'énergie

### Offline ne fonctionne pas
- Assurez-vous d'avoir lancé l'app **une fois** en ligne
- Service Worker doit être enregistré (vérifiez dans DevTools)
- Videz le cache complet du navigateur
- Réinstallez l'app depuis l'écran d'accueil

---

## 📄 Licence

MIT - Voir le fichier `LICENSE` pour les détails.

---

## 🤝 Contribution

Les contributions sont bienvenues ! N'hésitez pas à :
- Signaler des bugs
- Proposer des améliorations
- Créer des pull requests

---

## 📚 Ressources

- [Web App Manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest)
- [Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
- [Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
- [GitHub Pages](https://pages.github.com/)

---

## 👨‍💻 Auteur

Créé avec ❤️ pour tracker les frelons en temps réel.

---

## ⭐ Support

Si vous trouvez cette app utile, n'oubliez pas de ⭐ le repo !
