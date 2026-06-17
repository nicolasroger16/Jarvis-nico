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

### Étape 3 : Ajouter le résumé de mon agenda (si possible)

Si un connecteur calendrier (Google Calendar, etc.) est actif :
- Récupère mes événements de la journée
- Présente-les brièvement après la veille

Si aucun connecteur calendrier actif, ne mentionne rien sur l'agenda.

### Étape 4 : Analyser mes mails (si possible)

Si un connecteur Gmail est actif :
- Récupère les mails non lus des 3 derniers jours (inbox uniquement, pageSize 20)
- Filtre et classe selon 3 catégories :
  - **À faire aujourd'hui** : RDV, rappels urgents, paiements échoués, demandes avec deadline imminente
  - **À traiter bientôt** : sujets importants sans urgence immédiate (abonnements, renouvellements, opportunités)
  - **Info sécurité** : connexions inconnues, alertes compte
- Ignore tout ce qui est promotionnel, newsletter ou publicitaire (ne pas mentionner, ne pas compter)
- Si aucun mail pertinent, ne rien afficher dans cette section

Si aucun connecteur Gmail actif, ne mentionner rien sur les mails.

### Étape 5 : Veille scientifique PubMed (si connecteur disponible)

Si le connecteur PubMed est actif :
- Lancer 4 recherches en parallèle sur les publications récentes (30 derniers jours), 5 résultats max par recherche, triés par date :
  1. `fascia OR myofascial` (fascias et techniques myofasciales)
  2. `manual therapy OR osteopathic manipulative treatment` (thérapie manuelle et ostéopathie)
  3. `range of motion assessment OR mobility screening` (évaluation de la mobilité)
  4. `chronic pain AND manual therapy OR chronic musculoskeletal pain` (douleur chronique)
- Pour chaque article retenu, présenter : titre traduit en français, auteurs, journal, date, et en 1 ligne pourquoi c'est pertinent
- Garder uniquement 3 à 5 articles au total, les plus pertinents selon le contexte (approche evidence-based, fascias, pratique clinique, e-learning)
- Ne jamais inventer un article. Si aucun résultat pertinent, ne rien afficher dans cette section

Si le connecteur PubMed n'est pas actif, ne rien mentionner.

### Étape 6 : Présenter le tout dans un format unique

Format de sortie attendu :

```
☀️ Bonjour. Voici votre matinée.

📰 Votre veille du jour
[Résultat de la skill recherche-actualites-contextualisees]

📅 Votre agenda du jour (si connecteur disponible)
[Liste des événements de la journée]

📬 Vos mails à ne pas rater (si connecteur disponible)
🚨 À faire aujourd'hui
[Mails urgents avec action claire]

📌 À traiter bientôt
[Mails importants non urgents]

🔒 Info sécurité
[Alertes de connexion ou sécurité]

🔬 Votre veille scientifique (si connecteur PubMed disponible)
[3 à 5 articles récents filtrés et traduits, avec explication de pertinence]

🎯 Votre focus suggéré
[1 phrase qui propose le focus principal de la journée basé sur la veille + agenda + mails + recherche PubMed + projets en cours]

Bonne journée. Je suis prêt à vous aider.
```

---

## Règles importantes

- L'objectif de cette commande, c'est de remplacer 15 minutes de scroll matinal par 30 secondes de lecture utile
- Ne jamais dépasser 1 page de sortie, sinon c'est trop long pour une routine matinale
- Si quelque chose n'est pas disponible (pas de connecteur calendrier par exemple), ne pas le mentionner, juste passer à la section suivante
- Communication en français
- Pas de tirets longs (em dashes)
