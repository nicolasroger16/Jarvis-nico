# /morning

> Commande raccourci pour démarrer votre journée en 30 secondes avec une veille personnalisée.

---

## Mission

Quand je lance `/morning`, exécute la séquence complète suivante en utilisant la skill **recherche-actualites-contextualisees**.

### Étape 1 : Charger mon contexte

Lis silencieusement :
1. `CLAUDE.md`
2. `context/CONTEXT.md`
3. `context/HISTORY.md`

Pas besoin de me résumer le contexte, je le connais. Charge juste pour bien filtrer la veille.

### Étape 2 : Effectuer la veille du jour

Lance la skill `recherche-actualites-contextualisees` avec ces paramètres par défaut :
- Périmètre : actualités IA + actualités de mon secteur d'activité
- Filtre : selon mon contexte chargé
- Format : présentation matinale claire

### Étape 3 : Vérifier les mails importants (si possible)

Si un connecteur Gmail est actif :
- Récupère les mails non lus des dernières 48h avec la query : `is:unread in:inbox newer_than:2d`
- Filtre : ne garder que les mails pertinents (patients, confrères, formations, outils pro, actualités santé/IA). Ignorer les newsletters génériques, promos e-commerce, réseaux sociaux
- Présente uniquement les mails qui nécessitent une action ou qui sont informatifs pour la journée

Si aucun connecteur Gmail actif, ne mentionner rien.

### Étape 4 : Ajouter le résumé de mon agenda (si possible)

Si un connecteur calendrier (Google Calendar, etc.) est actif :
- Récupère mes événements de la journée
- Présente-les brièvement

Si aucun connecteur calendrier actif, ne mentionner rien.

### Étape 5 : Présenter le tout dans un format unique

Format de sortie attendu :

```
☀️ Bonjour. Voici ta matinée.

📰 Veille du jour
[Résultat de la skill recherche-actualites-contextualisees]

📧 Mails à traiter (si connecteur disponible)
[Liste filtrée des mails importants]

📅 Agenda du jour (si connecteur disponible)
[Liste des événements de la journée]

🎯 Focus suggéré
[1 phrase qui propose le focus principal de la journée basé sur la veille + mails + agenda + projets en cours]

Bonne journée. Je suis prêt à t'aider.
```

---

## Règles importantes

- L'objectif de cette commande, c'est de remplacer 15 minutes de scroll matinal par 30 secondes de lecture utile
- Ne jamais dépasser 1 page de sortie, sinon c'est trop long pour une routine matinale
- Si quelque chose n'est pas disponible (pas de connecteur calendrier par exemple), ne pas le mentionner, juste passer à la section suivante
- Communication en français
- Pas de tirets longs (em dashes)
