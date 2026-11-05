# Anaros Beauty Lounge — Spécification produit

Dossier de référence du logiciel de gestion d'institut de beauté **Anaros Beauty Lounge** :
16 chapitres, de la vision produit au guide d'intégration vidéo.

## Contenu

- `spec.pdf` — document A4 paginé (36 pages), prêt à diffuser.
- `spec.html` — version HTML du même document, avec les captures en annexe.
- `assets/` — 14 captures de l'application déployée.

## Ce que couvre le document

| Chapitre | Sujet |
|---|---|
| 01 – 04 | Résumé exécutif, contexte métier, 4 rôles, cartographie des 9 modules |
| 05 | Analyse module par module : agenda, rendez-vous, clientes, catalogue, équipe |
| 06 – 07 | Parcours utilisateurs et modèle de données (7 tables, Drizzle) |
| 08 – 11 | Architecture Express/PostgreSQL, design system, onboarding, sécurité |
| 12 – 14 | Audit de maturité, feuille de route en 3 phases, exploitation Passenger |
| 15 – 16 | Guide vidéo (storyboard, script) et annexes (routes, dépendances, captures, glossaire) |

## Constats de sécurité documentés

Lecture du code serveur (`server/storage.ts`) :

1. **Mots de passe en clair** — comparaison directe `eq(profiles.password, password)`,
   sans hachage ; les mots de passe générés à l'onboarding suivent le motif `prenom123`.
2. **Aucun filtrage tenant** — `tenant_id` est stocké mais jamais appliqué dans les requêtes.
3. **Aucune détection de chevauchement** — deux rendez-vous peuvent occuper le même employé.

Ces trois points sont traités en phase 1 de la feuille de route.

## Application

- Démonstration : https://springgreen-cheetah-495703.hostingersite.com/
