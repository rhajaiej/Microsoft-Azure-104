# Labs Microsoft

Recueil de labs Microsoft (Azure, Microsoft Entra ID, Microsoft 365, etc.), réécrits selon un standard commun afin d'être faciles à suivre, à maintenir et à contribuer sur GitHub.

## Structure du repo

```
labs-microsoft/
├── README.md                          # Ce fichier : vue d'ensemble et index des labs
├── docs/
│   └── LAB_TEMPLATE.md                # Modèle vierge à copier pour créer un nouveau lab
└── labs/
    ├── 01-create-entra-id-tenant/
    │   ├── README.md                  # Contenu du lab
    │   └── images/                    # Captures d'écran référencées dans le README
    └── ...
```

Chaque lab vit dans son propre dossier sous `labs/`, numéroté et nommé en `kebab-case` (ex. `01-create-entra-id-tenant`). Le dossier contient un `README.md` qui suit le modèle défini dans [`docs/LAB_TEMPLATE.md`](docs/LAB_TEMPLATE.md), ainsi qu'un sous-dossier `images/` pour les captures d'écran.

## Index des labs

| # | Lab | Produit | Durée estimée |
|---|-----|---------|----------------|
| 01 | [Créer un tenant Microsoft Entra ID](labs/01-create-entra-id-tenant/README.md) | Microsoft Entra ID | 15 min |

## Conventions

- **Langue** : cohérente au sein d'un même lab (ne pas mélanger le français et l'anglais dans un même document).
- **Étapes** : toujours numérotées, une action par étape, verbe à l'infinitif ou à l'impératif (« Ouvrir », « Sélectionner »).
- **Éléments d'interface** : noms d'options, boutons et menus en **gras**, exactement comme ils apparaissent dans le produit.
- **Remarques importantes** : utiliser la syntaxe d'alerte GitHub (`> [!IMPORTANT]`, `> [!NOTE]`, `> [!TIP]`) plutôt que du texte en gras noyé dans un paragraphe.
- **Tableaux** : utiliser de vrais tableaux Markdown pour les paires *paramètre / valeur*, jamais de texte tabulé.
- **Captures d'écran** : nommées `NN-description.png`, stockées dans le dossier `images/` du lab, référencées avec un texte alternatif descriptif.
- **Nettoyage** : chaque lab se termine par une section listant les ressources à supprimer, si applicable.
