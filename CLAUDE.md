# Règles pour Claude : dépôt business-os (GBI Events)

Ce dépôt est modifié par le Claude de Germaine (propriétaire de GBI Events) et par celui de Kissima (opérateur, génération de prospects).

## Avant toute modification
- Le site entier tient dans `index.html`. Garde la structure, les styles (variables CSS de `:root`, mode sombre) et la logique existante. Change seulement ce qui est demandé.
- Les données passent par la couche Supabase, en bas de `index.html`. Elle imite l'ancienne interface `window.claude.use('db')`, avec `collection().onSnapshot`, `add`, `doc().get`, `set`, `update` et `delete`. Pour une nouvelle fonctionnalité, réutilise-la.
- Un changement de base (nouvelle table, colonne, règle RLS) se fait par migration SQL dans Supabase, en activant la RLS et la règle `est_membre()` sur toute nouvelle table.
- Ne mets jamais la clé `service_role`, un mot de passe ou une clé privée dans ce dépôt public.
- Après une modification, vérifie que la page se charge, que la connexion fonctionne et que les fiches s'affichent.

## Règles commerciales de GBI Events
- **Argument principal : le clé en main.** Un seul interlocuteur pour le traiteur, la décoration et le matériel.
- **Traiteur pour tout type de client :** la cuisine africaine est la spécialité mise en avant, pas toute l'offre.
- **Packs :** uniquement pour les mariages.
- **Panier minimum :** 1 500 € par événement. En dessous, seulement sur dérogation de Germaine.
- **Matériel :** stock suivi par date, jamais de promesse au-delà du stock.

## Emails de prospection (phase 2)
- **Chaque entreprise reçoit un email :**
  - piste « signal » quand un événement ou un indice a été trouvé ;
  - piste « anti-signal » sinon, avec des faits réels sur la société et une question ouverte et bienveillante.
- **Contenu :** jamais de prix, une seule question, moins de 100 mots.
- **Désinscription :** aucune mention dans le texte principal. Tout en bas, après la signature, en petits caractères gris : « Message professionnel envoyé par GBI Events. Pour ne plus recevoir nos messages, répondez STOP. »
- **Pas de lien de désinscription dans les en-têtes.**
