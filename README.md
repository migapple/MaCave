# 🍷 Cave à Vin

Application iOS de gestion de cave à vin, développée avec Capacitor (HTML/CSS/JS → iOS natif).

---

## 1.2.0
- ajout nos autres App

## Fonctionnalités

- **Gestion de la collection** — ajout, modification, suppression de bouteilles
- **Scanner de codes-barres** — identification automatique via Open Food Facts
- **Fiches détaillées** — couleur, millésime, région, appellation, cépage, prix, note, garde
- **Filtres & recherche** — par couleur, région, cépage, recherche texte accent-insensitive
- **Statistiques** — répartition par couleur, top régions, top cépages, par décennie
- **Sommelier** — conseils personnalisés basés sur la cave
- **Export/Import** — CSV et JSON, sauvegarde dans le dossier Fichiers iOS
- **Bilingue** — français 🇫🇷 / anglais 🇬🇧 avec bascule instantanée
- **Thème luxe** — palette crème et bordeaux, typographie Raleway/Playfair

---

## Stack technique

| Élément | Technologie |
|---|---|
| Frontend | HTML / CSS / JavaScript (vanilla) |
| iOS bridge | Capacitor 6 |
| Scanner | @capacitor-mlkit/barcode-scanning 6.0.0 |
| Filesystem | @capacitor/filesystem 6 |
| Base de données vins | Open Food Facts API (gratuit, sans clé) |
| Stockage local | localStorage |

---

## Structure du projet

```
cave-a-vin/
├── www/
│   └── index.html          ← app web (source = cave-a-vin.html)
├── ios/                    ← projet Xcode généré par Capacitor
├── cave-a-vin.html         ← fichier source principal
├── capacitor.config.json
├── package.json
└── README.md
```

---

## Installation & build

### Prérequis

- Node.js 20+
- Xcode 16+
- CocoaPods 1.12+ (`brew install cocoapods`)
- Compte Apple Developer

### Étapes

```bash
# 1. Installer les dépendances
npm install

# 2. Copier le source dans www/
cp cave-a-vin.html www/index.html

# 3. Synchroniser avec iOS
npx cap sync ios

# 4. Installer les pods
cd ios/App && pod install

# 5. Ouvrir Xcode
cd ../.. && npx cap open ios
```

### Info.plist requis

```xml
<key>NSCameraUsageDescription</key>
<string>Cave à Vin uses the camera to scan the barcode on wine bottles. This allows the app to automatically identify the wine and pre-fill details such as the name, producer, and country of origin.</string>

<key>UIFileSharingEnabled</key>
<true/>

<key>LSSupportsOpeningDocumentsInPlace</key>
<true/>

<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
</dict>
```

### capacitor.config.json — plugin HTTP requis

```json
"plugins": {
  "CapacitorHttp": {
    "enabled": true
  }
}
```

---

## Versions

| Version | Nouveautés |
|---|---|
| 1.1.0 | Scanner code-barres, lookup Open Food Facts, remplissage automatique fiche |
| 1.0.0 | Version initiale — gestion cave, stats, sommelier, export/import, bilingue |

---

## Auteur

Michel Garlandat — développement iOS indépendant  
Construit avec Capacitor · Publié sur l'App Store
