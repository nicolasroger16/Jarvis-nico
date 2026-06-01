---
name: frontend-design
description: Skill de design frontend adapté au stack de Nico (HTML/CSS/JS, React, PWA). À utiliser quand l'utilisateur demande de concevoir une interface, créer un composant, améliorer le design d'une page, retravailler la typographie, proposer une palette de couleurs, ou auditer l'UI d'un projet existant. Couvre aussi les patterns PWA, le dark theme, et les interfaces mobiles Android.
---

# Skill : Frontend Design

## Mission

Produire des interfaces propres, cohérentes et adaptées aux projets de Nico. Pas de blabla théorique, pas de frameworks imposés inutilement. Le code livré doit être utilisable directement, dans le stack habituel : HTML/CSS/JS vanilla ou React, déployé sur Netlify, consulté sur Android.

---

## Phase 1 : Charger le contexte du projet

Avant de produire quoi que ce soit, identifier :

1. **Quel projet est concerné ?** (e-learning fascias, MoveCheck, app honoraires, nouveau projet)
2. **Quel stack est utilisé ?** (HTML/CSS/JS vanilla, React, PWA, ou mix)
3. **Y a-t-il déjà un design system ou une charte existante ?** (couleurs, typographie, dark theme)
4. **Quel est le support cible ?** (mobile Android prioritaire, desktop secondaire)
5. **Quel est l'objectif de l'utilisateur final ?** (apprendre, facturer, évaluer une mobilité, créer du contenu)

Si le contexte est flou, poser 1 ou 2 questions ciblées avant de produire.

---

## Phase 2 : Choisir l'approche

Selon la demande, adopter l'une de ces postures :

### A - Création from scratch
Concevoir un composant ou une page entière, en partant des besoins fonctionnels. Livrer du code prêt à l'emploi.

### B - Amélioration d'un existant
Analyser le code ou la description fournie, identifier les problèmes (espacement, hiérarchie visuelle, contraste, lisibilité), proposer des corrections ciblées.

### C - Audit UI rapide
Passer en revue une interface (code ou description) et lister les points à améliorer, classés par priorité (critique, important, nice-to-have).

### D - Système de design
Définir ou consolider une charte : couleurs, typographie, espacements, composants de base. Livrer sous forme de variables CSS ou de tokens React.

---

## Phase 3 : Principes de design à appliquer

Ces règles s'appliquent à tous les projets de Nico, sauf instruction contraire :

### Typographie
- Privilégier les polices lisibles en contexte médical et pédagogique : Inter, DM Sans, ou équivalent système
- Hiérarchie claire : titre principal, sous-titre, corps de texte, légende
- Line-height généreux pour la lecture longue (1.6 à 1.8 pour le corps)
- Taille minimale 16px sur mobile

### Couleurs
- Palette sobre et professionnelle, cohérente avec un contexte santé
- Support dark theme : utiliser des variables CSS (`--color-bg`, `--color-text`, etc.)
- Contraste minimum WCAG AA (4.5:1 pour le texte normal)
- Accents couleur utilisés avec parcimonie (1 couleur principale max)

### Espacement
- Système d'espacement cohérent basé sur une base 4px ou 8px
- Padding généreux sur mobile, sections bien séparées
- Pas de contenu collé aux bords de l'écran

### Composants
- Mobile-first systématiquement (Nico consulte sur Android)
- Touch targets minimum 44px de hauteur
- États interactifs clairs (hover, focus, active, disabled)
- Feedback visuel immédiat sur les actions (loading states, confirmations)

### PWA
- Icônes adaptées (maskable + purpose any)
- Splash screen cohérent avec la charte
- Offline state communiqué clairement à l'utilisateur
- Share sheet Android compatible (Web Share API)

---

## Phase 4 : Format de livraison

Selon la demande, livrer dans l'un de ces formats :

### Code directement utilisable
```html
<!-- Exemple de composant HTML/CSS -->
```
```jsx
// Exemple de composant React
```
```css
/* Variables CSS / tokens */
```

### Audit structuré
```
AUDIT UI — [Nom du projet]

Critique (à corriger avant mise en ligne)
- [Problème + correction proposée]

Important (améliore significativement l'expérience)
- [Problème + correction proposée]

Nice-to-have (polish)
- [Suggestion]
```

### Charte / tokens
```css
:root {
  /* Couleurs */
  --color-bg: ;
  --color-surface: ;
  --color-text: ;
  --color-accent: ;

  /* Typographie */
  --font-body: ;
  --font-size-base: ;
  --line-height-base: ;

  /* Espacement */
  --space-xs: ;
  --space-sm: ;
  --space-md: ;
  --space-lg: ;
  --space-xl: ;

  /* Radius */
  --radius-sm: ;
  --radius-md: ;
}
```

---

## Règles importantes

- **Pas de sur-engineering** : livrer ce qui est demandé, pas un design system complet si la question porte sur un bouton
- **Toujours expliquer les choix qui ne sont pas évidents** (une ligne max par choix)
- **Mobile-first obligatoire** pour tout ce qui sera consulté sur Android
- **Dark theme** : systématiquement penser aux deux modes quand on définit des couleurs
- **Ne pas inventer de dépendances** : rester dans le stack existant (pas de Tailwind si le projet est en CSS vanilla, pas de styled-components si le projet est en CSS modules)
- **Pas de tirets longs** dans les réponses
- **Communication en français**

---

## Références de projets actifs

Ces projets ont chacun leur identité visuelle, à respecter si une demande concerne l'un d'eux :

| Projet | Stack | Particularités |
|--------|-------|----------------|
| Module e-learning fascias | HTML/CSS/JS, SPA | Dark theme, navigation chapitres, suivi progression, schémas anatomiques |
| MoveCheck Content Studio | React | Theme chips, navigation par onglets, API Anthropic intégrée |
| App Notes d'honoraires | PWA (HTML/CSS/JS) | Génération PDF, share sheet Android, icône "NR", manifest installable |

Si la demande concerne un de ces projets, adapter le design à son identité existante plutôt que de repartir de zéro.
