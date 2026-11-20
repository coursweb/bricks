---
layout: page
title: Bricks et IA
permalink: bricks-et-IA.html
---

Cette page montre une méthode pour travailler avec Bricks et des agents AI.

Les outils utiliés: 

1. Bricks, dans la version 2.4 ou plus récente.
2. [OpenCode](https://opencode.ai/), qui comporte des modèles gratuits optimisés pour le code. 
3. [Figma Console MCP](https://github.com/southleft/figma-console-mcp) pour la connexion à Figma. C'est un utiliataire gratuit et open source.

### 1) Activer les fonctions IA dans Bricks

Depuis Bricks 2.4, il existe une implémentation officielle de l'AI. 

- Dans les réglages de Bricks, se rendre dans l'onglet AI. [Voir la documentation](https://academy.bricksbuilder.io/builder/features/ai-abilities-and-skills/).
- Activer les capacités IA de Bricks.
- Suivre les indications données (notamment installation MCP Adapter pour WordPress).
- Générer un mot de passe d'application. Le copier et conserver, car il ne sera plus affiché par la suite.

### 2) Relier votre IA à Bricks

Bricks va vous donner un message de configuration (sous *Choose how to connect* > *Copy a prompt*), que vous donnez à votre agent IA. Cela commence par: 

````
Add this WordPress site as an MCP server in this AI client.

Connection details:
- Server URL: INFO_URL
- Username: INFO_USERNAME
- Application password: INFO_MOT_DE_PASSE

etc...
```

OpenCode va appliquer la configuration pour se connecter à ce site. 

Ensuite, vous devez exécuter une commande optionnelle (fournie par Bricks) pour donner à l'IA les "skills" pour utiliser Bricks:

```
Install the Bricks skills package for this AI client.

Source repository: https://github.com/codeerhq/bricks-skills

Read the repository README and use the install method that matches this client.
Prefer the latest public GitHub release when the client needs a downloadable archive.
If this client cannot install skills or plugin-style guidance, stop and say so.
After installation, report the installed Bricks skill names and whether this client needs a restart or new chat to load them.
```

Après cette commande, OpenCode installe toute une série de "skills" pour bricks.

Ensuite, lui demander de lister les skills installées: 

```
Do not make changes. List the client-side skills loaded in this client whose names start with `bricks-`. For each skill, include the skill name and install location if this client exposes it. If no Bricks skills are loaded, say that the Bricks skills are not loaded. Do not call site abilities for this check.
```

Désormais, votre IA dans OpenCode est connectée à WordPress/Bricks et peut y faire des opérations.

## 3) Connexion de l'IA à Figma

On utilise pour connecter notre IA à Figma l'outil [Figma Console MCP](https://github.com/southleft/figma-console-mcp). C'est un utiliataire gratuit et open source. Certains utilisateurs le considèrent comme meilleur et plus complet que la solution MCP officielle de Figma!

- Consulter la documentation de [Figma Console MCP](https://github.com/southleft/figma-console-mcp).
- Créer un token personnel dans l'interface de Figma, notez-le bien.
- Donner l'information à votre agent IA.

Il faut donner cette info à l'agent IA (en remplaçant le CODE_SECRET par votre token):

```
I want to connect to Figma using https://github.com/southleft/figma-console-mcp

Here is the code I would give you if you were Claude Code:

claude mcp add figma-console -s user -e FIGMA_ACCESS_TOKEN=CODE_SECRET -e ENABLE_MCP_APPS=true -- npx -y figma-console-mcp@latest
```

Suite à cela, l'IA fait des configurations pour se connecter à Figma. L'IA va produire un fichier `manifest.json` nécessaire pour la connexion, p.ex. ainsi: 

```
The Desktop Bridge plugin was installed at: /Users/username/.figma-console-mcp/plugin/manifest.json
```

Dernière opération que vous devez faire: installer le fichier `manifest.json` qui est un plugin Figma. 

- Dans l'application Figma desktop: en ayant un fichier Figma ouvert aller dans le menu : *Plugins* > *Développement* > *Plugin d'importation à partir d'un manifeste*. 
- Sélectionner le fichier `manifest.json`.

Cela fait exécuter un plugin nommé "Figma Desktop Bridge". Par la suite, si vous rouvrez le fichier, vous pouvez relancer le plugin sous 

Désormais: 

- L'IA peut détecter les frames que vous sélectionnez dans ce document Figma.
- L'IA peut construire dans Bricks.
- On peut lui demander de faire toutes sortes d'opérations (aussi ACF, création de contenus...)

### Bug rencontré

Lors de la création d'une page par l'IA selon un modèle Figma, l'IA a importé une fonte, mais celle ci ne s'affichait pas. Le problème, révélé par l'inspecteur, était la forme de la déclaration CSS.

Message de correction donné à l'IA:

```
The way the font has been declared in CSS is a problem, it renders in the inspector as : 
"'Host Grotesk',sans-serif"
Which doesnt work because of the double quotes.
```

---

### Sources d'infos

- https://www.youtube.com/watch?v=fEQ7SbcCVEA (
Figma to Bricks Builder...with AI Agents.)
- https://github.com/southleft/figma-console-mcp

