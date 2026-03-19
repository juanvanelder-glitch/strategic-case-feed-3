# Strategy Case Feed 📱

Feed swipeable de business cases stratégie pour la préparation aux case interviews.

- **Swipe ↕** → changer de case
- **Swipe ↔** → naviguer les étapes (Contexte → Framework → Deep Dive → Brainstorm → Pitch)
- **Clavier** → flèches directionnelles

## Quick Start (local)

```bash
npm install
npm run dev
```

Ouvre http://localhost:5173 sur ton navigateur.

## Déployer sur Vercel (gratuit)

### Option 1 : Via GitHub (recommandé)

1. Crée un repo GitHub et push le code :
```bash
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/TON-USERNAME/strategy-case-feed.git
git push -u origin main
```

2. Va sur [vercel.com](https://vercel.com), connecte ton compte GitHub
3. Clique "Import Project" → sélectionne le repo
4. Framework Preset : **Vite** (auto-détecté)
5. Clique "Deploy" → c'est live en 30 secondes

### Option 2 : Via Vercel CLI

```bash
npm i -g vercel
vercel
```

Suis les prompts. C'est déployé.

## Installer comme app mobile (PWA)

Une fois déployé sur Vercel, ouvre l'URL sur ton téléphone :

- **iPhone** : Safari → bouton "Partager" → "Sur l'écran d'accueil"
- **Android** : Chrome → menu ⋮ → "Installer l'application"

L'app fonctionne offline et se lance comme une app native.

## Ajouter des cases

Édite `src/StrategyFeed.jsx`, dans le tableau `CASES`. Chaque case a cette structure :

```js
{
  id: 6,
  source: "consultor",         // clé de SOURCES
  category: "Strategy / Tech",
  title: "Titre du case",
  date: "Mars 2026",

  contexte: {
    body: "Le prompt client...",
    keyFact: "Chiffre clé",
    clarifyingQs: [
      { q: "Question ?", a: "Réponse du partner" },
    ],
  },

  framework: {
    name: "Nom du framework custom",
    why: "Pourquoi ce framework est pertinent pour ce case",
    branches: [
      {
        label: "Branche 1",
        children: [
          { label: "Sous-élément", detail: "Description" },
        ],
      },
    ],
  },

  deepDive: {
    chosenBucket: "Nom du bucket choisi",
    whyThisBucket: "Pourquoi on priorise ce bucket",
    matchAnalysis: [
      { dimension: "Nom", caseMatch: "Comment ça matche avec les données", severity: "critique" },
      // severity: "critique" | "haut" | "moyen" | "quick-win" | "avantage-fort" | "neutre"
    ],
  },

  brainstorm: {
    subProblem: "La sous-problématique issue du deep dive",
    ideas: [
      { idea: "Nom", detail: "Description", impact: "Fort", feasibility: "Fort" },
      // impact/feasibility: "Fort" | "Moyen" | "Faible"
    ],
  },

  elevatorPitch: {
    recommendation: "La reco en une phrase",
    arguments: ["Argument 1", "Argument 2", "Argument 3"],
    risks: [
      { risk: "Description du risque", mitigation: "Comment le mitiger" },
    ],
    nextSteps: ["Step 1 avec timeline", "Step 2", "Step 3", "Step 4"],
  },
}
```

## Stack technique

- **React 18** — composants fonctionnels + hooks
- **Vite 6** — build ultra-rapide
- **vite-plugin-pwa** — Progressive Web App (installable, offline)
- **Zero dependencies** — pas de framework UI, que du CSS-in-JS natif

## Prochaines étapes (roadmap)

- [ ] Connecter à un backend (Supabase/Firebase) pour l'actualisation auto
- [ ] Scraper RSS Consultor/L'Écho/FT + Claude API pour générer des cases
- [ ] Ajouter un mode "practice" (cacher les réponses, timer)
- [ ] Push notifications pour les nouveaux cases
- [ ] Bookmarks / favoris
