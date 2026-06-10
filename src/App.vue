<template>
  <div>
    <Navbar />
    <Hero />
    
    <ProjectSection 
      id="experiences" 
      title="Expériences professionnelles" 
      :projects="experiences" 
      @select-project="ouvrirModal" 
    />
    
    <ProjectSection 
      id="projets" 
      title="Projets réalisés" 
      :projects="projets" 
      @select-project="ouvrirModal" 
    />
    
    <Footer />

    <ProjectModal 
      :project="projetSelectionne" 
      @close="fermerModal" 
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import ProjectSection from './components/ProjectSection.vue'
import ProjectModal from './components/ProjectModal.vue'
import Footer from './components/Footer.vue'

const projetSelectionne = ref(null)

const ouvrirModal = (projet) => {
  projetSelectionne.value = projet
}

const fermerModal = () => {
  projetSelectionne.value = null
}




// 1. Nouvelle constante pour vos expériences professionnelles (Stages, Alternances, CDD, CDI)
const experiences = ref([
  {
    id: 'stage-insep',
    titre: 'Stage Ingénieur Data',
    date: 'Juin - Aout 2023',
    descriptionShort: "Traitement de données d'athlètes de très haut niveau afin d'améliorer les performances.",
    image: 'photo/logo_insep.png', // S'affichera sur la carte si l'icône ci-dessous n'est pas présente
    //icon: 'bi-briefcase',
    technos: ['Excel', 'VBA', 'Python', 'SQL'],
    contexte: "A un an des Jeux Olympiques Paris 2024 j'ai pu réaliser un stage au sein de l'INSEP (Institut National du Sport, de l'Expertise et de la Performance). J'ai accompagné les équipes de boxe et à l'aide de données récupérées l'objectif était d'identifier des patterns efficaces et modéliser des simulations afin d'accompagner les athlètes, et améliorer la performance au vue des enjeux.",
    realisation: "Durant la première partie du stage, j'ai participé à la collecte de données auprès des athlètes, à l'aide de capteurs placés pendant les sessions d'entrainement. Les capteurs récoltaient en temps réel les coordonnées, qui a permis par la suite de reconstruire les trajectoires, la vitesse, l'accélération et l'impact des coups. Les sessions étaient filmées et des vidéos de tous les adversaires ont aussi été récupérées afin d'enrichir la base de donnée de la Fédération Française de Boxe. \nDans un second, j'ai rejoint les équipes de l'IRMES, l'institut de recherche de l'INSEP. J'ai alors mené diverses analyses sur les données afin d'établir pour chaque athlète un rapport mettant en avant les patterns de coups efficaces. Ces données ainsi que les vidéos ont permis de développer des jumeaux numériques virtuels afin d'offrir une nouvelle technologie d'entrainement aux athlètes.",
    /*pointsCles: [
      "Modélisation et optimisation des flux de données.",
      "Déploiement de microservices isolés sous Docker Compose.",
      "Collaboration au sein d'une équipe technique en méthodologie Agile."
    ],*/
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  },

  {
    id: 'stage-axa',
    titre: 'Stage Ingénieur Data',
    date: 'Avril - Aout 2025',
    descriptionShort: "Gestion de très gros volumes de données pour analyser l'évolution de l'arrêt de travail en France depuis les années 2010.",
    image: 'photo/logo_axa.png', // S'affichera sur la carte si l'icône ci-dessous n'est pas présente
    //icon: 'bi-briefcase',
    technos: ['Databricks', 'PySpark', 'Big Data'],
    contexte: "J'ai rejoint la Direction Prévoyance Individuelle d'AXA France dans l'équipe de data scientist. L'objectif de la mission était d'explorer l'ensemble des données stockées par AXA afin de construire de nouvelles tables en vue d'analyser l'évolution de l'arrêt de travail et les mécanismes l'expliquant.",
    realisation: "Avec PySpark dans l'environnement Databricks, j'ai manipulé de très grosses tables de données, répertoriant les contrats, les garanties, les primes, les informations des clients... A partir de ces dernières il a fallu imaginer et concevoir de nouvelles tables sur lesquelles appliquer par la suite des algorithmes de Machine Learning. Les données pouvant être anciennes, et donc structurées différemment, ou comportant des erreurs, une très grosse étape de traitement a été nécessaire en amont de la construction des tables afin de ne garder que de la donnée propre pour la suite de l'étude.",
    /*pointsCles: [
      "Modélisation et optimisation des flux de données.",
      "Déploiement de microservices isolés sous Docker Compose.",
      "Collaboration au sein d'une équipe technique en méthodologie Agile."
    ],*/
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  },

  {
    id: 'stage-dassaults_systemes',
    titre: 'Stage Ingénieur Data et IA',
    date: 'Février - Juillet 2026',
    descriptionShort: "Construction de nouveaux modèles de données et supports d'analyse, en intégrant des agents IA.",
    image: 'photo/logo_dassault_systemes.png', // S'affichera sur la carte si l'icône ci-dessous n'est pas présente
    //icon: 'bi-briefcase',
    technos: ['3D Plateforme', 'Netvibes', 'Java', 'Python', 'Agents IA', 'Data Visualisation'],
    contexte: "J'ai rejoint les équipes R&D de BIOVIA, la branche 'Sciences de la vie et Santé' de Dassault Systèmes. Les équipes développent des outils pour de nombreux clients. Un des secteurs de BIOVIA concerne la création et la gestion de recettes (chimiques, cosmétiques, alimentaires...) à partir de matériaux et substances. L'enjeu de ce stage est de tester de nouvelles méthodes de construction des modèles de données et développer de nouvelles solutions d'analyse plus précises et efficaces, en y intégrant des agents IA.\nA BIOVIA il est possible de créer des recettes en ajoutant des matériaux (dont on indique le pourcentage dans la compostion). Pour chaque matériau ainsi utilisé un nouvel ingrédient est généré. De plus lorsqu'une recette est éditée, un matériau est automatiquement créé. Ainsi il est possible d'utilisé un matériau issu d'une recette en tant qu'ingrédient d'une nouvelle recette. Ce phénomène peut entrainer une infinité de niveau de récursivité dans la composition d'une recette initiale.",
    realisation: "A l'aide des outils Netvibes j'ai commencé par construire un modèle de données consolidées avec toutes les informations qui vont nous intéresser par la suite. Le modèle comporte trois classes, avec chacune ses propres attributs :",
    pointsCles: [
      "Recipe : contient les recettes",
      "Material : contient tous les matériaux (matériaux primaires et ceux issus de recettes)",
      "Ingredient : contient tous les ingrédients. Dans cette classe, je recalcule le pourcetange de l'ingrédient dans la composition de la recette originale, en prenant en compte la récursivité potentielle"
    ],
    realisation_2:"Une fois le modèle de données construit je peux appliquer d'autres requêtes pour construire une page de visualisation de la donnée. Grâce à cette interface un utilisateur à la possibilité de :",
    pointsCles_2: [
      "Consulter le détail de la composition d'une recette avec la liste de tous ses ingrédients (et leur provenance s'il y a de la récursivité)",
      "Chercher toutes les recettes contenant tel ingrédient et avec telles métriques (min/max pourcentage et masse)",
      "Chercher toutes les recettes contenant des ingrédients provenant de tel fournisseur",
      "Chercher toutes les recettes excluant telle liste d'ingrédients",
      "Appliquer des filtres sur les recettes (coût, type, forme, date...)",
      "Comparer simplement plusieurs recettes",
    ],
    realisation_3:"Enfin j'ai intégré les agents IA internes dans la solution afin de simplifier l'expérience utilisateur.",
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  },

  {
    id: 'parcours-recherche',
    titre: "Utilisation des techniques d'IA pour la prévention de maladies neurodégénératives",
    date: 'Septembre 2024 - Janvier 2026',
    descriptionShort: "Rédaction d'un état de l'art sur les méthodes actuellement employés pour la détection de ces maladies à un instant t et recherche de nouvelles solutions de prévention sur le long terme.",
    image: 'photo/logo_dvrc.jpg', // S'affichera sur la carte si l'icône ci-dessous n'est pas présente
    //icon: 'bi-briefcase',
    technos: ['Python', 'LaTeX', 'PETscan / IRM', 'Réseaux neuronaux convolutifs (CNN)'],
    contexte: "Dans le cadre de mes études j'ai pu, en parallèle de mon diplôme d'ingénieur, suivre une formation de chercheur dans le laboratoire de l'école. Avec un ami spécialisé en santé et biotechnologie, nous avons décidé de nous intéresser à l'emploi des nouvelles technologies, notamment l'arrivée prépondérante de l'IA, pour le suivi des maladies neurodégénératives, et principalement Alzheimer.",
    realisation: "Dans un premier temps, nous avons dressé un état de l'art sur toutes les méthodes employées actuellement pour Alzheimer et l'Atrophie Corticale Postérieure (ACP), qui est une autre maladie neurodégénérative considérée comme étant pré-Alzheimer. L'ACP est une maladie relativement rare mais un patient atteint développerait dans 80% des cas Alzheimer par la suite. \nL'objectif était, à travers cette synthèse, de déterminer dans quelle mesure l'analyse et le diagnostic de l'ACP pouvait être déterminante pour une meilleure prévention d'Alzheimer. Il était aussi intéressant de comparer les solutions techniques utilisées pour ces deux maladies parentes. \nLa prinicpale difficulté était le peu de données disponibles concernant l'ACP, de part la rareté de la maladie.\n\n Dans un second temps, nous nous sommes concentrés sur Alzheimer et avons cette fois, grâce aux données publiques fournies par OASIS, mené une étude longitudinale. Contrairement aux algorithmes qui prédisent l'état de santé, sain ou malade, à un instant t à partir d'une IRM, nous avons travaillé sur des solutions qui à partir de l'études de plusieurs IRM pour un même patient prédisent le risque de développer la maladie à terme. \nEn se basant sur les différences entre les IRM de patients sains qui sont devenus malades, nous pouvons établir la probabilité pour les patients sains d'avoir Alzheimer à moyen/long terme. Plutôt que de travailler sur un diagnostic immédiat nous nous sommes concentrés sur la question de la prévention de risques.",
    /*pointsCles: [
      "Modélisation et optimisation des flux de données.",
      "Déploiement de microservices isolés sous Docker Compose.",
      "Collaboration au sein d'une équipe technique en méthodologie Agile."
    ],*/
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  }
])



const projets = ref([
  {
    id: 'ENS-challenge-trains',
    titre: 'Challenge ENS : horaire de trains',
    descriptionShort: "Conception et programmation d'un microcontrôleur pour l'optimisation énergétique de capteurs IoT industriels.",
    image: 'photo/test.png',
    icon: 'bi-cpu',
    technos: ['Python', 'Machine Learning'],
    contexte: "Optimisation de la consommation d'énergie sur des capteurs industriels complexes.",
    realisation: "Programmation de tâches prioritaires sous FreeRTOS et optimisation des modes de veille du processeur.",
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  },

  {
    id: 'entreprise-C#',
    titre: "Construction d'une entreprise en POO",
    descriptionShort: "Utilisation de C# pour construire la structure d'une entreprise",
    image: 'photo/test.png',
    icon: 'bi-cpu',
    technos: ['Programmation Orientée Objet ', 'C#'],
    contexte: "Optimisation de la consommation d'énergie sur des capteurs industriels complexes.",
    realisation: "Programmation de tâches prioritaires sous FreeRTOS et optimisation des modes de veille du processeur.",
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  },

  {
    id: 'magic_gathering',
    titre: "Suivre la valeur d'une collection de cartes en temps réel",
    descriptionShort: "Utilisation de webscrapping afin de récupérer la valeur de chaque carte et consulter l'évolution au fil du temps.",
    image: 'photo/magic_logo.png',
    modalImage: 'photo/magic_logo.png',
    icon: 'bi-graph-up-arrow',
    technos: ['Python', 'Excel', 'SQL', 'Webscrapping'],
    contexte: "Je suis un très grand passionné de cartes Magic the Gathering et j'ai accumulé un très grand nombre pour les collectionner. Je me retrouve actuellement avec plusieurs milliers de cartes. L'objectif est de pouvoir suivre l'évolution de la valeur de ma collection à l'aide d'une application simple et gratuite.",
    realisation: "Pour ce faire, j'ai commencé par recenser l'entièreté de mes cartes dans des feuilles Excel, qui permettent d'être rapide dans l'écriture des données. Une fois les données prêtes, je les injecte dans un script python. Ce dernier utilise la bibliothèque streamlit pour me renvoyer vers un interface interactif dans lequel je peux consulter l'ensemble des données de mes cartes, en appliquant toutes sortes de filtres. Le grand intérêt est de pouvoir actualiser la valeur de chacune des cartes via du webscrapping. Pour cela j'utilise les informations contenues dans scryfall.com. \nJe peux ainsi :",
    pointsCles: [
      "Charger la valeur de chacune des cartes à la date du jour.",
      "Suivre l'évolution statistique de la valeur totale au fil du temps.",
      "Consulter les cartes ayant la plus forte valeur.",
      "Afficher celles qui ont eu la plus forte progression entre la dernière date et la précédente.",
      "Filtrer sur les caractéristiques des cartes (rareté, type, édition…) afin d'affiner la recherche."
    ],    
    galerie: [
      { src: '/photo/stats_globales.png', alt: 'Statistiques globales au cours du temps' },
      { src: '/photo/top_evolutions.png', alt: 'Editions avec la meilleure évolution' },
      { src: '/photo/top_cartes.png', alt: 'Cartes avec la plus grosse valeur' }
    ],
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  },
  {
    id: 'spark-adresses',
    titre: "Gestion de millions d'adresses en France",
    descriptionShort: "Utilisation de Spark afin d'assurer un suivi continu de dizaines de millions d'adresses en France métropolitaine.",
    //image: 'photo/test.png',
    modalImage: 'photo/magic_logo.png',
    icon: 'bi-database-fill',
    technos: ['Spark', 'Big Data'],
    contexte: "Ce projet est une solution de traitement et de gestion de données massives dédiée à la Base Adresse Nationale. L'objectif principal de ce programme est d'industrialiser l'ingestion, le suivi des modifications quotidiennes et la consolidation de fichiers contenant des dizaines de millions de lignes d'adresses. Le système est conçu pour maintenir un état historique des changements tout en offrant une vue unifiée et instantanée des données d'adresses à travers le pays.",
    realisation: "Le fonctionnement initial du projet repose sur une phase de préparation et de mise à jour des données sources. À l'aide d'un script d'automatisation, le programme commence par purger les anciennes données stockées localement pour télécharger la version la plus récente du fichier compressé officiel, qui pèse environ 1,4 Go. \nUne fois le fichier récupéré, l'utilisateur configure les variables d'environnement indispensables à Spark, notamment la date d'exécution et le chemin d'accès absolu vers le fichier CSV source, avant de lancer le traitement principal via un script ordonnanceur. Au cœur du traitement applicatif, le moteur Apache Spark (exécuté ici en version 4.0.1 avec Java 21) prend en charge le traitement distribué des données. \nLors du tout premier lancement du programme, Spark ingère l'intégralité du fichier source, ce qui représente l'insertion massive de plus de 27 millions de lignes de données géolocalisées. À l'issue de cette exécution, le système structure automatiquement les résultats dans un répertoire de base de données, scindé en deux sous-dossiers stratégiques : bal_diff et bal_latest. Le premier dossier, bal_diff, stocke l'historique des modifications quotidiennes selon un partitionnement par date, tandis que le second, bal_latest, consolide de manière permanente et complète la version propre la plus récente des adresses, optimisée au format de stockage orienté colonne Parquet. \nPour assurer le suivi et la validation de la cohérence des données, le projet intègre plusieurs outils de vérification et d'analyse statistique :",
    pointsCles: [
      "Un premier script permet d'inspecter les lignes modifiées, insérées ou supprimées pour une date spécifique, affichant la structure détaillée du schéma des données (identifiants, géolocalisation, nom de voie, code commune, code département et clé de hachage du contenu) ainsi que la nature de l'opération effectuée (INSERT, UPDATE ou DELETE).",
      "Un deuxième permet de visualiser la table finale consolidée à l'instant t.",
      "Un autre génère un rapport statistique avec des indicateurs globaux, comme le nombre total d'adresses traitées ou le classement des 20 départements français comportant le plus grand volume d'adresses enregistrées.",
      "Un dernier exécute un mécanisme avancé de reconstruction et d'extraction historique qui, à partir des fichiers d'archives, permet de recalculer l'état exact du référentiel d'adresses à n'importe quelle date."
    ],
    galerie: [
      { src: '/photo/stats_globales.png', alt: 'Statistiques globales au cours du temps' },
      { src: '/photo/top_evolutions.png', alt: 'Editions avec la meilleure évolution' },
      { src: '/photo/top_cartes.png', alt: 'Cartes avec la plus grosse valeur' }
    ],
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  },
  {
    id: 'chatbot-esilv',
    titre: "Agent conversationnel pour l'ESILV",
    descriptionShort: "Création d'un agent capable de répondre à toutes sortes de questions à propos de l'Ecole Supérieure d'Ingénieurs Léonard de Vinci.",
    //image: 'photo/test.png',
    modalImage: 'photo/chatbot.jpg',
    icon: 'bi-chat-dots-fill',
    technos: ['Python', 'Docker', 'Agents IA', 'Ollama', 'RAG'],
    contexte: "Dans toutes les grandes écoles d'ingénieurs la charge de travail administratif est très lourde et peut s'avérer complexe à gérer. De nombreux documents, sous divers formats, sont stockés à différents endroits, ce qui peut compliquer l'accès à l'information. Pour remédier à ce problème, l'ESILV dispose actuellement d'un système de FAQ comprenant plusieurs centaines de questions. Lorsque les étudiants saisissent leur question dans la barre de recherche, une liste de questions contenant les mêmes mots-clés s’affiche. Cependant, il arrive parfois que la question posée ne corresponde à aucune des autres, et l’étudiant doit alors contacter directement l’administration ou prendre le temps de rechercher la réponse par lui-même. Dans les deux cas, cela entraîne une perte de temps considérable, qui pourrait être évitée pour tout le monde. L'objectif est de développer une solution capable de comprendre le langage naturel et de puiser ses réponses directement dans l'ensemble de la documentation disponible, ainsi que directement sur le site internet de l'école. La solution a été de développer un RAG (Retrieval-Augmented Generation). Cette méthode permet d’ancrer les réponses du modèle linguistique dans une base de connaissances vérifiable.",
    realisation : "La solution repose sur une architecture de microservices isolés et orchestrés par Docker Compose. L'application se divise en trois piliers : une interface utilisateur développée avec Streamlit qui gère l'affichage du chat et les outils d'administration ; un serveur d'application propulsé par FastAPI qui centralise la logique métier, l'accès aux bases de données et la gestion de la mémoire ; et enfin un moteur d'inférence local Ollama. Ce dernier fait tourner de manière stable et isolée le modèle Llama 3.2 (version 3B), choisi parce qu'il est suffisamment léger pour s'exécuter sur la mémoire vive d'un ordinateur standard tout en restant performant pour suivre des instructions complexes.\nLe modèle est configuré avec un prompt système strict qui le transforme en un agent de vérification des faits, obligé de citer ses sources. L'efficacité du système RAG dépend d'un pipeline d'ingestion et de traitement de données rigoureux, capable de :",
    pointsCles: [
      "Gérer des fichiers CSV (ex : les anciennes FAQ), chaque ligne étant traitée comme une unité autonome enrichie de métadonnées précises (thème, statut du document, titre de section) permettant au chatbot d'indiquer ses sources avec exactitude.",
      "Gérer des documents PDF non structurés (ex : règlements pédagogiques et guides de vie étudiante). Les PDF sont extraits via PyPDF2 et nettoyés à l'aide d'expressions régulières (Regex) pour éliminer les artefacts visuels et les sauts de ligne intempestifs, avant d'être découpés en segments textuels cohérents.",
      "Ajouter de l'information à l'aide d'un script de scraping qui collecte, nettoie, dédoublonne et normalise le contenu textuel provenant des sections stratégiques du site web de l'école."
    ],
    realisation_2:"Toutes ces données sont ensuite transformées en vecteurs mathématiques par le modèle d'embedding dynamique all-MiniLM-L6-v2 -préféré pour son très bon compromis entre précision sémantique, sa faible empreinte mémoire et sa vitesse d'exécution sur CPU— puis indexées dans une base de données vectorielle FAISS.\n\nLe fonctionnement interne de l'assistant s'articule autour d'une collaboration entre plusieurs agents spécialisés. Lorsqu'un étudiant pose une question, l'Agent Retriever vectorise la requête, scanne la base FAISS, filtre les doublons et sélectionne les blocs de texte affichant les meilleurs scores de similarité sémantique.\nL'Agent de Synthèse récupère ces extraits ainsi que l'historique de la conversation pour formuler une réponse naturelle et chaleureuse, sans jamais inventer d'information. \nAfin d'éviter la saturation de la mémoire du modèle et le ralentissement des calculs sur CPU lors de longs échanges, un Agent de Supervision et de Mémoire surveille la longueur de la discussion. Dès que le seuil de cinq messages est atteint, il demande au LLM de générer un résumé condensé de l'échange qui servira de nouveau point de départ contextuel.\n\nEnfin, le projet intègre une gestion stricte de la sécurité et des outils de pilotage destinés aux administrateurs. Contrairement à l'interface étudiant qui est limité à l'espace de questions, l'interface administrateur, accessible par mot de passe, offre une transparence totale :",
    pointsCles_2:[
      "Il est possible de charger dynamiquement de nouveaux documents qui sont instantanément indexés.",
      "L'administrateur dispose d'un panneau de débogage affichant les métriques de recherche (documents trouvés, scores mathématiques de similarité).",
      "Il a aussi à disposition un tableau de bord statistique pour analyser l'historique des requêtes, le volume quotidien, les thématiques les plus consultées (stages, alternances) et les temps de réponse."
    ],
    realisation_3:"La viabilité de la solution a été validée par un protocole d'évaluation automatisé où Llama 3.2 a été utilisé comme « juge » sur des cas réels, attribuant des scores majoritaires de 4 ou 5 sur 5, tout en mettant en lumière des pistes d'amélioration pour rendre les réponses futures encore plus spécifiques et détaillées.",
    galerie: [
      { src: '/photo/chatbot_accueil.png', alt: 'Accueil utilisateurs (profil administrateur)' },
      { src: '/photo/chatbot_rag.png', alt: 'Alimentation dynamique du RAG' },
      { src: '/photo/chatbot_analyse_rag.png', alt: 'Analyse des résultats fournis RAG' },
      { src: '/photo/chatbot_historique.png', alt: "Historique des questions posées au chatbot" },
      { src: '/photo/chatbot_juge.png', alt: 'Evaluation de la performance de la solution' }
    ],
    resultatFinal: "Les tests en conditions réelles ont validé une réduction de 68 % de la consommation d'énergie, augmentant l'autonomie théorique du capteur de 12 à 34 mois.",
    github: 'https://github.com'
  }
])
</script>