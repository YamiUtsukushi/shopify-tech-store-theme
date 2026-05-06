# 🛒 Shopify Theme — Tech & Electronics Store

Thème Shopify Online Store 2.0 basé sur Dawn, conçu pour une boutique high-tech (composants gaming, audio, smartphones, accessoires). Refonte complète de la fiche produit avec galerie sticky paginée, timer flash-sale dynamique, accordéon FAQ avec override par produit, et section "highlights" entièrement personnalisable via metafields.

---

## 🌐 Application déployée

🔗 **[Voir la boutique en ligne](https://test-perso-dev.myshopify.com/)** 
- **Si mot de passe demandé, c'est `test`**

---

## 🛠️ Stack technique

- **Shopify Online Store 2.0** — plateforme e-commerce
- **Liquid** — moteur de templating Shopify
- **HTML5 / CSS3** — markup sémantique et styles custom (architecture BEM)
- **JavaScript (Vanilla)** — galerie produit, compte à rebours, lecteur vidéo YouTube/Vimeo, accordéons
- **Theme Dawn** — thème de base Shopify
- **Shopify Metafields** — personnalisation granulaire par produit
- **Embed YouTube / Vimeo** — lecteur vidéo intégré dans la section highlights

---

## ✨ Fonctionnalités principales

### 🖼️ Page produit personnalisée
- **Galerie image custom** : image principale en haut, vignettes horizontales paginées (+N) avec swap visuel
- **Sticky gallery** : l'image reste fixe à gauche pendant le scroll des infos à droite (desktop)
- **Badges automatiques** : NEW (produit < 30 jours), X% OFF (calculé depuis le prix barré)
- **Timer flash-sale** : compte à rebours lié à un metafield produit, partagé avec la section Flash Sale
- **Layout achat optimisé** : Quantité + Add to Cart sur la même ligne, Buy It Now en pleine largeur
- **Bandeau "Avantages"** : 4 icônes configurables (Daily Deals, Return, Payment, Help)
- **FAQ accordéon** : 3 sections par défaut avec override par produit via metafields

### 🎬 Section Highlights produit
- 4 cartes en grille asymétrique (1 grande à gauche + 1 large en haut à droite + 2 petites en bas à droite)
- Support **YouTube / Vimeo / MP4** auto-détecté
- 20 metafields produit pour personnalisation totale (image, vidéo, titre, sous-titre, lien × 4 cartes)
- Tailles, couleurs, graisses du texte configurables par carte

### ⚡ Section Flash Sale
- Carrousel horizontal de produits en promotion
- Timer individuel par produit (lecture depuis metafield produit)
- Bannière "Deal Of The Day" avec timer principal
- Drag-to-scroll desktop et mobile

### 📱 Responsive complet
- **Desktop ≥ 901px** : layout 2 colonnes avec gallery sticky
- **Tablette 601–900px** : 1 colonne, vignettes 4 colonnes
- **Mobile ≤ 600px** : optimisations touch (boutons 44px+), grilles adaptées
- **Très petit mobile ≤ 380px** : 4 icônes en 2x2, breadcrumb tronqué

---

## 🚀 Installation rapide

### Prérequis
- Compte Shopify (boutique de test ou plan Partner)
- [Shopify CLI](https://shopify.dev/docs/themes/tools/cli) (recommandé)
- [Node.js ≥ 18](https://nodejs.org/) si tu utilises le CLI

### Méthode 1 — Upload direct via l'admin Shopify
1. Télécharge le repo en ZIP : `Code` → `Download ZIP`
2. Dans ton admin Shopify : **Boutique en ligne → Thèmes → Ajouter un thème → Téléverser un fichier ZIP**
3. Active le thème

### Méthode 2 — Via Shopify CLI (recommandée pour dev)

```bash
# Cloner le repo
git clone https://github.com/<ton-username>/<nom-du-repo>.git
cd <nom-du-repo>

# Lancer le serveur de dev
shopify theme dev --store=ta-boutique.myshopify.com
```

Le thème se synchronise automatiquement avec ta boutique de test.

### Configuration des metafields (étape obligatoire)

Pour activer toutes les fonctionnalités, configure ces metafields dans **Settings → Custom data → Products → Add definition** :

**Timer flash-sale**
- `custom.flash_sale_end_date` (Single line text, format `DD-MM-YYYYTHH:MM:SS`)

**FAQ overrides**
- `custom.faq_about` (Multi-line text)
- `custom.faq_details` (Multi-line text)
- `custom.faq_shipping` (Multi-line text)

**Highlights — 4 cartes × 5 champs = 20 metafields** *(optionnels, fallback sur les valeurs du customizer si vides)*

Pour chaque rôle (`left_main`, `right_top`, `right_small_1`, `right_small_2`) :
- `custom.highlight_<role>_image` (File — Image)
- `custom.highlight_<role>_video` (URL)
- `custom.highlight_<role>_heading` (Single line text)
- `custom.highlight_<role>_subheading` (Multi-line text)
- `custom.highlight_<role>_link` (URL)

> 💡 **Astuce** : active "Accès à la Storefront API" sur chaque metafield pour que Liquid puisse les lire.

---

## 📁 Structure du projet

```
.
├── sections/
│   ├── main-product.liquid        # Fiche produit refondue
│   ├── product-highlights.liquid  # Section "highlights" 4 cartes
│   ├── flash-sale.liquid          # Carrousel flash sale + DOTD
│   ├── header.liquid              # Header customisé
│   ├── footer.liquid
│   └── ...
├── snippets/
│   ├── buy-buttons.liquid
│   ├── price.liquid
│   ├── product-media.liquid
│   ├── card-product.liquid
│   └── ...
├── assets/
│   ├── product-page-custom.css    # Styles fiche produit
│   ├── product-gallery-custom.css # Styles galerie
│   ├── product-highlights.css     # Styles section highlights
│   ├── flash-sale.css             # Styles flash sale
│   └── ...
├── templates/
│   ├── product.json
│   ├── collection.json
│   └── ...
├── locales/
│   ├── en.default.json
│   └── fr.json
├── config/
│   ├── settings_data.json
│   └── settings_schema.json
└── README.md
```

---

## 📸 Aperçus

> 💡 *Prochainement*

| Desktop | Mobile |
|---|---|
| ![Desktop](docs/screenshots/desktop.png) | ![Mobile](docs/screenshots/mobile.png) |

---

## 🗺️ Roadmap

- [ ] Pages collection avec filtres avancés
- [ ] Lazy loading optimisé pour les vidéos YouTube
- [ ] Support du zoom image au hover sur la galerie
- [ ] Mode sombre
- [ ] Tests Lighthouse / Web Vitals optimisés

---

## 🧰 Compatibilité

- Shopify Online Store 2.0 (sections everywhere)
- Navigateurs modernes : Chrome, Firefox, Safari, Edge (versions récentes)
- Mobile : iOS Safari 14+, Chrome Android

---

## 📝 Licence

Ce projet est sous licence **MIT**. Voir le fichier `LICENSE` pour plus de détails.

> Le thème Dawn (base) est sous licence MIT par Shopify Inc.

---

## 👤 Auteur

Projet réalisé par **Jayson MOOKEN**
🔗 [LinkedIn](https://www.linkedin.com/in/jayson-mooken/)

---

⭐ Si ce projet t'a été utile, n'hésite pas à laisser une étoile sur le repo !
