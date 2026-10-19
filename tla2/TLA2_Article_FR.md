---
title: "Du routage des preuves à l’apprentissage territorial collectif : architecture formelle et protocole de simulation réfutable"
subtitle: "TLA 2 — Formalisation computationnelle et protocole d’évaluation par simulation Monte Carlo"
author: "Émile Tanic"
date: "Octobre 2026"
lang: fr-FR
geometry: margin=2.25cm
fontsize: 10pt
classoption: a4paper
colorlinks: true
linkcolor: blue
header-includes:
  - \usepackage{amsmath,amssymb,mathtools}
  - \usepackage{microtype}
  - \usepackage{longtable}
  - \usepackage{float}
  - \usepackage{placeins}
  - \usepackage{array}
  - \setlength{\emergencystretch}{3em}
---

**Cadre de référence :** Émile Tanic, *Et si l’IA pouvait rendre un territoire plus intelligent ? La Martinique comme territoire apprenant à l’âge de l’intelligence artificielle*, 2026, édition publiée et accessible sur [Amazon.fr](https://www.amazon.fr/dp/B0HLHC1MT2) (ASIN B0HLHC1MT2). **Point de départ scientifique :** *TLA — Territorial Learning Architecture: An AI-Assisted Learning Architecture for Territories*, version anglaise EN_v2a, DOI : [10.5281/zenodo.22923636](https://doi.org/10.5281/zenodo.22923636).

**Traçabilité scientifique.** Trois étiquettes distinguent les origines des propositions : **[LB]** = mécanisme décrit dans le Livre blanc publié sur Amazon et cité dans le cadre de référence ; **[TLA1]** = mécanisme présenté dans l’article scientifique cité dans le cadre de référence ; **[NOUVEAU]** = choix de modélisation proposé ici, non spécifié dans les deux documents. Une correspondance conceptuelle ne signifie pas qu’un algorithme opérationnel existe déjà. **Les équations ci-dessous sont des hypothèses de formalisation, non des citations du Livre blanc. Aucun résultat expérimental nouveau n’est revendiqué.**

# Résumé

Cette spécification propose une extension simulable de la *Territorial Learning Architecture* (TLA). Le Livre blanc de 2026 décrit un Laboratoire Territorial Auto-Apprenant (LTAA) qui exploite d’abord les preuves existantes, explicite les incertitudes importantes, compare des micro-expériences réversibles grâce à l’Indice de Rendement d’Apprentissage Territorial (IRAT), sollicite une expertise humaine au moyen du Martinique Intelligence Network (MIN) et transforme les résultats en capacités documentées, gouvernées et transférables. Le premier article TLA a développé l’*Adaptive Evidence Routing* (AER), le *Context-Aware Experience Reuse* (CAER) et trois mémoires complémentaires. TLA 2 articule ces éléments dans un processus distribué, placé sous gouvernance humaine, et inclut le transfert contextuel, le graphe des organisations et des capacités, les coûts, les protections et les conditions d’arrêt. Il spécifie un modèle minimal de transition d’état, des politiques concurrentes, des indicateurs définis avant simulation et un protocole Monte Carlo de 800 mondes synthétiques appariés par scénario. L’objectif est d’identifier **les bénéfices possibles et les conditions d’échec**, et non de prévoir une valeur économique pour la Martinique.

# Introduction — Pourquoi formaliser le modèle avant de le simuler ?

Le Livre blanc propose une architecture de développement territorial fondée sur une idée : transformer l'observation et l'expérimentation en apprentissages, puis en capacités durables. L'article scientifique cité dans le cadre de référence en isole et précise plusieurs mécanismes de traitement des preuves et de réemploi des expériences (AER, CAER et trois mémoires). La présente spécification, **TLA 2**, cherche à rendre simulables leurs interactions avec les autres mécanismes du Livre blanc, notamment le LTAA, l'IRAT, le MIN, le compilateur de capacités et le graphe territorial. Cette formalisation n'est pas une réécriture du Livre blanc : c'est une **hypothèse de représentation computationnelle** qu'il sera possible de discuter et de modifier.

**L'objectif de la simulation Monte Carlo** est de soumettre plusieurs architectures concurrentes aux mêmes séries de situations synthétiques, en faisant varier les problèmes rencontrés, les ressources disponibles, les coûts, la fiabilité des informations, les experts mobilisables et l'évolution des contextes. Cette démarche s'inscrit dans le prolongement d'une première simulation exploratoire du LTAA réalisée par l'IA **Dori**, à la demande de **Benoit Deschamps**, et analysée dans une note datée du 2 octobre 2026. Cette première expérience, fondée sur 400 mondes simulés et sur la comparaison de trois stratégies (grand projet, tests aléatoires, logique IRAT/LTAA), a montré l'intérêt méthodologique d'une modélisation explicite de l'apprentissage territorial, tout en soulignant le caractère hypothétique des paramètres et l'absence de validation empirique directe. TLA 2 vise à prolonger ce travail en proposant un cadre plus général, plus transparent et plus reproductible. Il s'agit de comparer, dans des conditions explicitement définies, leur capacité à améliorer les décisions, à éviter des dépenses inutiles, à conserver des compétences réutilisables et à limiter les risques. La simulation doit également mettre en évidence les circonstances où l'architecture complète **ne fonctionne pas mieux**, coûte trop cher ou engendre des transferts erronés. Elle n'a ni pour objet de prédire les résultats économiques réels de la Martinique ni de démontrer, par elle-même, l'efficacité du dispositif sur le terrain.

**Pourquoi la formalisation est-elle indispensable ?** Une description conceptuelle ne détermine pas automatiquement ce qu'un programme informatique doit calculer. Il faut rendre explicites les variables d'état, les règles d'accès aux sources, les décisions possibles, leurs coûts, leurs effets, les mécanismes d'apprentissage et de transfert, les événements aléatoires ainsi que les critères de comparaison. À défaut, une simulation peut surtout mesurer les hypothèses implicites du programmeur. La formulation mathématique est donc une condition de **testabilité**, et non une prétention à réduire la complexité politique et humaine à une unique équation.

**Pourquoi viser la critique par des observateurs extérieurs ?** Les résultats ne seront scientifiquement analysables que si des équipes indépendantes peuvent distinguer les mécanismes provenant des textes de référence des choix de simulation nouveaux, retrouver chaque paramètre et sa justification, examiner les distributions et les corrélations retenues, inspecter les règles de gouvernance, reproduire les calculs et vérifier les différences entre politiques sur les mêmes mondes synthétiques. Le protocole, les données générées, le code, les graines aléatoires, les tests, les résultats négatifs et les analyses de sensibilité devront pouvoir être audités. **La reproductibilité informatique ne garantit pas la validité empirique :** une confrontation ultérieure à des données territoriales réelles restera nécessaire.

La figure 1 rend visible le lien entre les trois niveaux de travail. Ses flèches expriment une **correspondance conceptuelle**, non une identité parfaite entre modules ni une généalogie algorithmique démontrée. L'infographie rappelle également qu'une première simulation Monte Carlo exploratoire existe déjà ; elle ne vaut pas validation du modèle, mais fournit un point d'appui utile pour justifier la nécessité d'une formalisation plus complète.

![Correspondance entre le Livre blanc, TLA1 et TLA2 : des concepts aux mécanismes simulables.](assets/TLA2_Infographie_FR.png){width=95%}

# 1. Objet, périmètre et limites de TLA 2

La question de recherche est : **dans quelles conditions une architecture d’apprentissage territorial soumise à une gouvernance humaine améliore-t-elle, par rapport à des processus décisionnels plus simples, la qualité des décisions, l’accumulation de capacités, les coûts, la résilience et l’équité ?**

TLA 2 ne constitue ni l’ensemble du programme de développement économique du Livre blanc, ni une autorité publique autonome, ni une IA à laquelle seraient délégués les choix politiques. Il modélise les mécanismes qui soutiennent l’apprentissage dans des contraintes institutionnelles. La Martinique motive sa conception, mais ne fournit pas encore de paramètres empiriquement calibrés. Le modèle doit pouvoir **échouer**, coûter excessivement en coordination ou recommander un transfert inapproprié.

Trois objets ne doivent pas être confondus : **(a) le TIIA**, vision globale du développement territorial [LB, pp. 12–29] ; **(b) le LTAA**, architecture distribuée de décision et d’apprentissage [LB, chap. 5] ; **(c) TLA 2**, abstraction computationnelle proposée [NOUVEAU] articulant certaines fonctions du LTAA et les mécanismes de TLA 1. AER et CAER ne sont pas des synonymes du LTAA, de l’IRAT, du compilateur ou du MIN.

# 2. Matrice de traçabilité fidèle aux sources

| Mécanisme | Engagement du Livre blanc | Formalisation proposée / TLA 1 | Référence | Statut |
|:---|:---|:---|:---|:---|
| LTAA | Observer, expliciter l’incertitude, générer, filtrer, comparer par IRAT, autoriser, mesurer, compiler | Machine à états orchestrant les étapes | LB, chap. 5–6, fig. 4, pp. 61–65 | LB → NOUVEAU |
| IRAT | Mettre en balance information, valeur publique, capacité, transfert, argent, temps humain, risque et irréversibilité ; priorités fixées humainement | Classement multicritère d’expériences admissibles | LB, chap. 7, pp. 66–68 | LB → NOUVEAU |
| AER | Choisir la source de preuve selon l’incertitude, le coût, les risques et le contexte | Politique de routage entre documents, experts, expériences et arrêt | TLA1 ; LB, chap. 6 | TLA1 étendu |
| MIN | Organiser des micro-missions volontaires et bornées, avec consentement et adéquation des compétences | File de missions et appariement humain | LB, chap. 15, pp. 84–85 | LB → NOUVEAU |
| Compilateur | Conserver contexte, droits, échecs, coûts, compétences, maintenance, limites du transfert | Objets de capacité structurés et validés | LB, chap. 8, pp. 69–70 | LB → NOUVEAU |
| Trois mémoires | Preuves, connaissances consolidées, expériences | Mémoires fédérées avec provenance et droits | TLA1 ; LB, chap. 14, pp. 82–83 | TLA1 + LB |
| CAER | Réutiliser, adapter ou réexpérimenter selon le contexte | Évaluation explicite du transfert, avec abstention | TLA1 ; LB, chap. 26 | TLA1 étendu |
| Jumeaux de problème | Comparer les signatures des problèmes, pas les seules apparences | Distance contextuelle et domaines de validité | LB, chap. 26, pp. 129–130 | LB → NOUVEAU |
| Graphe territorial | Liens autorisés entre organismes, compétences, données et capacités | Graphe typé intégrant dépendances et coûts | LB, chap. 25, pp. 127–128 | LB → NOUVEAU |
| Mode miroir | Confronter les recommandations du LTAA aux pratiques humaines sans action automatique | Phase distincte d’évaluation, seuils de confiance et autorisations | LB, chap. 9, pp. 71–72 | LB → NOUVEAU |
| Gouvernance | Autonomie bornée, droits, équité, biosphère, réversibilité et continuité | Contraintes dures, validations, veto, incidents | LB, chap. 10–13 et 17 | LB → NOUVEAU |
| Évaluation | Services, coût d’apprentissage, capacité résiduelle, résilience, accès, écologie | Vecteur de résultats multidimensionnel | LB, chap. 29, pp. 137–139 | LB → NOUVEAU |

*Toutes les pages citées renvoient à la pagination imprimée de l’édition papier au format 6 × 9 pouces, telle qu’elle figure dans le fichier intérieur KDP de 154 pages correspondant au Livre blanc publié sur Amazon (ASIN B0HLHC1MT2). Elles ne désignent pas des emplacements Kindle, dont la présentation est variable. Les interfaces précises des trois mémoires devront être confrontées au texte de référence de l’article EN_v2a avant stabilisation.*

# 3. Objet mathématique : un processus territorial distribué et partiellement observé

Une exécution de simulation contient des **organisations** $o\in\mathcal O$, des **problèmes** $p\in\mathcal P$, des **contextes** $x\in\mathcal X$, des **experts** $h\in\mathcal H$, des **capacités** $c\in\mathcal C$ et des instants $t=0,\ldots,T$. Les propriétés réelles $\theta$ du problème sont cachées à la politique de décision ; le simulateur les connaît pour évaluer les erreurs.

L’état observé est représenté par :

$$
S_t=\left(P_t,B_t,M_t^{E},M_t^{K},M_t^{X},C_t,H_t,G_t,Z_t,Q_t\right).
$$

Ici, $B_t$ désigne les budgets de ressources ; $M_t^E$ la mémoire des preuves ; $M_t^K$ la mémoire des connaissances consolidées ; $M_t^X$ la mémoire des expériences ; $C_t$ les capacités compilées ; $H_t$ les compétences et disponibilités humaines ; $G_t$ le graphe territorial ; $Z_t$ les règles de gouvernance et d’accès ; et $Q_t$ la qualité évaluée des politiques d’apprentissage. Chaque problème possède un indicateur de résultat et une signature contextuelle $x_p$ (organisation, environnement, droit, facteurs humains, technique).

L’évolution est modélisée par :

$$
S_{t+1}\sim P_{\varphi}\!\left(\,\cdot\mid S_t,a_t,\omega_t\right),
\qquad a_t\sim\pi(\cdot\mid S_t),
$$

avec $a_t$ l’action, $\pi$ la politique, $\omega_t$ les événements externes et $\varphi$ les paramètres de scénario. Il s’agit d’un processus stochastique contrôlé et partiellement observé, **non** d’une affirmation selon laquelle les choix politiques se réduisent à une optimisation.

Distinctions impératives : une observation n’est pas une croyance ; une corrélation n’est pas automatiquement causale ; une ressource mémorisée n’est pas nécessairement accessible juridiquement ; une expérience enregistrée n’est pas déjà une capacité validée ; tout réemploi est une décision nouvelle pouvant nécessiter une micro-expérience.

# 4. Modules, interfaces et mécanismes de contrôle

## 4.1 Enregistrement du problème et mandat [LB → NOUVEAU]

**Entrées :** problème documenté, organisme responsable, parties concernées, résultats visés, situation de référence, règles et données disponibles. **Sortie :** un objet *ProblemCase* contenant une question réfutable, les actions envisageables, les contraintes de sécurité, les incertitudes et l’enveloppe d’expérimentation autorisée. Un dossier insuffisamment défini peut être refusé. L’autorité humaine fixe les objectifs et seuils ; le modèle ne les invente pas.

## 4.2 AER — routage adaptatif des preuves [TLA1 → NOUVEAU]

**Entrées :** dossier décisionnel, croyance actuelle $b_t(\theta)$, mémoires et sources accessibles. **Sortie :** une voie $r$ choisie entre : réutiliser une trace existante, rechercher d’autres données, interroger le MIN, conduire une micro-expérience réversible, arrêter et agir, s’abstenir ou demander un arbitrage.

Pour une source $r$, une première définition de la **valeur espérée de l’information pour la décision** est :

$$
\operatorname{VEI}(r)=
\mathbb E_{y\mid r,D_t}\!\left[
\max_{a\in\mathcal A}\mathbb E\!\left[U(a,\theta)\mid D_t,y,r\right]
\right]
-\max_{a\in\mathcal A}\mathbb E\!\left[U(a,\theta)\mid D_t\right].
$$

$D_t$ regroupe les preuves disponibles, $y$ l’observation encore inconnue que procurerait $r$, $\mathcal A$ les actions admissibles et $U$ leur utilité publique. La politique compare cette valeur au **coût complet de l’information**, sous contraintes :

$$
\operatorname{GainNet}(r)=\operatorname{VEI}(r)-C_{\mathrm{info}}(r).
$$

Une information n’est pas acquise si son gain marginal attendu est insuffisant ou si son accès est interdit. La création d’une infrastructure coûteuse n’est pas le point de départ par défaut. AER peut confier à l’IRAT le classement de plusieurs micro-expériences admissibles. **Ces équations sont nouvelles**, et non prescrites par le Livre blanc. Il faudra tester le calibrage et l’excès de confiance de l’estimateur. AER doit pouvoir conclure qu’il n’est pas utile de rechercher davantage d’informations.

## 4.3 IRAT — comparaison multicritère transparente [LB → NOUVEAU]

Pour chaque expérience réversible et admissible $e$, on définit le vecteur :

$$
z(e)=\bigl(I_e,V_e,K_e,T_e,C_e,H_e,R_e,J_e,E_e,D_e\bigr),
$$

qui représente respectivement : gain d’information, valeur publique, capacité résiduelle, transférabilité, coût financier, heures humaines rares, risque, irréversibilité, charge écologique et délai. Les seuils juridiques et de sécurité sont vérifiés **avant** le classement. Les responsables humains fixent les pondérations, les bornes de normalisation, les veto et la légitimité des arbitrages.

Une première fonction expérimentale possible est :

$$
\operatorname{Score}_{w}(e)=
\sum_{j\in\mathcal B}w_j\,\operatorname{norm}\!\left(z_j(e)\right)
-\sum_{k\in\mathcal N}w_k\,\operatorname{norm}\!\left(z_k(e)\right),
\qquad e\in\mathcal E_{\mathrm{admissible}}.
$$

$\mathcal B$ rassemble les critères de bénéfice et $\mathcal N$ les charges. **Ce score n’est pas une formule IRAT définitive** : le Livre blanc refuse expressément la fiction d’un « score magique ». L’interface doit montrer les intervalles d’incertitude et les alternatives de Pareto. Les droits et seuils écologiques ne doivent pas devenir des pénalités négociables. Une variation des pondérations peut inverser le classement et doit être publiée. Les effets futurs réutilisables sont incertains et ne peuvent être comptés deux fois.

## 4.4 MIN — micro-expertise humaine bornée [LB → NOUVEAU]

**Objet mission :** question, signature du problème, compétences requises, sensibilité, durée bornée, consentement, rémunération éventuelle, échéance et responsable. **Entrées d’appariement :** compétences déclarées de volontaires, disponibilité, information autorisée et conditions de reconnaissance. **Sorties :** mission acceptée/refusée, délai, coût, observation validée et fiabilité estimée. L’échec de l’appariement, l’absence de réponse ou le désaccord entre experts restent possibles. Aucune expertise illimitée ou gratuite ne doit être présumée dans la diaspora. Le MIN doit être comparé à une voie ordinaire de recours à un expert rémunéré.

## 4.5 Exécution et évaluation indépendante des expériences [LB → NOUVEAU]

Exécuter une intervention limitée, réversible et explicitement autorisée. Enregistrer la situation initiale, l’intervention, les résultats, les dommages, le temps humain, le coût de déploiement, les écarts au protocole et les conséquences décisionnelles. Une évaluation indépendante détermine si les croyances sont modifiées, si une réplication est nécessaire ou si l’action doit être arrêtée. **Les essais négatifs ou non concluants sont conservés.** Le simulateur inclura mesures biaisées, expériences peu informatives, irréversibilité et effets indésirables.

## 4.6 Compilateur de capacités [LB → NOUVEAU]

**Entrée :** expérience évaluée (positive, négative ou ambiguë), avec provenance. **Sortie :** un *CapabilityObject* validé, ou seulement un *ExperienceRecord* non promu — jamais un bénéfice gratuit. L’objet de capacité décrit au minimum : problème et contexte, hypothèses, sources, droits d’accès, protocole, résultats et erreurs mesurés, compétences mobilisées, outils et scripts, reproductibilité, sécurité, contraintes d’emploi, limites de transférabilité, responsable de maintenance, version, échéance de révision et régime d’accès (ouvert, mutualisé, restreint, protégé).

La promotion exige une qualité de preuve minimale, un responsable nommé et des ressources de maintenance. Une capacité peut perdre sa validité, être retirée ou échouer lors d’un réemploi. La compilation inclut les coûts de validation **et** de maintenance récurrente. Une représentation schématique de sa persistance est :

$$
q_c(t+1)=q_c(t)\,\bigl(1-\delta_c(t)\bigr)+\Delta q_c(t),
$$

avec $q_c(t)$ une mesure conventionnelle de validité, $\delta_c$ une dégradation et $\Delta q_c$ un éventuel effet de revalidation. **Cette équation de dégradation est une proposition nouvelle**, qui ne figure pas dans le Livre blanc.

## 4.7 CAER, jumeaux de problème et graphe territorial [TLA1 + LB → NOUVEAU]

CAER recherche une capacité ou une expérience candidate $c$, puis compare son domaine de validité au nouveau contexte $x$. Une distance contextuelle transparente peut s’écrire :

$$
d(x,x_c)=\sum_{j=1}^{m}\alpha_j\,d_j(x_j,x_{c,j}),
\qquad \sum_{j=1}^{m}\alpha_j=1,
$$

**sous réserve** de conditions juridiques et de sécurité non compensatoires. Une grande similarité ne suffit pas à elle seule. CAER propose **réutiliser / adapter / réexpérimenter / renoncer**, avec intervalle de prévision et justification. Un transfert constitue une **nouvelle expérience**, pas une réutilisation garantie. Les échecs et contre-exemples corrigent le domaine de validité.

Le graphe $G_t$ comprend des nœuds typés (organisations, experts, détenteurs de données, processus, méthodes, capacités) et des liens autorisés (accès, dépendance, coopération, transfert). L’existence d’un chemin n’accorde pas automatiquement un droit d’accès. Créer et maintenir les liens entraîne des coûts, délais et échecs. La coopération peut réduire les coûts futurs, mais des dépendances ou situations de verrouillage peuvent aussi les augmenter. Les effets du réseau sont des **hypothèses empiriques à tester**.

## 4.8 Mode miroir et autonomie bornée [LB → NOUVEAU]

**Phase 0 :** recommandation parallèle aux experts, sans action automatisée. **Phase 1 :** expériences conduites par les humains, éventuellement inspirées des recommandations. **Phase 2 :** automatisation seulement pour des tâches validées, réversibles et à faible risque. Les décisions à conséquences importantes restent soumises à des validations humaines identifiées. Les changements de phase nécessitent des seuils définis à l’avance : qualité de décision, calibration, dommages, équité, complétude des audits. Une défaillance provoque une suspension ou un retour au niveau antérieur. Dans les comparaisons simulées, les processus humains de contrôle doivent rester comparables entre stratégies.

# 5. Articulation causale et hypothèse centrale

Flux proposé : **enregistrer le problème → vérifier les contraintes → choisir la source par AER → rechercher éventuellement par CAER → classer éventuellement par IRAT → solliciter éventuellement le MIN → autoriser l’expérience ou l’action → évaluer indépendamment → mettre à jour preuves et expériences → compiler éventuellement → mettre à jour le graphe → surveiller, retirer ou reprendre l’apprentissage**.

Les boucles et délibérations parallèles sont autorisées ; toutes ces étapes ne sont pas obligatoires pour chaque problème. Les preuves existantes peuvent suffire à décider sans nouvelle expérience.

L’hypothèse centrale est **conditionnelle et réfutable** : lorsque des problèmes apparentés reviennent, que l’information peut être acquise à un coût acceptable et que la pertinence contextuelle est correctement évaluée, l’association du routage adaptatif, de la compilation gouvernée et du réemploi peut améliorer les résultats cumulés par rapport à des politiques plus simples. Elle peut au contraire se révéler inférieure en cas de dérive des contextes, de mauvais appariement des experts, de maintenance coûteuse, de faible réemploi, d’accès restreints ou de preuves peu fiables.

# 6. Protocole Monte Carlo : 800 mondes appariés

## 6.1 Unité de simulation et mondes communs

Utiliser **800 mondes synthétiques par scénario prédéfini** (et non 800 communes). Dans chaque monde, les politiques reçoivent le même flux de problèmes cachés, les mêmes changements institutionnels de contexte, experts, sources de données et résultats potentiels. Les événements exogènes utilisent des tirages aléatoires communs ; les conséquences dépendantes d’une politique doivent néanmoins respecter les mécanismes stochastiques établis. Les épisodes doivent être assez longs pour faire apparaître la persistance et l’obsolescence des capacités : par exemple 60 périodes et des familles de problèmes récurrents (**choix illustratifs**, pas faits observés). Séparer les paramètres fixés avant l’essai des paramètres à calibrer sur données réelles.

## 6.2 Politiques comparées et ablations

| Code | Politique | Question isolée |
|:---|:---|:---|
| P0 | Processus classique avec contrôles humains, sans couche partagée d’apprentissage | Référence crédible |
| P1 | P0 + AER et recherche ciblée de preuves | Valeur de l’information sélectionnée |
| P2 | P1 + classement expérimental IRAT | Gain de priorisation adaptative |
| P3 | P2 + MIN et micro-missions bornées | Accès aux compétences, net des délais et coûts |
| P4 | P3 + compilateur et mémoires gouvernées | Capacité résiduelle nette des frais de maintien |
| P5 | P4 + CAER, jumeaux de problème et transfert par graphe | Effet marginal du réemploi contextuel |
| P6 | P5 + amélioration de la **politique d’apprentissage elle-même**, après évaluation indépendante | Apprendre à apprendre |

P1 à P6 sont des architectures expérimentales proposées [NOUVEAU]. Il faut également retirer, l’un après l’autre, chaque composant de P5 et comparer CAER à une réutilisation naïve sans contrôle contextuel. Une configuration AER + CAER sans compilateur doit utiliser un dépôt de référence explicitement défini, et non des capacités fictivement gratuites. Fonctions de résultat, budgets et protections humaines restent comparables entre politiques.

## 6.3 Scénarios de résistance

**A. Stable et récurrent :** problèmes apparentés, preuves de qualité modérée, possibilités de transfert. **B. Dérive contextuelle rapide :** changements de relations et analogies trompeuses mettant CAER en difficulté. **C. Expertise humaine rare :** faible disponibilité, délais et augmentation de la valeur du temps humain. **D. Compilation et maintenance coûteuses :** peu de réemplois, validation onéreuse et obsolescence. **E. Institutions fragmentées :** accès refusés, liens du graphe défaillants et limites de protection des données. **F. Dommages graves asymétriques :** événements peu probables à impact élevé et veto obligatoires. Exécuter **800 mondes appariés pour chacun** des six scénarios, après enregistrement du protocole. Un pilote de débogage ne doit pas être présenté comme une confirmation.

## 6.4 Résultats et contraintes impératives

**Indicateurs principaux (petit nombre fixé à l’avance) :** (i) utilité nette moyenne des services, après coûts directs et indirects ; (ii) résultat du bas de distribution, percentile P10 et perte moyenne au-delà d’un seuil défavorable ; (iii) coût complet en temps et argent par apprentissage utile ayant modifié une décision ; (iv) bénéfice validé du réemploi de capacités, net de maintenance. **Indicateurs secondaires :** erreurs graves, délais, heures d’expertise, couverture et équité entre groupes, empreinte écologique, transferts erronés, calibration des décisions, audits indépendants, reprise après interruption de service, participation et départ des organisations, coût de coordination du graphe. Les publier séparément, sans les masquer derrière un indice unique « d’intelligence ».

**Contraintes dures :** interdictions légales, sécurité, autorisation humaine pour les choix à conséquences, permissions d’accès, seuils écologiques et protections des publics vulnérables. Une action interdite ne reçoit pas simplement une amende monétaire ; elle devient inadmissible ou constitue une violation de gouvernance mesurée à part.

## 6.5 Analyse statistique

Pour chaque scénario et chaque monde $i$, calculer les **différences appariées** :

$$
\Delta_i=Y_i(P5)-Y_i(P0),\qquad i=1,\ldots,800,
$$

ainsi que les comparaisons P5–P4 et P5–P2. Rapporter la moyenne et la médiane des différences, un intervalle à 95 % calculé par *bootstrap apparié sur les mondes*, les percentiles P10/P90 et les distributions des dommages ; appliquer des intervalles d’incertitude binomiaux aux événements rares. Recommencer avec plusieurs graines indépendantes.

La variance Monte Carlo peut se réduire en augmentant les mondes, **sans valider pour autant les hypothèses**. Les analyses de sensibilité doivent identifier les seuils de bascule selon le bruit des preuves, la récurrence des problèmes, le délai d’expertise, le coût du compilateur, les erreurs de transfert et les frais de gouvernance. Les comparaisons principales sont définies à l’avance et les explorations secondaires présentées comme telles. Mesurer aussi la probabilité d’une **infériorité**. Un intervalle de confiance ne corrige pas une mauvaise spécification du modèle.

## 6.6 Conditions de réfutation

L’hypothèse de supériorité du système complet échoue, pour un scénario considéré, si la valeur publique nette n’augmente pas, si les coûts absorbent la valeur du réemploi, si les dommages ou inégalités dépassent les seuils, ou si les contraintes de gouvernance sont violées. La capacité d’**apprendre à apprendre** n’est pas étayée si P6 n’améliore pas les performances hors échantillon par rapport à P5, à flux de problèmes comparable. Le rendement cumulatif du compilateur n’est pas confirmé si les gains de réemploi ne remboursent pas compilation et maintenance. AER devrait être moins performant qu’une méthode simple lorsque le coût de l’information excède sa contribution aux décisions. Ces résultats négatifs sont des résultats scientifiques valables.

# 7. Ce qu’il faudra programmer et ce qui reste ouvert

**Composants exécutables requis :** générateur de mondes ; signatures problème/contexte ; mise à jour des croyances ; simulateurs de sources documentaires, d’experts et de micro-tests ; filtrage de sécurité ; AER ; IRAT ; appariement MIN ; résultats évalués ; compilateur et dégradation ; mémoires gouvernées ; CAER et interdictions de transfert ; graphe ; comptabilité des ressources ; politiques de comparaison ; exécution appariée ; graphiques et tableaux reproductibles au format CSV/Parquet. Chaque variable aléatoire devra posséder une distribution, des corrélations et des unités. Toute « valeur » économique devra être définie sans double comptage.

**Choix de conception encore ouverts :** mesure réelle de la valeur publique et arbitrages entre groupes ; normalisation et pondérations IRAT ; faisabilité juridique des échanges ; décision d’ouvrir un apprentissage comme commun ; vérité de référence pour identifier un apprentissage « utile » ; disponibilité et fiabilité des experts ; calibration de la distance contextuelle ; contribution causale du graphe ; horizon financier et actualisation ; comparaison avec les organisations existantes. Monte Carlo ne tranche pas seul ces questions.

# 8. Vérification, reproductibilité et limites de validité

Pour permettre une évaluation indépendante, l'implémentation devra publier les définitions des variables, les distributions et leurs corrélations, les unités, les paramètres, la configuration logicielle, les graines aléatoires, les journaux de décisions et les résultats complets, y compris les échecs. Des tests unitaires devront vérifier l'absence d'actions interdites, de dépassements budgétaires, de fuite de la vérité cachée vers les politiques et de réemplois gratuits ou sans provenance.

La vérification commencera par de petits mondes calculables analytiquement : information gratuite ou parfaite, sources inaccessibles, contextes sans similarité et experts indisponibles. Elle distinguera les défauts de programmation des résultats défavorables au modèle. Les différences appariées devront être reproductibles sur plusieurs graines ; les analyses de sensibilité devront rechercher activement les seuils de perte de performance. Les choix de valeurs publiques, les règles d'accès et les décisions de gouvernance doivent être documentés, et non présentés comme des propriétés neutres de l'algorithme.

Une reproduction informatique réussie ne valide ni les distributions retenues ni les effets économiques réels. L'étalonnage empirique requiert au moins un démonstrateur territorial borné et une comparaison indépendante avec des pratiques existantes. La preuve de l'efficacité du modèle demeure donc une question ouverte.

# 9. Conclusion

TLA 2 propose une articulation computationnelle explicite entre le routage adaptatif des preuves (AER), la sélection multicritère des micro-expériences (IRAT), la mobilisation ciblée de l'expertise humaine (MIN), la capitalisation gouvernée des expériences et leur réemploi contextuel (CAER). Elle distingue les concepts issus du Livre blanc, les mécanismes déjà développés dans TLA1 et les hypothèses supplémentaires nécessaires à leur mise en calcul. L'originalité recherchée ne réside pas dans chaque algorithme isolé, mais dans leurs interactions, leurs coûts, les possibilités d'abstention et les limites d'autonomie placées sous responsabilité humaine.

La première simulation Monte Carlo réalisée avec Dori, à la demande de Benoit Deschamps, illustre l'intérêt d'un premier examen quantitatif mais aussi l'importance d'un protocole explicite et vérifiable. Le présent article définit un cadre permettant de comparer des politiques concurrentes dans les mêmes mondes synthétiques, d'évaluer leurs effets nets et de rechercher leurs conditions d'échec. Il ne présente aucun résultat nouveau de simulation et ne prétend pas établir l'efficacité empirique de l'architecture.

La contribution est ainsi une **spécification théorique réfutable**, destinée à permettre l'implémentation, la contre-expertise et, ultérieurement, la confrontation du modèle aux observations territoriales. Sa valeur scientifique dépendra autant des résultats défavorables qu'elle rend possibles que des améliorations éventuelles qu'elle aidera à identifier.

# 10. Références bibliographiques

1. **Tanic, Émile.** *Et si l’IA pouvait rendre un territoire plus intelligent ? — Martinique Territoire Intelligent.* Édition publiée, 2026, format imprimé 6 × 9 pouces, [Amazon.fr, ASIN B0HLHC1MT2](https://www.amazon.fr/dp/B0HLHC1MT2). Pages citées dans le présent document : 12–29 (modèle TIIA) ; 61–72 (LTAA, IRAT, compilateur, mode miroir) ; 74–88 (gouvernance, mémoires, MIN) ; 127–130 (graphe et jumeaux de problème) ; 137–139 (évaluation). Les emplacements de l’édition Kindle peuvent varier selon l’appareil.
2. **Tanic, Émile.** *TLA — Territorial Learning Architecture: An AI-Assisted Learning Architecture for Territories.* Version anglaise EN_v2a, septembre 2026. DOI : <https://doi.org/10.5281/zenodo.22923636>. Point de départ de la présente spécification : AER, CAER et trois mémoires organisationnelles.
3. **Dori** (système d’IA créé par Benoit Deschamps), simulation réalisée à la demande de **Benoit Deschamps**. Résultats présentés et discutés dans *Simulation Monte-Carlo du LTAA — Comprendre la méthode, lire les résultats et apprécier leur portée*, note d’analyse du 2 octobre 2026, document communiqué dans le cadre de ce travail. La simulation compare trois stratégies sur 400 mondes simulés ; elle constitue un précédent méthodologique et non une validation empirique du modèle général.
