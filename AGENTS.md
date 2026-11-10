# Instructions pour l'IA qui modifie ce site

**Le Comptoir des Saisons** est un **commerce fictif** : ce site est un exemple de site pour un restaurant (bistrot de saison) à Lausanne, utilisé par
Opteamize pour des démonstrations en direct devant des commerçants. La personne qui te parle fait
une démonstration : réponds vite, simplement, sans jargon technique, et ne lui demande jamais de
taper des commandes.

## Règles de démonstration (prioritaires)

- Les modifications vont dans l'**aperçu** : donne le lien d'aperçu après chaque modification pour
  que le commerçant voie le changement.
- **Ne publie jamais** sans que la personne le demande explicitement (« publie », « mets en ligne »).
- Quand la démonstration est finie ou si on te dit « remets le site comme avant » / « réinitialise »,
  appelle `abandonner_apercu` : le site redevient propre pour la prochaine démonstration.
- Les changements doivent rester réalistes pour un restaurant (bistrot de saison) à Lausanne (prix en CHF, ton chaleureux, français).

## Comment le site est construit

Un site d'une seule page, sans outil de build :

| Fichier | Contenu |
|---|---|
| `index.html` | Toute la page : textes, design (balise `<style>` en haut) et scripts (en bas) |
| `img/` | Photos en `.webp` (les photos envoyées depuis le téléphone arrivent dans `assets/photos/`) |

Sections de la page (attribut `id`), dans l'ordre : maison (présentation), carte (la carte en onglets Entrées / Plats / Desserts), midi (encadré du menu de midi, plat du jour dans `#plat-du-jour`), infos (horaires, plan, formulaire de réservation `#reserver`), concept. Le menu du haut
(`<nav id="menu">`) pointe vers ces `id`.

Chaque plat est une ligne `<div class="plat" id="i-…">` avec nom (`<b>`), description (`<small>`) et prix (`<span class="px">`), dans l'onglet de sa catégorie.

Bandeau d'annonce (fermeture exceptionnelle, soldes…) : le `<div class="annonce" id="annonce">`
juste après le bandeau noir du haut. Pour l'afficher, y mettre le texte et ajouter la classe `on`
(`<div class="annonce on" id="annonce">Texte</div>`).

Horaires : tableau `<table class="horaires">` dans la section `infos`.

## Ce qu'il ne faut pas casser

- Le bandeau noir du haut (« Exemple de site… commerce fictif ») et la section `concept`
  (téléphone simulé et liste `ACTIONS` dans le script) : ils servent à la démonstration.
- Garder le style existant (couleurs et polices définies dans `:root`) pour tout nouvel élément.
- Toute nouvelle image : texte `alt` descriptif et `loading="lazy"`.
- Ne pas toucher à `.nojekyll`.
