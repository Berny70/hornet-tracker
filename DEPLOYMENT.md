# 🚀 Guide Rapide de Déploiement GitHub Pages

Déployez votre PWA Frelon Tracker en 5 minutes !

## ⚡ Déploiement Ultra-Rapide (Git CLI)

### 1️⃣ Préparer votre machine

```bash
# Installer Git si nécessaire
# https://git-scm.com/download

# Configurer Git avec votre compte GitHub
git config --global user.name "Votre Nom"
git config --global user.email "votre@email.com"
```

### 2️⃣ Créer le repository GitHub

Allez sur https://github.com/new et créez un repo nommé `hornet-tracker`

### 3️⃣ Pousser les fichiers

```bash
# Clone le repo vide
git clone https://github.com/VOTRE_USERNAME/hornet-tracker.git
cd hornet-tracker

# Copier tous les fichiers du projet
# (index.html, v2.html, manifest.json, sw.js, README.md, LICENSE)

# Pousser vers GitHub
git add .
git commit -m "Initial PWA deployment v2.0"
git push origin main
```

### 4️⃣ Activer GitHub Pages

1. Allez sur https://github.com/VOTRE_USERNAME/hornet-tracker/settings/pages
2. **Source** → Sélectionnez `main` branch
3. **Folder** → Sélectionnez `/ (root)`
4. Cliquez **Save**

### 5️⃣ Attendez ~1 minute ⏳

Votre PWA est maintenant en ligne à :
```
https://VOTRE_USERNAME.github.io/hornet-tracker/
```

---

## 📱 Tester sur Smartphone

### Android (Chrome)
1. Ouvrez le lien ci-dessus
2. Appuyez sur **⋮** (menu)
3. Sélectionnez **"Ajouter à l'écran d'accueil"**
4. Lancez l'app depuis votre écran d'accueil

### iPhone (Safari)
1. Ouvrez le lien ci-dessus
2. Appuyez sur **↗️** (partage)
3. Sélectionnez **"Ajouter à l'écran d'accueil"**
4. Lancez l'app depuis votre écran d'accueil

---

## 🔧 Mise à Jour de votre PWA

Après chaque modification de code :

```bash
git add .
git commit -m "Description de la mise à jour"
git push origin main
```

**GitHub Pages met à jour automatiquement en ~2 minutes.**

---

## ✅ Vérifier le déploiement

1. Visitez votre URL GitHub Pages
2. Ouvrez les **DevTools** (F12)
3. Allez sur l'onglet **Application**
4. Vérifiez :
   - ✓ Service Worker enregistré
   - ✓ Manifest chargé
   - ✓ Cache disponible

---

## 🆘 Dépannage

### Pages n'affiche rien
- Attendez 2-3 minutes après le push
- Videz le cache du navigateur (Ctrl+Shift+Del)
- Vérifiez que les fichiers sont bien sur GitHub

### Service Worker ne s'enregistre pas
- HTTPS doit être actif (GitHub Pages le fournit)
- Vérifiez que `sw.js` est dans le dossier root
- Ouvrez la console pour les erreurs

### PWA n'est pas proposée à l'installation
- Assurez-vous que `manifest.json` existe
- Vérifiez que l'app est en HTTPS
- Testez depuis une autre machine

---

## 📊 URLs Utiles

| Ressource | Lien |
|-----------|------|
| **GitHub Pages Guide** | https://pages.github.com/ |
| **GitHub Settings** | https://github.com/VOTRE_USERNAME/hornet-tracker/settings/pages |
| **Repository** | https://github.com/VOTRE_USERNAME/hornet-tracker |
| **Live App** | https://VOTRE_USERNAME.github.io/hornet-tracker/ |

---

## 💡 Astuces Pro

### Personnaliser le domaine
Si vous avez un domaine personnalisé, dans **Settings → Pages** :
- Custom domain → Entrez votre domaine
- Suivez les instructions DNS

### Automatiser les mises à jour
Utilisez GitHub Actions pour des déploiements automatiques :
```yaml
# À ajouter dans .github/workflows/deploy.yml
name: Deploy
on: [push]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      # GitHub Pages se met à jour automatiquement
```

### Monitoring
Activez les notifications GitHub pour suivre l'état des déploiements.

---

## 🎉 C'est fait !

Votre PWA est maintenant en ligne et installable sur tous les appareils ! 🚀

Partagez le lien avec vos amis :
```
https://VOTRE_USERNAME.github.io/hornet-tracker/
```

