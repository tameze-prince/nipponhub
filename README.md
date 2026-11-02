# 🌸 NipponHub

> Plateforme e-commerce de produits asiatiques : vendeurs, administrateurs et clients sur une même application.

[![CI](https://github.com/tameze-prince/nipponhub/actions/workflows/ci.yml/badge.svg)](https://github.com/tameze-prince/nipponhub/actions/workflows/ci.yml)
![Java](https://img.shields.io/badge/Java-21-ED8B00?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?logo=springboot&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

🌐 [Démo en ligne](https://front-end-nipponv1.vercel.app)

## Fonctionnalités

**Clients** : catalogue, panier avec variantes, commande, 3 modes de paiement (Mobile Money, retrait, paiement à la livraison), suivi de commande.

**Vendeurs** : gestion des produits et variantes, ventes flash, notifications, tableau de bord.

**Administrateurs** : gestion des utilisateurs, produits et commandes, modération, statistiques.

**Transverse** : authentification JWT, contrôle d'accès par rôle (`CUSTOMER`, `OWNER`, `ADMIN`), upload d'images via Cloudinary, CORS configuré.

## Architecture

```
Frontend (Next.js)  ──REST──▶  Backend (Spring Boot)  ──JDBC──▶  PostgreSQL
      Vercel                        Render (Docker)               + Cloudinary (images)
```

## Structure du dépôt

```
nipponhub/
├── backend/     API Spring Boot (Java 21, Maven, Dockerfile)
├── frontend/    Application Next.js (TypeScript, Tailwind)
├── docs/        Documentation du projet
└── .github/     Intégration continue
```

## Démarrage rapide

### Backend

```bash
cd backend
cp .env.example .env     # puis renseigner les valeurs
./mvnw spring-boot:run   # http://localhost:8080
```

### Frontend

```bash
cd frontend
npm install
npm run dev              # http://localhost:3000
```

### Tests

```bash
cd backend  && ./mvnw test
cd frontend && npm run lint && npm test
```

## Configuration

Variables du backend (voir [`backend/.env.example`](backend/.env.example)) : base de données, secret JWT et durées d'expiration, origines CORS autorisées, identifiants Cloudinary.

**Ne jamais commiter de fichier `.env`** : seuls les fichiers `.env.example` sont versionnés.

## Déploiement

| Composant | Plateforme | Réglage important |
|---|---|---|
| Frontend | Vercel | *Root Directory* = `frontend` |
| Backend | Render (Docker) | *Root Directory* = `backend` |

Une vue d'ensemble plus détaillée est disponible dans [`docs/PROJECT_OVERVIEW.md`](docs/PROJECT_OVERVIEW.md).

## Historique

L'ancienne version monolithique du dépôt est conservée sous le tag `legacy-monolith-v0`.

## Licence

[MIT](LICENSE) © ZEUFACK TAMEZE Prince

## Auteur

**ZEUFACK TAMEZE Prince** · [@tameze-prince](https://github.com/tameze-prince)