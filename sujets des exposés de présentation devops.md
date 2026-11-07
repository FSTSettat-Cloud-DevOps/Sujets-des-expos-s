# Module : Cloud Computing, Virtualisation & DevOps
### Master Sciences et Techniques — Année Universitaire 2026/2027
### Pr. ABASSI Abdelfattah

---

## 📌 Consignes Générales pour les Exposés

- **Durée maximale :** 20 minutes par groupe (18 minutes de présentation + 2 minutes de questions/débat).
- **Format attendu :** Présentation  / Slides (12 à 15 diapositives conseillées).
- **Évaluation :** Clarté de la présentation, respect du temps imparti, maîtrise technique du plan proposé, illustration par un cas pratique concrétisé et animation du débat final.

---

## SECTION 1 :  Introduction au DevOps

### Sujet 1 : Du Document Word au Pipeline CI/CD — Transformer un Déploiement Chaotique en Processus 100% Automatisé

- **Objectif de l'exposé :** Analyser le scénario d'une entreprise utilisant un déploiement manuel basé sur un document Word et concevoir une chaîne d'intégration et de déploiement continus complète en s'appuyant sur les technologies du module.
- **Durée maximale :** 20 minutes (18 min d'exposé + 2 min de débat)

#### Plan type conseillé :

1. **Diagnostic flash (3 min) :** Identifier les dysfonctionnements organisationnels et culturels (absence des piliers CALMS, silos Dev/Ops, culture du blâme).
2. **La chaîne technique cible (5 min) :** Présenter l'enchaînement automatisé du code à la production : Commit Git $\rightarrow$ Tests automatisés $\rightarrow$ Packaging Docker (`docker build`) $\rightarrow$ Déploiement Kubernetes (`kubectl apply`).
3. **Cas pratique & Démonstration (5 min) :** Présenter un exemple concret de pipeline et de conversion des étapes d'un document Word en script d'Infrastructure as Code (IaC).
4. **Impact sur les métriques DORA (3 min) :** Démontrer la réduction du temps de mise en œuvre (*Lead Time*) et l'amélioration de la fréquence de déploiement et de la stabilité.

#### 🛠️ Exemple concret pour la partie pratique :
- **Scénario d'étude :** Une entreprise de billetterie en ligne dont le guide de déploiement est une liste d'instructions de 15 pages sur Word (ex: *"Étape 4: Copier le fichier .jar sur le serveur 192.168.1.50 via SCP et relancer le service"*).
- **Implémentation pratique à présenter :**
  - Présentation d'un extrait de workflow GitHub Actions / GitLab CI remplaçant ce document.
  - Démonstration de la conversion d'instructions manuelle en un job automatisé de build d'image Docker et de mise à jour d'un *Deployment* Kubernetes (`kubectl set image deployment/api-billetterie api=image:tag`).
  - Comparatif avant/après sur le temps de déploiement (passant de 4 heures manuelles à 3 minutes automatisées).

> **Question pour le débat final :** *« Si l'automatisation est totale mais que l'équipe refuse de partager les responsabilités en cas de bug, est-on vraiment en DevOps ? »*

---

### Sujet 2 : Comment le cadre CALMS peut-il sauver une startup qui livre du code en urgence chaque nuit ?

- **Objectif de l'exposé :** Appliquer les cinq piliers du cadre CALMS (Culture, Automation, Lean, Measurement, Sharing) à une situation de crise organisationnelle pour structurer la transition DevOps au-delà des simples outils.
- **Durée maximale :** 20 minutes (18 min d'exposé + 2 min de débat)

#### Plan type conseillé :

1. **Mise en situation de crise (3 min) :** Décrire l'épuisement d'une équipe technique effectuant des mises en production nocturnes manuelles sans visibilité.
2. **Analyse détaillée du modèle CALMS (6 min) :** Appliquer concrètement Culture (post-mortems sans blâme, *"You build it, you run it"*), Automation (élimination des tâches répétitives), Lean (petits lots de travail), Measurement et Sharing.
3. **Cas pratique d'application (5 min) :** Modéliser la transformation organisationnelle à travers un cas réel de crise de déploiement.
4. **Le rôle et la philosophie du SRE (4 min) :** Définir la fonction du Site Reliability Engineer et la manière d'appliquer une approche logicielle aux problèmes d'exploitation.

#### 🛠️ Exemple concret pour la partie pratique :
- **Scénario d'étude :** La startup *FoodExpress* subit un crash majeur lors de la livraison nocturne d'une mise à jour de 50 000 lignes de code. Le fondateur cherche à renvoyer le développeur responsable.
- **Implémentation pratique à présenter :**
  - Rédaction d'un **"Blameless Post-Mortem" (Rapport d'incident sans blâme)** sous forme de fiche type : analyse de la cause racine systémique (absence de tests automatiques, taille de lot trop grande) au lieu de blâmer l'humain.
  - Proposition d'un tableau Kanban montrant le passage d'une release monolitique mensuelle à des déploiements par petits lots de fonctionnalités (*Lean*).
  - Définition d'une charte de partage d'astreinte (*Sharing / "You build it, you run it"*).

> **Question pour le débat final :** *« Pourquoi est-il souvent plus difficile de changer la culture d'une entreprise que d'installer un cluster Kubernetes ? »*

---

## SECTION 2 :  CI/CD : Intégration et Déploiement Continus

### Sujet 3 : Continuous Delivery vs Continuous Deployment — Choisir le Bon Degré d'Automatisation pour une Application Critique

- **Objectif de l'exposé :** Comparer rigoureusement Continuous Delivery (avec validation humaine) et Continuous Deployment (automatisation totale) pour conseiller une entreprise sur la stratégie d'automatisation optimale.
- **Durée maximale :** 20 minutes (18 min d'exposé + 2 min de débat)

#### Plan type conseillé :

1. **Clarification des concepts (4 min) :** Définir la pyramide d'automatisation CI/CD ($\text{CI} \rightarrow \text{Continuous Delivery} \rightarrow \text{Continuous Deployment}$) et expliciter la place du contrôle humain.
2. **Exigences de la Pyramide des Tests (4 min) :** Démontrer pourquoi le Continuous Deployment requiert une suite complète de tests (Unitaires, Intégration, E2E) et un système d'arrêt automatique (*Fail Fast*).
3. **Cas pratique et configuration YAML (5 min) :** Présenter et expliciter la différence de syntaxe et d'architecture de pipeline entre les deux approches.
4. **Étude comparative des scénarios (5 min) :** Analyser les critères de décision et proposer des recommandations ciblées (gestion bancaire vs réseau social).

#### 🛠️ Exemple concret pour la partie pratique :
- **Scénario d'étude :** Une application de santé gérant des dossiers médicaux (*PayMed*) souhaite accélérer ses livraisons.
- **Implémentation pratique à présenter :**
  - Code YAML comparatif d'un pipeline (GitLab CI / GitHub Actions) :
    - Version **Continuous Delivery** : utilisation de la clause `when: manual` ou `environment: production` avec approbation manuelle sur la plateforme.
    - Version **Continuous Deployment** : ajout d'un job automatisé exécutant une suite de tests de sécurité (`OWASP ZAP` / `trivy`) autorisant directement la mise en production si la couverture de tests dépasse 90%.
  - Démonstration théorique du comportement du pipeline lorsqu'un test d'intégration échoue (*Fail-Fast*).

> **Question pour le débat final :** *« Peut-on réellement faire confiance à 100% à une suite de tests automatisés pour déployer directement en production sans validation humaine ? »*

---

### Sujet 4 : Déploiement Zero-Downtime — Évaluer et Implémenter les Stratégies Rolling Update, Blue-Green et Canary

- **Objectif de l'exposé :** Présenter, comparer et simuler l'application des trois grandes stratégies de mise à jour d'applications en production sans interruption de service (*Zero-Downtime*).
- **Durée maximale :** 20 minutes (18 min d'exposé + 2 min de débat)

#### Plan type conseillé :

1. **Le problème des mises à jour en production (3 min) :** Expliquer les enjeux du zero-downtime et les risques d'incompatibilité de versions simultanées.
2. **Analyse technique des 3 stratégies (6 min) :** Étudier le fonctionnement, l'infrastructure requise et le comportement réseau de Rolling Update (par défaut Kubernetes), Blue-Green et Canary.
3. **Cas pratique sur Kubernetes (5 min) :** Démontrer le fonctionnement concret des stratégies avec des manifestes Kubernetes (YAML).
4. **Matrice de décision et coût (4 min) :** Comparer les stratégies selon 3 axes (complexité, coût d'infrastructure, vitesse de rollback) et motiver le choix pour une plateforme e-commerce.

#### 🛠️ Exemple concret pour la partie pratique :
- **Scénario d'étude :** Mise à jour v1 vers v2 du service de paiement d'un site e-commerce à fort trafic sans perdre aucun panier client.
- **Implémentation pratique à présenter :**
  - **Canary Release sur Kubernetes :** Présentation des manifestes YAML avec 2 Deployments (`app-v1` avec 9 réplicas et `app-v2` avec 1 réplica) rattachés au même *Service* Kubernetes pour distribuer 10% du trafic sur la v2.
  - **Blue-Green Release :** Explication du basculement d'un Service Kubernetes en modifiant le sélecteur (`selector: app-v1` $\rightarrow$ `selector: app-v2`) via une seule commande `kubectl apply`.
  - Comparaison du comportement du trafic lors d'un rollback instantané.

> **Question pour le débat final :** *« Dans quel cas la stratégie Rolling Update par défaut de Kubernetes devient-elle dangereuse et justifie-t-elle le surcoût d'un déploiement Blue-Green ? »*

---

## SECTION 3 :  Monitoring, Sécurité et Projet DevOps

### Sujet 5 : Pilotage de la Disponibilité Applicative — Du SLO/SLA à l'Implémentation de Prometheus & Grafana avec les Méthodes RED/USE

- **Objectif de l'exposé :** Concevoir une architecture complète d'observabilité en définissant les objectifs de niveau de service (SLO/SLA), l'Error Budget et les métriques clés via le tandem Prometheus & Grafana.
- **Durée maximale :** 20 minutes (18 min d'exposé + 2 min de débat)

#### Plan type conseillé :

1. **Les fondements de la disponibilité (4 min) :** Expliquer SLI, SLO, SLA et calculer l'Error Budget mensuel associé à un SLO de 99,9% (ex. 43 min d'indisponibilité).
2. **Méthodologies de métriques (4 min) :** Structurer la collecte avec la méthode RED (*Rate, Errors, Duration* pour les services) et la méthode USE (*Utilization, Saturation, Errors* pour l'infrastructure).
3. **Cas pratique PromQL & Dashboard Grafana (5 min) :** Présenter des requêtes concrètes et la modélisation d'un tableau de bord de supervision.
4. **Alerting et Boucle de Rétroaction (5 min) :** Définir des seuils d'alerte précis pour éviter la fatigue d'alerte (*Alert Fatigue*) et fermer la boucle de rétroaction DevOps.

#### 🛠️ Exemple concret pour la partie pratique :
- **Scénario d'étude :** Supervision d'une API Gateway recevant 1000 requêtes/seconde.
- **Implémentation pratique à présenter :**
  - **Exposition des métriques :** Exemple de code (Python/Node.js) exposant la métrique `http_requests_total` sur le sous-domaine `/metrics`.
  - **Requêtes PromQL :** 
    - Calcul du taux de requêtes (Rate) : `rate(http_requests_total[5m])`
    - Calcul du taux d'erreur 5xx (Errors) : `sum(rate(http_requests_total{status=~"5.."}[5m])) / sum(rate(http_requests_total[5m]))`
  - **Maquette de Dashboard Grafana :** Schéma / capture d'un tableau de bord affichant le taux de consommation de l'Error Budget en temps réel.

> **Question pour le débat final :** *« Comment l'Error Budget permet-il de résoudre objectivement le conflit historique entre les développeurs (souhaitant déployer vite) et les Ops (souhaitant la stabilité) ? »*

---

### Sujet 6 : Sécurité Cloud & Gestion des Secrets — Appliquer la Défense en Profondeur et la Règle de Sauvegarde 3-2-1 en Production

- **Objectif de l'exposé :** Présenter une stratégie intégrée de sécurisation et de résilience des applications conteneurisées, couvrant la défense en profondeur, la gestion dynamique des secrets et le plan de reprise d'activité.
- **Durée maximale :** 20 minutes (18 min d'exposé + 2 min de débat)

#### Plan type conseillé :

1. **Modèle de Responsabilité Partagée & Défense en Profondeur (4 min) :** Analyser les risques de sécurité (images vulnérables, privilèges root, secrets en clair) et empiler les couches de protection.
2. **Gestion avancée des Secrets (4 min) :** Démontrer les limites des Secrets Kubernetes (base64) et présenter la rotation automatique des secrets (ex. HashiCorp Vault) pour réduire les fenêtres d'exposition.
3. **Cas pratique de Sécurisation & PRA (5 min) :** Présenter la mise en place d'un audit d'image Docker, de politiques de sécurité Pod (`SecurityContext`) et un scénario de reprise après sinistre.
4. **Résilience et Sauvegarde (5 min) :** Appliquer la règle 3-2-1 (3 copies, 2 supports, 1 hors-site) et définir les indicateurs RPO (*Recovery Point Objective*) et RTO (*Recovery Time Objective*).

#### 🛠️ Exemple concret pour la partie pratique :
- **Scénario d'étude :** Sécurisation d'une application conteneurisée manipulant une base de données MySQL contenant des données clients sensibles.
- **Implémentation pratique à présenter :**
  - **Sécurité des Conteneurs :** Analyse comparative d'un Dockerfile non sécurisé (`USER root`, image `latest`) vs sécurisé (`USER node`, scan de vulnérabilités Trivy, image alpine/distroless).
  - **Gestion des Secrets :** Explication du danger d'un secret Kubernetes encodé en Base64 simple vs l'injection dynamique de secrets via HashiCorp Vault ou SOPS.
  - **Plan de Sauvegarde 3-2-1 :** Schéma d'une stratégie de backup d'une base de données avec 1 dump local quotidien, 1 copie répliquée sur un stockage objet Cloud (ex: AWS S3) et 1 copie chiffrée hors-site, pour garantir un RPO < 1h et un RTO < 30min.

> **Question pour le débat final :** *« Si un mot de passe de base de données a été accidentellement committé puis supprimé dans un commit Git ultérieur, pourquoi est-il toujours en danger et quelle mesure immédiate s'impose ? »*
