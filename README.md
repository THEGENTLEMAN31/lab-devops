# Lab-DevOps : Pipeline CI/CD Django & Docker

Ce projet est une démonstration complète d'un cycle de vie DevOps moderne pour une application Django. Il intègre la conteneurisation avec Docker, l'automatisation des tests avec GitHub Actions, le déploiement continu et le monitoring des erreurs avec Sentry.

## 🚀 Fonctionnalités
- **Django 4.2** : Application de monitoring simple.
- **Docker & Docker Compose** : Environnement universel et reproductible.
- **Kill-Switch Test** : Test de sécurité automatisé bloquant le déploiement si des balises de maintenance (mot "Attention") sont présentes.
- **CI/CD GitHub Actions** : Pipeline automatisé de construction et de test.
- **Sentry Monitoring** : Capture des erreurs en temps réel, même pour les bugs "silencieux".

## 🛠 Installation Locale

### Avec Docker (Recommandé)
1. Clonez le dépôt :
   ```bash
   git clone git@github.com:THEGENTLEMAN31/lab-devops.git
   cd lab-devops
   ```
2. Lancez l'application :
   ```bash
   docker compose up --build
   ```
3. Accédez à l'application sur `http://localhost:8000`.

### Sans Docker
1. Créez un environnement virtuel :
   ```bash
   python -m venv venv
   source venv/bin/activate  # ou venv\Scripts\activate sur Windows
   ```
2. Installez les dépendances :
   ```bash
   pip install -r requirements.txt
   ```
3. Lancez le serveur :
   ```bash
   python manage.py runserver
   ```

## 🤖 Pipeline CI/CD (GitHub Actions)
Le fichier `.github/workflows/verify.yml` définit le workflow suivant :
1. **Build** : Construction de l'image Docker.
2. **Test** : Exécution des tests Django dans le conteneur.
3. **Validation** : Le bouton "Merge" sur GitHub ne devient vert que si tous les tests passent.

## 📈 Monitoring Sentry
L'application est configurée pour envoyer les exceptions à Sentry.
- Une route `/sentry-debug/` permet de simuler une erreur `ZeroDivisionError`.
- Les erreurs sont capturées manuellement pour démontrer le monitoring des "Silent Fails".

## 🐳 DockerHub
L'image est disponible sur DockerHub :
`docker pull thegentleman31/lab-devops:latest`

---
*Projet réalisé dans le cadre du TP Collecte et Exploration des données - EIGSI 2026.*