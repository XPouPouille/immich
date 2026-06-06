# Immich — Self-hosted photo backup

Déploiement Immich avec Traefik comme reverse proxy.

## Prérequis

- Docker + Docker Compose installés
- Réseau Docker `traefik` existant
- Traefik configuré avec entrypoint `websecure` et certresolver `letsencrypt`

## Installation

### 1. Cloner le repo

```bash
cd ~
git clone https://github.com/XPouPouille/immich.git
cd immich
```

### 2. Configurer l'environnement

```bash
cp .env-exemple .env
nano .env
```

Modifier au minimum :
- `IMMICH_DOMAIN` — ton domaine
- `DB_PASSWORD` — mot de passe fort
- `UPLOAD_LOCATION` — chemin de stockage des photos sur l'hôte

### 3. Créer le dossier de stockage

```bash
mkdir -p /opt/immich/photos
```

> Adapter selon la valeur de `UPLOAD_LOCATION` dans ton `.env`.

### 4. Lancer les conteneurs

```bash
docker compose up -d
```

### 5. Accéder à Immich

Ouvrir `https://<IMMICH_DOMAIN>` dans le navigateur.  
Créer le compte administrateur au premier lancement.

## Commandes utiles

```bash
# Voir les logs
docker compose logs -f immich-server

# Arrêter
docker compose down

# Mettre à jour
docker compose pull && docker compose up -d
```
