# GBI Business OS

Outil commercial de **GBI Events** : prospects, appels, devis, stock de matériel, messages et performance par canal.

- **Site :** https://gbi-events.github.io/business-os/ (GitHub Pages, branche `main`)
- **Données :** Supabase, projet `gbi-business-os` (organisation GBI Events)
- **Connexion :** email et mot de passe. Les comptes sont créés dans Supabase → Authentication → Users → Invite, et l'email doit aussi figurer dans la table `membres`.

## Fichiers
| Fichier | Rôle |
|---|---|
| `index.html` | toute l'application : interface, logique, connexion, couche Supabase |
| `config.js` | URL du projet et clé **publique** Supabase. Ne jamais y mettre la clé secrète `service_role` |
| `CLAUDE.md` | règles à suivre pour toute modification faite par Claude |

## Base de données (Supabase)
Tables au format document : `id text`, `data jsonb`.
- `prospects` : fiches prospects ;
- `reservations` : réservations de matériel ;
- `settings` : un document `pricing`, avec les tarifs et le stock ;
- `spend` : dépenses par canal ;
- `emails` : prospection par email (phase 2) ;
- `membres` : qui a le droit d'accès.

Fonction `fusion_doc(t, doc_id, patch)` : fusionne `patch` dans `data`.

Règles d'accès (RLS) : seuls les utilisateurs connectés **et** présents dans `membres` peuvent lire ou écrire.

## Ajouter une personne
1. Supabase → Authentication → Users → **Invite user** (son email).
2. SQL Editor :
   ```sql
   insert into membres(email, nom, role) values ('email@exemple.fr', 'Prénom', 'membre');
   ```
3. La personne clique sur le lien reçu, choisit son mot de passe sur le site, puis se connecte.
