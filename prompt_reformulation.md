# PROMPT : Reformuler le contenu d'un site existant

## Contexte

J'ai un site vitrine statique existant pour une entreprise d'un métier donné. Je veux créer un **nouveau site pour une autre entreprise du même métier**, dans un **nouveau département / nouvelle zone géographique**, avec de **nouvelles villes d'intervention**.

Le site source sert de **modèle**. On garde la même structure HTML, le même design, le même CSS, le même JavaScript et la même stratégie SEO (mêmes mots-clés métier). On change :
- **L'entreprise** (nom, coordonnées, SIRET, images, mentions légales)
- **La zone géographique** (département, région, villes d'intervention)
- **Tout le contenu textuel** (reformulé pour être 100% unique)
- **Les noms de fichiers HTML** (adaptés au nouveau département/villes)

**Objectif** : Obtenir un site au contenu 100% unique, avec les informations de la nouvelle entreprise, sur la nouvelle zone géographique, tout en conservant la même structure, le même design et la même stratégie SEO par mots-clés.

---

## 1. INFORMATIONS A FOURNIR AVANT DE COMMENCER

Avant de lancer la reformulation, fournir :

- [ ] **Chemin / dossier du site existant** (le dossier contenant tous les fichiers HTML, CSS, JS, images)
- [ ] **Confirmation du périmètre** : reformuler toutes les pages ou seulement certaines ? (par défaut : toutes)
- [ ] **Informations de la nouvelle entreprise** (obligatoire) :
  - [ ] **Nom de l'entreprise**
  - [ ] **Forme juridique** (SASU, SARL, auto-entrepreneur...)
  - [ ] **Adresse complète**
  - [ ] **SIRET / RCS**
  - [ ] **Téléphone mobile** (ex: 07 XX XX XX XX)
  - [ ] **Téléphone fixe** (ex: 09 XX XX XX XX) — si applicable
  - [ ] **Email**
  - [ ] **Horaires d'ouverture** (détail par jour)
  - [ ] **Liens réseaux sociaux** (LinkedIn, Instagram, Facebook, etc.)
  - [ ] **Clé webhook WebPrime** (pour le formulaire)
  - [ ] **Nom de domaine** du nouveau site
- [ ] **Nouvelle zone géographique** (obligatoire) :
  - [ ] **Numéro de département** (ex: 78)
  - [ ] **Nom du département / région** (ex: Yvelines)
  - [ ] **Liste des 20 villes d'intervention** (pour les pages villes)
- [ ] **Images de la nouvelle entreprise** (obligatoire, **toutes en format WebP**) :
  - [ ] **Logo** (WebP, < 15 KB) — nom de fichier fourni
  - [ ] **Image héro** (fond du bandeau principal, WebP, < 30 KB) — nom de fichier fourni
  - [ ] **Images services** (1 par service, WebP, < 80 KB) — noms de fichiers fournis
  - [ ] **Image zone d'intervention** (carte du département, WebP, < 80 KB) — nom de fichier fourni
  - [ ] **Photos page entreprise** (véhicules + réalisations, WebP, < 80 KB) — noms de fichiers fournis. Le nombre de photos dépend du site source (observer la page entreprise existante)
  - [ ] **Logos partenaires/certifications** (WebP, < 10 KB chacun) — noms de fichiers fournis. Le nombre dépend du site source
  - [ ] **Favicons** (favicon.ico, apple-touch-icon, android-icon, ms-icon) — fichiers fournis
- [ ] **Mentions légales** :
  - [ ] Nom du responsable de publication
  - [ ] Hébergeur (nom, adresse, site)
- [ ] **Éléments spécifiques à modifier** (au-delà de la reformulation) : si certaines sections doivent être ajoutées, supprimées ou restructurées, le préciser ici. Sinon, seule la reformulation est appliquée.

> **IMPORTANT — Toutes les images doivent être fournies en WebP.** Si le site source utilise d'autres formats (AVIF, PNG, JPG), les nouvelles images seront en WebP et les `src` dans le HTML seront mis à jour avec les nouveaux noms de fichiers .webp.

> **RENOMMAGE DES IMAGES** : Les fichiers images seront **renommés automatiquement** selon la convention `mot-clé-département.webp` (cf. section 4.7.1). Les noms de fichiers fournis ci-dessous sont indicatifs — l'IA déterminera les noms finaux en fonction du mot-clé métier associé à chaque image et du nouveau département.

> **Tout ce qui est dans cette liste doit être fourni AVANT de commencer.** L'IA remplace les anciennes infos/images par les nouvelles et reformule tout le contenu textuel.

---

## 2. INVENTAIRE DES PAGES A CREER (à partir du site source)

Le site source contient les types de pages suivants. Chaque page est **dupliquée avec un nouveau nom de fichier** adapté au nouveau département/villes, puis le contenu est reformulé.

| Type de page | Nom fichier source (exemple) | Nom fichier cible (nouveau dept) | Action |
|--------------|------------------------------|----------------------------------|--------|
| **Page d'accueil** | `index.html` | `index.html` | Reformuler contenu + remplacer infos entreprise |
| **Page entreprise** | `[nom]-95-val-doise.html` | `[nouveau-nom]-[dept]-[region].html` | Renommer + reformuler + remplacer infos |
| **Pages services** (N) | `[service]-95.html` | `[service]-[dept].html` | Renommer + reformuler. **Le nombre de services (N) varie** selon le site source — reproduire exactement le même nombre de pages services |
| **Page prix / devis** | `devis-pour-[metier]-95.html` | `devis-pour-[metier]-[dept].html` | Renommer + reformuler |
| **Pages villes** (20) | `[metier]-[ville].html` | `[metier]-[nouvelle-ville].html` | **Toujours 20 pages**, créées à partir de l'index avec les nouvelles villes + contenu unique par ville |
| **Mentions légales** | `mentions-legales.html` | `mentions-legales.html` | Remplacer les infos entreprise |

**Total** : 4 pages principales + N pages services + 20 pages villes + mentions légales.

> **Le nombre de pages services (N) est variable.** Lire le site source pour compter le nombre exact de pages services. Reproduire exactement le même nombre.

### Ce qui change dans les noms de fichiers :
- Le **numéro de département** (ex: `95` → `78`)
- Le **nom de la région** (ex: `val-doise` → `yvelines`)
- Le **nom de l'entreprise** (dans le fichier page entreprise)
- Les **noms des villes** (20 nouvelles villes pour les pages villes)
- Les services restent les mêmes (même métier) donc les noms de services dans les URLs ne changent pas

### Fichiers techniques à régénérer :

| Fichier | Consigne |
|---------|----------|
| **Sitemap.xml** | Régénérer entièrement avec les nouvelles URLs (nouveau domaine, nouveaux noms de fichiers, nouvelles images .webp). Les `<image:caption>` et `<image:title>` sont des textes descriptifs : les **reformuler** en gardant les mots-clés métier |
| **Robots.txt** | Mettre à jour l'URL du sitemap avec le nouveau domaine |
| **CNAME** | Mettre à jour avec le nouveau nom de domaine |

> **Instruction** : Avant de commencer, lire TOUTES les pages HTML du site source pour identifier chaque fichier et son type. Lister les fichiers trouvés et mapper chaque fichier source vers son fichier cible.

---

## 3. CE QUI NE DOIT PAS CHANGER

### 3.1 Fichiers à ne pas toucher du tout

| Fichier / élément | Raison |
|--------------------|--------|
| **style.css** | Le design ne change pas |
| **JavaScript** (scripts inline sur chaque page) | Le comportement ne change pas. **Seules exceptions** : l'URL du webhook WebPrime et l'URL de redirection après envoi du formulaire — à remplacer |

### 3.2 Fichiers à remplacer (fournis par le client)

| Fichier / élément | Consigne |
|--------------------|----------|
| **Images** (logo, héro, services, réalisations, véhicules, carte zone) | Remplacer par les nouveaux fichiers **WebP**. Mettre à jour les `src` dans le HTML avec les nouveaux noms de fichiers |
| **Favicons** (favicon.ico, apple-touch-icon, android-icon, ms-icon) | Remplacer par les nouveaux fichiers fournis |
| **Logos partenaires** | Remplacer par les nouveaux logos fournis |

### 3.3 Éléments HTML à ne pas modifier dans chaque page

Ne pas modifier la structure HTML, les attributs techniques (`id`, `class`, `loading`, `decoding`, metas techniques) ni la structure du formulaire (champs, `name`, `value`, honeypot). Le layout, le CSS et le JS restent identiques.

### 3.4 Éléments HTML à ADAPTER au nouveau département / nouvelles villes

| Élément | Consigne |
|---------|----------|
| **Balises `<title>`** | Remplacer l'ancien département/région par le nouveau (ex: "95 Val-d'Oise" → "78 Yvelines"). **Garder les mêmes mots-clés métier**, ne changer que la localisation |
| **Balises `<h1>`** | Identiques aux `<title>`, même remplacement |
| **`<link rel="canonical">`** | Mettre à jour avec la nouvelle URL (nouveau domaine + nouveau nom de fichier) |
| **`<link rel="preload">`** | Mettre à jour avec le nom du nouveau fichier image héro (.webp) |
| **URLs / liens `href` internes** | Mettre à jour tous les liens internes pour pointer vers les nouveaux noms de fichiers |
| **Liens `tel:`** | Remplacer par le(s) nouveau(x) numéro(s) de téléphone (mobile ET fixe si les 2 existent dans le site source) |
| **Liens `mailto:`** | Remplacer par le nouvel email |
| **Liens réseaux sociaux** | Remplacer par les nouveaux liens fournis |
| **Webhook URL** dans le JS du formulaire | Remplacer par la nouvelle clé webhook |
| **URL de redirection** après envoi du formulaire (`window.location.href`) | Remplacer par le nouveau domaine |
| **JSON-LD LocalBusiness** — voir détail ci-dessous | Adapter tous les champs |

### 3.4.1 Détail JSON-LD LocalBusiness — champs à adapter par page

Le JSON-LD LocalBusiness change d'une page à l'autre dans le site source. Voici les champs à adapter :

| Champ JSON-LD | Consigne |
|----------------|----------|
| `"name"` | Remplacer par le nouveau nom d'entreprise + localisation |
| `"description"` | **Reformuler** le texte (c'est du texte libre, pas un mot-clé). Garder les mots-clés métier à l'intérieur |
| `"url"` | Mettre à jour avec la nouvelle URL de la page |
| `"telephone"` | Remplacer par le nouveau téléphone |
| `"address"` (streetAddress, addressLocality, addressRegion, postalCode) | Remplacer par la nouvelle adresse |
| `"image"` (array) | Mettre à jour les URLs des images avec les nouveaux noms de fichiers .webp et le nouveau domaine |
| `"hasOfferCatalog"."name"` | **Reformuler** ce texte (ex: "Nos services de couverture et rénovation" → "Nos prestations de couverture et rénovation"). C'est du texte libre |
| `"hasOfferCatalog"."itemListElement"` (Offers) | **Garder les mêmes `name`** (ce sont des mots-clés). Mettre à jour les `url` avec le nouveau domaine |
| `"areaServed"."name"` | Remplacer par le nouveau département |

> **IMPORTANT** : Le nombre d'Offers dans le JSON-LD **varie d'une page à l'autre** (l'accueil peut en avoir 15+, une page service peut en avoir 3-5). Reproduire exactement le même nombre et les mêmes mots-clés `name`, seules les URLs changent.

### 3.5 Textes SEO à ne pas modifier (MOTS-CLÉS MÉTIER)

| Élément | Raison |
|---------|--------|
| **Mots-clés métier dans les `alt` des images** | Mots-clés SEO optimisés pour le métier (même métier = mêmes mots-clés). Adapter uniquement la localisation (dept/ville) |
| **Mots-clés métier dans les `title` des images et des liens** | Idem |
| **Noms de services dans les Offers du JSON-LD** | Même métier = mêmes services = mêmes mots-clés |
| **Options du `<select>` prestations** dans le formulaire | Ce sont des noms de services = mots-clés |

### 3.6 Textes d'interface (UI) à ne pas modifier

Les textes des boutons, de la navigation et des CTA sont ceux du site source. **Les garder identiques** — ils sont liés aux liens, au JS et à la conversion.

### 3.7 Informations factuelles à REMPLACER par celles de la nouvelle entreprise

Toutes les informations de l'ancienne entreprise doivent être remplacées par celles fournies dans la section 1 :

| Élément | Consigne |
|---------|----------|
| Nom de l'entreprise | Remplacer partout (header, footer, JSON-LD, mentions légales, textes) |
| Adresse complète | Remplacer dans le footer, mentions légales, JSON-LD |
| Téléphone mobile | Remplacer dans le footer, bouton flottant, liens `tel:`, JSON-LD, hero |
| Téléphone fixe (si applicable) | Remplacer dans le footer, liens `tel:` correspondants. Si le site source a 2 numéros (mobile + fixe), le nouveau site doit aussi en avoir 2 |
| Adresse email | Remplacer dans le footer, liens `mailto:` |
| SIRET / RCS | Remplacer dans les mentions légales |
| Horaires d'ouverture (détail par jour) | Remplacer dans le footer |
| Liens réseaux sociaux | Remplacer les URLs dans le footer |
| Webhook WebPrime | Remplacer l'URL du webhook dans le JS du formulaire |
| URL de redirection formulaire | Remplacer `window.location.href` avec le nouveau domaine |
| Copyright | Mettre l'**année en cours** (ne pas copier l'année du site source). Garder "Site réalisé par webprime" |

### 3.8 Éléments à ne PAS modifier malgré le changement d'entreprise

| Élément | Raison |
|---------|--------|
| Noms des services | Même métier, mêmes services proposés |
| Mots-clés SEO métier (dans alt, title images, Schema.org Offers) | La stratégie SEO par mots-clés métier reste la même. Seule la localisation (dept/ville) change dans ces éléments |

---

## 4. CE QUI DOIT ETRE REFORMULE

### 4.1 Sur TOUTES les pages (principales + pages villes)

| Élément à reformuler | Consigne |
|-----------------------|----------|
| **`<meta name="description">`** | Réécrire (120-160 caractères). Garder les mêmes mots-clés mais reformuler la phrase autour |
| **Balises `<h2>`** (titres de sections) | Reformuler pour dire la même chose autrement. Garder les mots-clés métier dans le titre |
| **Balises `<h3>`** (sous-sections) | Reformuler en gardant les mots-clés principaux du service |
| **Titre de section FAQ** (H2 au-dessus des FAQ) | Reformuler (ex: "QUESTIONS FREQUENTES" → "VOS INTERROGATIONS LES PLUS COURANTES") |
| **Titre au-dessus du formulaire** (si présent) | Reformuler le texte d'introduction du formulaire |
| **Paragraphes descriptifs** | Réécrire chaque paragraphe. **Garder approximativement la même longueur** (±20% du nombre de mots) |
| **Textes des cartes de services** (descriptions courtes dans les `<h3>` des cartes) | Reformuler chaque description |
| **Sections alternées texte/image** | Réécrire tous les textes descriptifs |
| **Section équipement / savoir-faire** | Reformuler entièrement |
| **Section tarifs** (texte d'accroche, pas le bouton CTA) | Reformuler le texte descriptif |
| **Section valeurs / engagements** | Réécrire avec de nouvelles tournures |
| **Section types de contrats / offres** | Reformuler les descriptions (pas les noms de services si ce sont des mots-clés) |
| **Questions FAQ** (`<summary>`) | Reformuler chaque question (même thème, mots différents) |
| **Réponses FAQ** (contenu des `<details>`) | Réécrire chaque réponse entièrement. Garder la même longueur |
| **JSON-LD FAQPage** (questions et réponses) | **Doit correspondre EXACTEMENT au contenu FAQ visible sur la page** (copier-coller depuis les FAQ reformulées) |
| **JSON-LD LocalBusiness `"description"`** | Reformuler (texte libre). Garder les mots-clés métier |
| **JSON-LD `"hasOfferCatalog"."name"`** | Reformuler (texte libre) |

### 4.2 Page entreprise (en plus des éléments ci-dessus)

| Élément | Consigne |
|---------|----------|
| **Section histoire** | Réécrire le texte de présentation. Garder les mêmes faits (date de création, spécialisations) |
| **Section réalisations** | Reformuler les descriptions |
| **Section engagement / équipe** | Reformuler les textes sur les valeurs et l'équipe |
| **Section équipe** (présentation) | Reformuler le texte de présentation de l'équipe |

### 4.3 Pages services (en plus des éléments communs)

| Élément | Consigne |
|---------|----------|
| **Blocs H3 + paragraphes descriptifs** par page service | Reformuler toutes les sous-sections descriptives. **Le nombre de blocs varie** selon la page — reproduire exactement le même nombre que dans le site source. Garder les mots-clés du service dans les H3 |
| **FAQ spécifiques au service** | Reformuler questions et réponses. **Le nombre de FAQ varie** selon la page — reproduire le même nombre que dans le site source |

### 4.4 Page prix / devis (en plus des éléments communs)

| Élément | Consigne |
|---------|----------|
| **Section philosophie tarifaire** | Réécrire l'explication des prix et critères |
| **FAQ sur les tarifs** | Reformuler questions et réponses |

### 4.5 Pages villes (20 pages)

**Toujours créer 20 pages villes**, une par ville de la liste fournie dans la section 1. Chaque page ville est une adaptation de la page d'accueil pour une ville spécifique.

| Élément | Consigne |
|---------|----------|
| **`<meta description>`** | Unique par ville, reformulée |
| **Tous les H2 et H3** | Reformulés en gardant le nom de la ville |
| **Tous les paragraphes** | Reformulés avec des tournures différentes, le nom de la ville intégré naturellement |
| **Titre de section FAQ** | Reformulé avec la ville |
| **Titre au-dessus du formulaire** | Reformulé avec la ville |
| **FAQ par ville** | Questions et réponses reformulées avec la ville (même nombre de FAQ que l'index) |
| **JSON-LD FAQPage** | Correspond exactement au contenu FAQ visible |
| **JSON-LD LocalBusiness** | `addressLocality` = nom de la ville, `url` = URL de la page ville, `description` reformulée avec la ville |

**IMPORTANT** : Les 20 pages villes doivent toutes avoir un contenu différent entre elles ET différent du site source. Double reformulation.

### 4.6 Mentions légales (`mentions-legales.html`)

| Élément | Consigne |
|---------|----------|
| **Nom de l'entreprise** | Remplacer par la nouvelle entreprise |
| **Forme juridique** | Remplacer (SASU, SARL, etc.) |
| **Adresse** | Remplacer par la nouvelle adresse |
| **SIRET / RCS** | Remplacer par les nouveaux numéros |
| **Responsable de publication** | Remplacer par le nouveau nom |
| **Hébergeur** | Mettre à jour si changement (nom, adresse, site) |
| **Le reste de la structure** | Ne pas toucher (la structure HTML des mentions légales reste identique) |

> Les mentions légales ne sont pas "reformulées" au sens créatif du terme. On **remplace** les informations factuelles de l'ancienne entreprise par celles de la nouvelle.

### 4.7 Images — Renommage des fichiers et mise à jour des références dans le HTML

Toutes les nouvelles images sont en **WebP**.

#### 4.7.1 Renommage des fichiers images

Les fichiers images doivent être **renommés** selon la convention `mot-clé-département.webp` :

| Cas | Règle | Exemple |
|-----|-------|---------|
| **Le nom de fichier contient déjà un mot-clé métier + ancien département** | Remplacer uniquement le numéro de département | `reparation-toiture-95.webp` → `reparation-toiture-78.webp` |
| **Le nom de fichier contient un mot-clé métier sans département** | Ajouter le nouveau département | `nettoyage-toiture.webp` → `nettoyage-toiture-78.webp` |
| **Le nom de fichier est générique** (ex: `hero.webp`, `img1.webp`, `photo-entreprise.webp`) | Renommer avec le mot-clé principal correspondant au contenu de l'image + nouveau département | `hero.webp` → `couvreur-78.webp` |
| **Logo** | Renommer avec le nom de l'entreprise (pas de département) | `logo.webp` → `logo-nom-entreprise.webp` |
| **Carte zone d'intervention** | Renommer avec le département | `carte.webp` → `zone-intervention-78.webp` |
| **Favicons** | **Ne pas renommer** (noms standards obligatoires) | `favicon.ico` reste `favicon.ico` |
| **Logos partenaires / certifications** | **Ne pas renommer** (noms indépendants du département) | Garder les noms fournis |

> **IMPORTANT** : Après le renommage, **tous les `src`**, `preload`, JSON-LD `"image"` et sitemap `<image:loc>` doivent être mis à jour avec les nouveaux noms de fichiers.

#### 4.7.2 Mise à jour des références dans le HTML

| Élément à mettre à jour | Consigne |
|--------------------------|----------|
| **Attributs `src`** de toutes les `<img>` | Pointer vers les fichiers .webp **renommés** selon la convention ci-dessus |
| **`<link rel="preload" href="...">`** dans le `<head>` | Mettre à jour avec le nouveau nom du fichier héro .webp |
| **Favicons** (`<link rel="icon">`, `<link rel="apple-touch-icon">`, etc.) | Mettre à jour les chemins |
| **`alt` et `title` des images** | **NE PAS MODIFIER les mots-clés métier** — seule la localisation (dept/ville) change |
| **`title` des liens** | **NE PAS MODIFIER les mots-clés métier** — seule la localisation (dept/ville) change |
| **JSON-LD `"image"` array** | Mettre à jour les URLs avec le nouveau domaine et les nouveaux noms de fichiers .webp renommés |

### 4.8 Sitemap — Mise à jour

| Élément | Consigne |
|---------|----------|
| **`<loc>`** de chaque URL | Nouveau domaine + nouveaux noms de fichiers |
| **`<lastmod>`** | Mettre la date du jour |
| **`<image:loc>`** | Nouveau domaine + nouveaux noms de fichiers images .webp |
| **`<image:caption>`** | **Reformuler** les phrases descriptives en gardant les mots-clés métier |
| **`<image:title>`** | **Garder les mêmes** (ce sont des mots-clés métier) |
| **Ajouter les 20 pages villes** | Chaque page ville doit avoir son entrée `<url>` dans le sitemap |

---

## 5. DISTINCTION MOT-CLÉ vs TEXTE LIBRE

C'est la règle la plus importante pour ne pas casser le SEO.

### 5.1 Qu'est-ce qu'un mot-clé ?

Un **mot-clé** est une expression SEO choisie stratégiquement pour le référencement. On les trouve dans :
- Les `<title>` et `<h1>` (identiques entre eux)
- Les `alt` et `title` des images
- Les `title` des liens (`<a title="...">`)
- Les `name` des Offers dans le JSON-LD LocalBusiness
- Les options du `<select>` du formulaire
- Les noms de services quand ils apparaissent comme **titre de carte** ou **titre de lien**
- Les `<image:title>` dans le sitemap

**Les mots-clés NE SE REFORMULENT PAS.** Seule la localisation (département/ville) est remplacée.

### 5.2 Qu'est-ce qu'un texte libre ?

Un **texte libre** est un paragraphe, une description, une explication rédigée en langage naturel. On les trouve dans :
- Les paragraphes `<p>`
- Les descriptions de services (corps de texte)
- Les réponses de FAQ
- Les textes de sections (valeurs, tarifs, histoire, etc.)
- Les meta descriptions
- Les `"description"` dans le JSON-LD LocalBusiness
- Les `"hasOfferCatalog"."name"` dans le JSON-LD
- Les `<image:caption>` dans le sitemap

**Les textes libres SE REFORMULENT.**

### 5.3 Cas ambigus — règle à suivre

| Situation | Règle |
|-----------|-------|
| Un mot-clé apparaît **dans** un paragraphe de texte libre | **Garder le mot-clé**, reformuler le reste de la phrase autour |
| Un H2 contient un mot-clé métier | Reformuler la structure du H2, **garder le mot-clé** à l'intérieur |
| Un H3 est un nom de service | **Garder le nom du service** dans le H3, reformuler les mots autour si possible |
| Une FAQ contient un mot-clé dans la question | **Garder le mot-clé**, reformuler la tournure de la question |
| Un `<strong>` dans une carte service est un nom de service | **Ne pas reformuler** le nom du service dans le `<strong>` |

**Exemple concret :**

Original :
> "Notre entreprise de **réparation toiture** intervient dans tout le département pour un résultat durable."

Reformulé :
> "Spécialisés dans la **réparation toiture**, nous assurons des interventions de qualité sur l'ensemble du département."

→ Le mot-clé "réparation toiture" est conservé. Le reste de la phrase est reformulé.

---

## 6. REGLES DE REFORMULATION

### 6.1 Principes obligatoires

1. **Même sens, mots différents** : Chaque phrase reformulée doit transmettre exactement la même information
2. **Garder les mots-clés stratégiques** dans le texte (cf. section 5)
3. **Ne pas inventer d'informations** : Ne pas ajouter de services, de promesses ou de détails qui n'existent pas dans la version originale
4. **Conserver le ton professionnel** : Même registre de langue, même niveau de formalité
5. **Garder la même longueur** : Chaque paragraphe reformulé doit faire ±20% du nombre de mots de l'original. Ne pas écrire des pavés si l'original est court, et inversement
6. **Garder le même nombre de paragraphes/sections** : Ne pas fusionner 2 paragraphes en 1, ne pas couper 1 paragraphe en 3
7. **Garder le même nombre de FAQ** par page que dans le site source

### 6.2 Règles spécifiques aux FAQ

- **Même thème par question** (ex: si la Q1 parle des services proposés, la nouvelle Q1 aussi)
- **Reformuler la question ET la réponse**
- **Garder environ la même longueur** de réponse (±20%)
- **Ne pas changer l'ordre des FAQ**
- **Garder le même nombre de FAQ** que dans le site source (chaque page peut avoir un nombre différent)
- **Le JSON-LD FAQPage doit être mis à jour** avec le texte exact des nouvelles FAQ

### 6.3 Règles spécifiques aux pages villes

- Le **nom de la ville** doit rester présent 2-4 fois par paragraphe
- Varier l'intégration : "à [Ville]", "sur [Ville]", "dans la commune de [Ville]", "sur le secteur de [Ville]"
- **Chaque page ville doit être unique** par rapport aux autres villes ET par rapport au site source
- Les **20 pages villes doivent utiliser des formulations différentes les unes des autres** (pas de chercher-remplacer du nom de ville)

---

## 7. FORMAT DE SORTIE

### Instruction pour l'IA :

**OBLIGATOIRE — Travailler SANS agents (sans sub-agents / sans parallel tools).** Traiter chaque page de manière séquentielle, une par une, dans l'ordre indiqué ci-dessous. Ne pas paralléliser le travail. Même si c'est plus long, cela garantit la cohérence et évite les erreurs.

Pour chaque page, **réécrire le fichier HTML complet**. Ne pas fournir uniquement les extraits modifiés.

### Ordre de travail :

1. **Lire toutes les pages** du site source et lister les fichiers trouvés
2. **Mapper** chaque fichier source vers son fichier cible (nouveaux noms avec nouveau dept/villes)
3. **Pages principales d'abord** (dans cet ordre) :
   1. `index.html` (accueil)
   2. Page entreprise (nouveau nom de fichier)
   3. Pages services (nouveaux noms de fichiers, une par une — **toutes les pages services**, quel que soit leur nombre)
   4. Page prix / devis (nouveau nom de fichier)
4. **Mentions légales** : remplacer les infos entreprise
5. **Pages villes** (les 20, une par une, avec les nouvelles villes)
6. **Fichiers techniques** :
   - Régénérer `sitemap.xml` (nouvelles URLs, nouveau domaine, nouveaux noms d'images .webp, `<image:caption>` reformulées, 20 nouvelles pages villes ajoutées)
   - Mettre à jour `robots.txt` (nouveau domaine dans l'URL du sitemap)
   - Mettre à jour `CNAME` (nouveau domaine)
7. **Ne PAS toucher** : `style.css`

### Pour chaque page HTML :

1. Lire le fichier HTML source en entier
2. Créer le nouveau fichier avec le bon nom (nouveau dept/ville)
3. Remplacer toutes les infos de l'ancienne entreprise par la nouvelle (cf. section 3.7)
4. Adapter la localisation : département, région, villes (cf. section 3.4)
5. Mettre à jour tous les liens internes (nouveaux noms de fichiers)
6. Renommer les fichiers images selon la convention `mot-clé-département.webp` (cf. section 4.7.1) et mettre à jour tous les `src` avec les nouveaux noms
7. Reformuler tous les textes en appliquant les règles (cf. sections 5 et 6)
8. Mettre à jour le JSON-LD LocalBusiness complet (cf. section 3.4.1)
9. Mettre à jour le JSON-LD FAQPage (copier exactement les nouvelles FAQ reformulées)
10. Mettre à jour le copyright avec l'année en cours
11. Écrire le fichier HTML complet

---

## 8. AUDIT DE VÉRIFICATION COMPLET

**OBLIGATOIRE — Une fois TOUTES les pages terminées**, effectuer un audit complet de vérification en relisant chaque fichier créé. Cet audit est une étape à part entière, pas une simple relecture rapide.

### Procédure d'audit :

1. **Relire chaque fichier HTML généré** un par un et vérifier point par point :
   - [ ] Les textes sont bien reformulés (pas de copier-coller du site source)
   - [ ] Les mots-clés métier sont préservés dans les textes reformulés
   - [ ] Les infos de la nouvelle entreprise sont correctes partout (nom, tel, email, adresse, SIRET, horaires, réseaux sociaux)
   - [ ] La localisation (département, région, villes) est à jour partout (title, h1, alt/title images, JSON-LD, canonical)
   - [ ] Tous les liens internes pointent vers les bons fichiers (nouveaux noms)
   - [ ] Les `src` des images pointent vers les fichiers renommés en `mot-clé-département.webp`
   - [ ] Le `<link rel="preload">` pointe vers la bonne image héro
   - [ ] Le JSON-LD LocalBusiness est complet et correct (description reformulée, URLs à jour, Offers identiques au site source)
   - [ ] Le JSON-LD FAQPage correspond **exactement** au contenu FAQ visible sur la page
   - [ ] Le webhook et l'URL de redirection du formulaire sont mis à jour
   - [ ] Le copyright affiche l'année en cours

2. **Vérifier les pages villes** :
   - [ ] Les 20 pages existent bien avec les bons noms de fichiers
   - [ ] Chaque page a un contenu **unique** (comparer quelques paragraphes entre les pages pour s'assurer qu'il n'y a pas de doublons)

3. **Vérifier les fichiers techniques** :
   - [ ] `sitemap.xml` : toutes les URLs sont correctes (nouveau domaine, nouveaux fichiers HTML, nouvelles images renommées, 20 pages villes présentes, `<image:caption>` reformulées, `<image:title>` conservés)
   - [ ] `robots.txt` : URL du sitemap avec le nouveau domaine
   - [ ] `CNAME` : nouveau nom de domaine

4. **Vérifier ce qui ne doit PAS avoir changé** :
   - [ ] Les mots-clés métier dans les alt/title des images et des liens sont identiques au site source (seule la localisation change)
   - [ ] Les noms de services et le nombre d'Offers dans le JSON-LD sont identiques au site source
   - [ ] Le nombre de FAQ par page est identique au site source
   - [ ] Le nombre de blocs descriptifs par page service est identique
   - [ ] Les textes UI (navigation, boutons CTA, options du select) sont identiques
   - [ ] La structure HTML (sections, classes, IDs) est identique
   - [ ] Le `style.css` n'a pas été modifié

5. **Lister les anomalies trouvées** et les corriger immédiatement avant de terminer

---

## 9. INFORMATIONS DE LA NOUVELLE ENTREPRISE (À REMPLIR)

> **Remplir cette section avant de donner le prompt à l'IA.** Toutes les informations ci-dessous seront utilisées pour remplacer celles de l'ancienne entreprise dans le site source.

---

### Dossier du site source

```
Chemin : _______________________________________________
```

---

### Entreprise

```
Nom de l'entreprise     : _______________________________________________
Forme juridique         : _______________ (SASU, SARL, auto-entrepreneur...)
Adresse complète        : _______________________________________________
Code postal + Ville     : _______________________________________________
SIRET                   : _______________________________________________
RCS                     : _______________________________________________
```

---

### Contact

```
Téléphone mobile        : __ __ __ __ __
Téléphone fixe          : __ __ __ __ __ (laisser vide si un seul numéro)
Email                   : _______________________________________________
```

---

### Horaires d'ouverture

```
Lundi                   : __h__ - __h__
Mardi                   : __h__ - __h__
Mercredi                : __h__ - __h__
Jeudi                   : __h__ - __h__
Vendredi                : __h__ - __h__
Samedi                  : __h__ - __h__
Dimanche                : Fermé / __h__ - __h__
```

---

### Réseaux sociaux

```
Facebook                : https://_______________________________________________
Instagram               : https://_______________________________________________
LinkedIn                : https://_______________________________________________
Autre                   : https://_______________________________________________
```

---

### Zone géographique

```
Numéro de département   : ____
Nom du département      : _______________________________________________
Nom de la région        : _______________________________________________
```

#### 20 villes d'intervention

```
 1. _______________________________________________
 2. _______________________________________________
 3. _______________________________________________
 4. _______________________________________________
 5. _______________________________________________
 6. _______________________________________________
 7. _______________________________________________
 8. _______________________________________________
 9. _______________________________________________
10. _______________________________________________
11. _______________________________________________
12. _______________________________________________
13. _______________________________________________
14. _______________________________________________
15. _______________________________________________
16. _______________________________________________
17. _______________________________________________
18. _______________________________________________
19. _______________________________________________
20. _______________________________________________
```

---

### Technique

```
Nom de domaine          : _______________________________________________
Clé webhook WebPrime    : _______________________________________________
```

---

### Images (toutes en WebP)

```
Logo                    : _______________.webp
Image héro (bandeau)    : _______________.webp
Image zone intervention : _______________.webp
```

#### Images services (1 par page service)

```
Service 1               : _______________.webp
Service 2               : _______________.webp
Service 3               : _______________.webp
Service 4               : _______________.webp
Service 5               : _______________.webp
Service 6               : _______________.webp
Service 7               : _______________.webp
Service 8               : _______________.webp
Service 9               : _______________.webp
(ajouter / supprimer des lignes selon le nombre de services du site source)
```

#### Photos page entreprise (véhicules, réalisations, équipe)

```
Photo 1                 : _______________.webp
Photo 2                 : _______________.webp
Photo 3                 : _______________.webp
Photo 4                 : _______________.webp
(ajouter / supprimer des lignes selon le site source)
```

#### Logos partenaires / certifications

```
Partenaire 1            : _______________.webp
Partenaire 2            : _______________.webp
Partenaire 3            : _______________.webp
(ajouter / supprimer des lignes selon le site source)
```

#### Favicons

```
favicon.ico             : fourni ☐
apple-touch-icon.png    : fourni ☐
android-icon-192x192.png: fourni ☐
ms-icon-144x144.png     : fourni ☐
```

---

### Mentions légales

```
Responsable publication : _______________________________________________
Hébergeur (nom)         : _______________________________________________
Hébergeur (adresse)     : _______________________________________________
Hébergeur (site web)    : https://_______________________________________________
```


