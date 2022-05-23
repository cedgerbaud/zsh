# Installer zsh et le plugin docker

Ce tuto a pour but d'expliquer la démarche à suivre pour installer zsh avec le plugin Docker. Zsh est un interpréteur de commandes (shell), tout comme bash. Il fournit cependant de nombreuses fonctionnalités supplémentaires grace à la possibilité d'installer divers thèmes et plugins, dont un plugin docker.

Pour installer ce(s) plugin(s), nous utiliserons [Oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) qui est un gestionnaire de plugins pour zsh.

![zsh-docker](/home/cedric/Videos/zsh-docker.gif)

## Etape #1 - Installer zsh

#### Ubuntu, Debian et dérivés (Windows 10 WSL)

```bash
apt install zsh
```

Si non disponible avec `apt`, essayer avec `apt-get` ou `aptitude`.

#### Centos/RHEL

```bash
sudo yum update && sudo yum -y install zsh
```

#### macOS

```bash
brew install zsh
```



Une fois le paquet installé, verifier l'installation avec `zsh --version`. Le résultat doit etre `zsh 5.0.8` ou plus récent.

Pour passer zsh en shell par défaut, utiliser la commande suivante

```bash
chsh -s $(which zsh)
```

*Pour plus de détails sur l'installation de zsh -> cliquer [ici](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)*.



## Etape #2 - Installer oh-my-zsh

#### Prérequis

- `zsh` doit etre installé
- `curl` ou `wget` doit etre installé
- `git` doit etre installé

#### Installation

Pour installer oh-my-zsh, il suffit d'executer l'une des commandes suivantes, en fonction de la méthode souhaitée. 

| **Méthode** | **Commande**                                                 |
| ----------- | ------------------------------------------------------------ |
| **curl**    | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
| **wget**    | `sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
| **fetch**   | `sh -c "$(fetch -o - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |



## Etape #3 - Installer le plugin docker

#### Installation de plugins

Pour installer les plugins avec oh-my-zsh, tout se passe dans le fichier `.zshrc`, équivalent du `.bashrc` qui doit se trouver dans le dossier `$HOME` de l'utilisateur (`~/`).

Il faut donc ouvrir ce fichier avec un editeur (vi, nano, notepad++, vscode...), et modifier la variable plugins pour y ajouter les plugins souhaités.

Par exemple: 

```
plugins=(
  git
  bundler
  dotenv
  macos
  rake
  rbenv
  ruby
)
```

La liste des plugins installés par défaut avec oh-my-zsh se trouve [ici](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins). Chaque plugin possède un readme détaillant son utilisation et les installations à effectuer si nécessaire.

#### Installation du plugin docker

Pour installer le plugin [docker](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/docker), il suffit donc de l'ajouter à la liste. En plus de l'autocomplétion, le plugin fournit une série d'alias facilitant les commandes docker. La liste complète de ces alias se trouve dans la doc du plugin (lien ci-dessus).

#### Quelques plugins utiles

- [aliases](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/aliases) qui fournit une liste complète d'alias pour tout un tas de commandes
- [colored-man-pages](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/colored-man-pages) ajoute une coloration syntaxique qui facilite la lecture des manuels sous linux
- [copyfile](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/copyfile) et [copypath](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/copypath) qui permettent de facilement copier le nom d'un fichier ou son chemin
- [dotenv](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/dotenv) va charger automatiquement les variables d'environnement qui se trouvent dans le fichier `.env` d'un dossier quand on y accède avec un `cd`
- [kubectl](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/kubectl) et [minikube](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/minikube) qui sont les équivalents du plugin docker pour kubernetes
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) ajoute la coloration syntaxique directement dans le terminal quand on écrit une commande (très pratique !). Nécessite une installation préalable avec la commande suivante: `git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting`
- Et bien d'autres [ici](https://travis.media/top-10-oh-my-zsh-plugins-for-productive-developers/) ou [là](https://safjan.com/top-popular-zsh-plugins-on-github/) 



## Etape Bonus - Installer un nouveau thème

Un des gros avantages de zsh en plus de ses plugins, c'est la possibilité de personnaliser l'interface du shell en y ajoutant des informations parfois très utiles, comme par exemple la branche sur laquelle on se trouve lorsque l'on se trouve dans un dossier qui comporte un repo git.

Par exemple :

![image-20220523230921080](/home/cedric/snap/typora/57/.config/Typora/typora-user-images/image-20220523230921080.png)



Pour installer un thème, là encore, il va falloir éditer le fichier `.zshrc`., et venir modifier la variable `ZSH_THEME` avec le nom du thème sélectionné.

Par exemple :

```
ZSH_THEME="robbyrussel"
```

```
ZSH_THEME="agnoster"
```

La liste des thèmes installés avec oh-my-zsh se trouve [ici](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes).

Si vous souhaitez un thème très complet et ultra comfigurable, je vous recommande [powerlevel10k](https://github.com/romkatv/powerlevel10k) (screenshot ci-dessus). Il nécessite cependant une installation un peu plus poussée avec des polices particulières ([nerd fonts](https://www.nerdfonts.com/)), mais la doc est très bien faite, rendant l'installation assez simple, et sa config se fait très facilement aussi avec un programme en cli (`p10k configure`). 



