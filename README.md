# Creation-d-un-Agent-IA-avec-MCP
Création d’agents IA avec Claude et le Model Context Protocol (MCP)

# 1.Présentation du projet 🧠🤖
## L'intelligence artificielle (IA) conversationnelle ne se limite plus à des modèles statiques. Le Model Context Protocol (MCP) permet d'intégrer des services externes et d'exécuter des actions pour rendre les agents IA plus autonomes et interactifs. Ce guide explique comment configurer et utiliser MCP avec Claude AI pour créer des agents capables de récupérer des données en ligne, analyser des informations et automatiser des tâches complexes.

### L'objectif de ce projet est de construire notre propre agent IA, capable de se connecter directement à Internet pour accomplir des tâches précises et automatisées. Grâce au Model Context Protocol (MCP), notre agent pourra :

### ✅ Envoyer des e-mails personnalisés en fonction du contexte et des besoins.
### ✅ Effectuer des recherches ciblées sur Internet et générer des résumés précis.
### ✅ Analyser des documents et structurer des informations pour faciliter la prise de décision.
### ✅ Éviter les hallucinations de l’IA en s’appuyant sur des sources fiables et vérifiables.

### Ce guide vous accompagne pas à pas dans la configuration et l'utilisation de cet agent IA avancé, en exploitant Claude AI et des outils puissants comme Puppeteer, Notion, et Brave Search.

### 🚀 Avec cet agent, nous passons d’un simple modèle conversationnel à une IA proactive et efficace, capable d’agir pour nous sur le web !
 
 # Présentation générale du Model Context Protocol (MCP)
Le Model Context Protocol (MCP) est un protocole conçu pour “brancher” un ou plusieurs outils ou services externes à un modèle d’IA, afin de rendre la conversation (ou l’agent) plus puissante et plus flexible. L’idée consiste à :
●	Exécuter des tâches (analyse, actions web, requêtes API, etc.) au nom de l’IA.

●	Fournir des informations supplémentaires (p. ex. résultats de recherche internet, transcription audio/vidéo, etc.) à un modèle conversationnel (par exemple Claude, GPT, etc.).

●	Centraliser la configuration permettant à l’agent d’utiliser ces services.

Ce protocole permet en quelque sorte de créer un “agent IA” capable d’agir dans différents contextes. L’installation s’effectue en plusieurs étapes : installation de Claude Desktop, activation du mode développeur, ajout de Node.js, configuration du fichier de settings, etc.
________________________________________
# 2. Prérequis et installation de Claude AI Desktop
1.	Télécharger Claude AI Desktop
 Rendez-vous sur le lien officiel :
 https://claude.ai/download
 Choisissez la version correspondant à votre système d’exploitation (Windows, macOS, …).

2.	Installation

○	Windows : Exécutez le fichier .exe téléchargé et suivez les instructions d’installation classiques (lieu de stockage, raccourcis, etc.).

○	macOS : Ouvrez le fichier .dmg ou .pkg et faites glisser l’icône de Claude dans le dossier Applications, puis validez l’installation.

3.	Lancement

○	Sur Windows, vous devriez trouver Claude dans le menu Démarrer.

○	Sur macOS, double-cliquez simplement sur Claude dans votre dossier Applications.

________________________________________
# 3. Activation du mode développeur dans Claude AI Desktop
Une fois Claude AI Desktop installé et lancé, vous devez activer le “mode développeur” pour pouvoir configurer des plugins ou utiliser des protocoles externes (comme le MCP).
Les étapes peuvent varier selon la version de Claude. Généralement, vous trouverez :
1.	Préférences / Paramètres

○	Soit via un menu “Préférences”, “Paramètres” ou “Settings” accessible directement dans l’interface de Claude.

○	Ou via un raccourci du type Ctrl + , (Windows) / Cmd + , (macOS).

2.	Mode Développeur / Developer Mode

○	Recherchez la mention “Developer mode” ou “Advanced settings”.

○	Activez cette option.

3.	Redémarrer Claude
 Souvent, il est nécessaire de redémarrer Claude pour prendre en compte le changement de mode.

________________________________________
# 4. Smithery : bibliothèque pour rechercher des outils
Pour enrichir les capacités de votre agent IA, vous pouvez employer différentes bibliothèques d’outils. L’une d’entre elles, mentionnée dans votre question, est Smithery :
●	Smithery : https://smithery.ai/

Ce répertoire réunit de nombreux scripts et plugins utilisables avec un agent IA. C’est un peu l’équivalent d’un “app store” pour les fonctionnalités d’IA.
Méthode d’usage :
●	Vous vous rendez sur https://smithery.ai/ pour chercher un outil ou un plugin particulier (ex. un module d’analyse sentimentale, un connecteur à l’API Notion, etc.).

●	Selon la documentation fournie par Smithery, vous verrez comment installer chaque plugin.

________________________________________
# 5. Installation de Node.js
Node.js est un environnement d’exécution JavaScript côté serveur. C’est crucial pour faire fonctionner divers scripts, serveurs ou installateurs relatifs au MCP.
●	Téléchargez Node.js depuis la page officielle : https://nodejs.org/en.

○	Choisissez la LTS (version stable de support à long terme) ou la plus récente, selon vos préférences.

●	Installez Node.js en suivant les étapes de l’installateur.

Pour vérifier l’installation, ouvrez un terminal et tapez :
node -v
npm -v

Vous devriez voir un numéro de version pour chacun (par ex. node v18.12.1, npm 8.19.2, etc.).
________________________________________
# 6. Configuration sous Windows / macOS
Selon votre système, vous aurez éventuellement besoin de personnaliser la configuration de Claude AI Desktop :
Sur Windows
●	Le fichier de configuration de Claude se situe souvent dans le dossier %APPDATA%.

Chemin par défaut (à adapter si nécessaire) :



%APPDATA%\Claude\claude_desktop_config.json
●	
●	Vous pourrez y ajouter/manipuler des clés d’API, des plugins, ou des paramètres MCP (si le workflow l’exige).

Sur macOS
●	Le chemin est souvent similaire mais localisé dans le dossier ~/Library/Application Support/Claude/.

Par exemple :



~/Library/Application Support/Claude/claude_desktop_config.json
○	
●	Vérifiez bien que vous avez les droits d’écriture pour modifier ce fichier.

________________________________________
# 7. Installation de MCP Installer
Pour l’installer, vous pouvez vous référer au dépôt GitHub suivant :
 https://github.com/anaisbetts/mcp-installer
1.	Installation

○	Ouvrez votre terminal (ou invite de commandes).

Exécutez :

 
npm install -g mcp-installer
○	
Selon vos droits, vous devrez peut-être exécuter la commande en sudo sur Linux / macOS :



sudo npm install -g mcp-installer
○	
2.	Problèmes de permission

Si vous rencontrez un problème du type EACCES, vous pouvez lancer :



sudo chown -R $(whoami) ~/.npm
○	
○	Cette commande redonne au compte courant (vous) la propriété du dossier ~/.npm.

3.	Vérifier l’installation

Une fois l’installation terminée, vérifiez :



mcp --help
○	
○	Vous devriez voir un message d’aide indiquant les différentes commandes disponibles.

________________________________________
# 8. Accès à Internet via Puppeteer (mcp-servers)
Le but ici est de doter votre agent IA d’un accès internet (pour la recherche, le scraping, la récupération d’informations, etc.). Le projet mentionné :
 https://github.com/modelcontextprotocol/servers/tree/main/src/puppeteer
C’est un module permettant de lancer un serveur Puppeteer (headless Chrome) relié à votre agent. Cela lui autorise :
●	La navigation web (ouvrir des pages, extraire du contenu)

●	L’exécution de requêtes (cliquer sur un bouton, remplir un formulaire)

●	Le scraping de données (lecture du DOM, récupération d’éléments précis)

Installation
Cloner ou télécharger le code :



git clone https://github.com/modelcontextprotocol/servers.git
1.	
2.	Accéder au dossier servers/src/puppeteer.

Installer les dépendances :



cd servers/src/puppeteer
npm install
3.	
Démarrer le serveur :


npm run start
4.	
5.	Configurer ensuite votre agent pour pointer vers ce serveur Puppeteer (détails selon la documentation ou votre fichier de config “claude_desktop_config.json”).

________________________________________
# 9. Transcription de vidéos YouTube
Il est possible de transcrire des vidéos YouTube (ou d’autres sources) grâce à un outil tiers mentionné dans votre liste :


curl -LsSf https://astral.sh/uv/install.sh | sh

Celui-ci va installer un script (souvent “uv” ou “unofficial-youtube-transcription tool”) permettant :
●	Récupération de la piste audio d’une vidéo YouTube.

●	Transcription via un moteur interne (souvent Whisper ou tout autre STT, speech-to-text).

Une fois le script installé, vous pourrez exécuter une commande du type :


uv https://www.youtube.com/watch?v=ID_DE_LA_VIDEO

Le script pourra alors :
●	Télécharger la vidéo.

●	Générer une transcription texte.

●	Envoyer cette transcription à Claude ou à un autre agent si vous l’avez configuré dans le protocole MCP.

________________________________________
# 10. Possibles cas d’usage
A. Analyse de marché et visualisation de site web
●	Analyse de marché : avec Puppeteer, l’agent IA peut scraper des données de marché, récolter des informations sur des produits, prix, tendances, etc.

●	Visualisation de site web : on peut faire prendre des captures d’écran, générer des rapports, etc.

B. Transcription de vidéo YouTube
●	Nous venons de le voir : la commande uv (ou un outil équivalent) permet de récupérer la vidéo, la transcrire, et ainsi offrir un résumé ou une analyse par Claude.

C. Intégration à Notion
●	Certains plugins (ex. sur Smithery ou ailleurs) connectent Claude/MCP à l’API Notion.

●	On peut ainsi automatiser la création de pages, l’ajout de notes transcrites, etc.

D. Ajout de MCP dans Cursor (ex. Brave Search)
●	“Cursor” est un éditeur/IDE pouvant intégrer des plugins d’IA.

Si vous souhaitez brancher l’API Brave via MCP, la commande donnée est :



BRAVE_API_KEY=TA_CLÉ npx -y @modelcontextprotocol/server-brave-search
●	 Ici, vous définissez la variable d’environnement BRAVE_API_KEY avec votre clé Brave, puis lancez @modelcontextprotocol/server-brave-search.

●	Cela permet à l’agent IA d’effectuer des recherches via Brave Search et de renvoyer le contenu à Claude.

________________________________________
# 11. Conclusion
En suivant ce guide, vous aurez :
1.	Installé et configuré Claude AI Desktop.

2.	Activé le mode développeur pour permettre l’ajout de plugins/outils.

3.	Installé Node.js pour gérer les différents modules MCP.

4.	Accédé au fichier de configuration (selon Windows ou macOS).

5.	Installé et configuré MCP Installer pour ajouter des capacités à votre agent.

6.	Mis en place un serveur Puppeteer permettant l’accès à des pages web.

7.	Installé un script de transcription pour YouTube (ou d’autres).

8.	Exploré quelques usages potentiels (analyse de marché, integration Notion, Brave Search…).

L’objectif final est de doter Claude (ou un autre modèle conversationnel) d’une capacité d’action étendue : il ne se contente plus de “répondre” à des questions, mais peut s’exécuter au travers d’outils (scraper du contenu, se connecter à un site, réaliser des recherches, etc.). C’est tout l’intérêt du Model Context Protocol.
________________________________________
Ressources complémentaires
●	Site officiel du Model Context Protocol :
 https://modelcontextprotocol.io/quickstart/user

●	Smithery.ai :
 https://smithery.ai/

●	MCP Installer :
 https://github.com/anaisbetts/mcp-installer

●	Serveurs MCP / Puppeteer :
 https://github.com/modelcontextprotocol/servers/tree/main/src/puppeteer

En suivant scrupuleusement ces étapes, vous devriez pouvoir créer votre agent IA “MCP-compatibles” avec Claude. Bonne mise en place et bonne expérimentation !

●	n audio/vidéo, etc.) au modèle conversationnel (Claude, GPT, etc.).

●	Centraliser la configuration pour que l’IA puisse exploiter ces services.

Grâce à ce protocole, vous pouvez créer un “agent IA” capable de travailler dans divers contextes. L’installation suit plusieurs étapes : installer Claude Desktop, activer le mode développeur, ajouter Node.js, configurer le fichier de paramètres, etc.
________________________________________


Ressources complémentaires
●	Site officiel du Model Context Protocol :
 https://modelcontextprotocol.io/quickstart/user

●	Smithery.ai :
 https://smithery.ai/

●	MCP Installer :
 https://github.com/anaisbetts/mcp-installer

●	Serveurs MCP / Puppeteer :
 https://github.com/modelcontextprotocol/servers/tree/main/src/puppeteer

