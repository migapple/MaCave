# 🍷 Cave à Vin — Setup Capacitor iOS

## Structure du projet

```
cave-a-vin/
├── www/
│   └── index.html          ← Le fichier cave-a-vin.html renommé
├── package.json
├── capacitor.config.json
└── SETUP_CAPACITOR.md
```

---

## 1. Préparer le dossier

```bash
mkdir cave-a-vin
cd cave-a-vin

# Copier les fichiers fournis
cp package.json .
cp capacitor.config.json .

# Créer le dossier www et y placer le HTML
mkdir www
cp cave-a-vin.html www/index.html
```

---

## 2. Installer les dépendances

```bash
npm install
```

---

## 3. Initialiser Capacitor

```bash
npx cap init "Cave à Vin" "com.michelparet.caveaVin" --web-dir www
```

---

## 4. Ajouter la plateforme iOS

```bash
npx cap add ios
```

---

## 5. Synchroniser

```bash
npx cap sync ios
```

---

## 6. Ouvrir dans Xcode

```bash
npx cap open ios
```

---

## 7. Configuration Xcode

Dans Xcode, vérifier / modifier :

| Réglage | Valeur |
|---|---|
| Bundle Identifier | `com.michelparet.caveaVin` |
| Display Name | `Cave à Vin` |
| Deployment Target | iOS 14.0+ |
| Version | 1.0 |
| Build | 1 |

### Icône de l'app
Ajouter une icône 🍷 dans `Assets.xcassets > AppIcon` (1024×1024 px minimum).

### Couleur de fond au lancement
Dans `App/App/Info.plist`, vérifier que `UIBackgroundColor` est `#1A0A0E`.

---

## 8. Test sur simulateur

Dans Xcode : `Cmd + R` sur un iPhone 15 Pro ou similaire.

---

## 9. Soumission App Store

1. **App Store Connect** → Créer une nouvelle app `Cave à Vin`
2. Dans Xcode : `Product > Archive`
3. `Distribute App > App Store Connect`
4. Compléter la fiche App Store :
   - Catégorie : `Food & Drink` ou `Lifestyle`
   - Description : Gérez votre cave à vin facilement…
   - Screenshots : iPhone 6.7" requis
5. Soumettre pour review

---

## Notes importantes

- Les données sont stockées en **localStorage** (WKWebView) — elles persistent entre les sessions
- Le plugin `@capacitor/keyboard` évite que le clavier recouvre les champs du formulaire
- `StatusBar` en mode `DARK` pour correspondre au fond sombre de l'app
- `contentInset: always` gère le notch et la Dynamic Island automatiquement

---

## Mises à jour futures

Pour toute modification du HTML :

```bash
# Modifier www/index.html
npx cap sync ios
# Puis re-build dans Xcode
```
