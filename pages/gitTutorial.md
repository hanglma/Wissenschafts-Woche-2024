# Versionsverwaltung der Zukunft: Beispiele mit git

## 1. Installation und Einrichtung

### Installation der Programme

Als erstes muss _git_ natürlich installiert werden. Dafür müssen die Download-Files von https://git-scm.com/download/win heruntergeladen werden.
Der Link führt zum Download für die Windows Version von _git_, hier kann die neuste Version herunterladen.

Um nun _git_ zu installieren muss man die gerade heruntergeladene .exe Datei die ausführen. Nun wird dir ein Dialogfenster angezeigt, das Optionen zur Installation von _git_ enthält. Die Voreinstellungen passen so wie sie sind, d.h. es kann einfach durch geklickt werden.

Natürchlich braucht man auch einen Code-Editor. Im folgenden wird Visual Studio Code genutzt, jedoch is in diesem Tutorial leider keine Zeit für ein vollständiges Tutorial von VS-Code. Hier ist ein Video, dass trotzdem nützlich sein könnte 😉 https://www.youtube.com/watch?v=r5jNl-IOSZg

### Anmeldung bei gitHub oder gitLab

Um mit _git_ Repositories zu verwalten braucht man natürlich auch Repositories. Hierfür muss ein gitHub oder gitLab Account erstellt werden. Beide Websites funktionieren gut jedoch ist gitHub die größere Plattform was heißt, dass es dort mehr Projekt von Anderen zufinden gibt.

Für die Registrierung folge bitte diesem Link: https://github.com (Nutzerdaten merken!!!)

### Einrichtung Username & E-Mail

Um nun das _git_ des Computers mit gitHub zu verbinden muss die _.gitconfig-Datei_ bearbeitet werden. Dies geschiet mit dem Befehl _git config_.

```
# Befehl zum setzten des Nutzernamen
$ git config --global user.name hanspeter

# Befehl zum setzen der E-Mail
$ git config --global user.email hans@peter.de
```

Die ersten Schritte sind geschafft 😁 _git_ ist jetzt berteit für das erste Projekt. Aber wie und welche Befehle kannst man dabei gebrauchen kann, dass kommt im nächsten Abschnitt.

## 2. grundlegende Begriffe und Befehle + erstes Projekt

Um die Grundlegenden Begriffe und Befehle zu lernen kann man ein Projekt namens _first-contributions_. Hier wird einem beigebracht wie man mit Menschen aus der ganzen Welt zusammenarbeiten kannst.

Hier ein Link für dieses Projekt: https://github.com/firstcontributions/first-contributions/tree/main

### ein Repository _"forken"_

Als erstes muss man das Repository _"forken"_ damit Änderungen daran vorgenommen werden können. Hierzu muss auf den Knopf namens Fork geklickt werden.

![Picture of where to Fork](picture/forkPicture1.png)

Als nächstes auf Create Fork klicken. (alle anderen Einstellungen passen so wie sie sind) Dies sollte nun eine Kopie des Repositorys im persöhnlichen Account erstellen.

<img src="picture/forkPicture2.png" alt="picture of how to fork" width="400"/>

### das Projekt auf den eigenen Computer laden (_git clone_)

Jetzt wird das vorher _"geforkte"_ Repository auf den Computer _geklont_. Dazu öffnet man das Repository in seinem Account und klickt auf den Knopf "Code".

![picture of where to clone](picture/clonePicture1.png)

Nun öffnet sich ein Fenster mit einre URL, diese muss kopiert werden.

![picture of how to clone](picture/clonePicture2.png)

Um das Repositroy zu klonen gibt man jetzt den Befehl _git clone_ gefolgt von der gerade kopierten URL.

Dieser Befehl muss in _Commandline_ oder _Cmd_ eingegeben werden (Cmd öffnet sich in VS-Code mit Strg + Ö)

```
# git clone "URL für Repository"
$ git clone https://github.com/firstcontributions/first-contributions.git
```

### Erstellung eines Branch (_git switch -c_)

Bei der Verwendung von _git_ erstellt man für jedes neue Feature einen Branch, den man danach wieder in den Branch _main_ einbettet.

Um einen Branch zu erstellen wird der Befehl _git switch_ verwendet. Jedoch muss man sich dafür mit der _Commandline_ innerhalb des innerhalb des Repositorys befinden.

```
# cd "Ordner wohin man möchte"
$ cd first-contributions
```

Hans befindet sich im richtigen Ordner, da der Pfad den Namen seines Repositroys enthält.

```
C:\Users\hans\Dokumente\first-contributions>
```

Um einen Branch zu erstellen brauch man natürlich auch einen sinnvollen Namen. Dieser sollte das Feature beschreiben, dass man in diesem umsetzen will.

```
# git switch -c "Branchname"
$ git switch -c added_Hans_Peter
```

Das "-c" steht hierfür "create". Das heißt falls man zwischen mehreren Branches wechseln will, ohne einen neuen zu erstellen, lässt man "-c" einfach weg.

Um zu sehen in welchem Branch man sich befindet nutzt den Befehl _git branch_. Hierbei hat man auch die Optionen -r oder -a (-r => zeigt remote Repositories & -a => zeigt lokale und remote Repositories)

```
$ git branch
    * added_Hans_Peter
      master
```

Super! Jetzt darf man seinen Namen in die Datei Contributers.md schreiben 😎

### Änderungen speichern (_git status_, _git add_ & _git commit_)

Zum Speichern der Änderungen reicht _Strg + S_ leider nicht. Als erstes werden mit _git status_ die Änderungen ausgegeben.

```
$ git status
    Changes not staged for commit:
      (use "git add/rm <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
        modified: Contributors.md
```

Als nächstes muss man alle veränderten Datein mit _git add_ zum nächsten "commit" hinzufügen.

```
# git add "Dateiname"
$ git add Contributors.md
```

Zuletzt müssen diese Änderungen abgegeben/commited werden. Hierzu wird der Befehl _git commit_ verwendet. Jeder _commit_ sollte eine Commit-Message enthalten. Diese wird mit -m hinzugefügt und beschreibt was seit dem letzten commit geändert wurde.

```
# git commit -m "Commit-Message"
$ git commit -m "Add Hans to Contributors list"
```

<img src="picture/commitMessages.png" alt="picture of commit Messages" width="400"/>

### Änderungen hochladen/pushen (_git push_)

Alle Änderungen, die bis jetzt vorgenommen wurden, waren local. Um nun das Projekt online zu sichern muss es auf gitHub hochgeladen/gepusht werden. Dafür wird der Befehl _git push_ verwendet.

```
# git push origin "Branchname"
$ git push origin added_Hans_Peter
```

Origin steht beschreibt hier, dass der Branch zu einem Online-Repository gehört.

### Projekt in das Orginal-Projekt integrieren (_pull request_)

Jetzt, da alle Änderungen vorgenommen wurden kann man das Projekt wieder in das Orginalprojekt integrieren. Hierzu navigiert man auf gitHub wieder zu seinem Projekt und erstellt eine sogenannte _pull request_.

![where to pullRequest](picture/pullRepuest1.png)

Nun öffnet sich ein Fenster indem man den Namen seiner _pull request_ und einen Kommentar eingibt. Beides sollte definieren was mit dieser _pull request_ erreichent werden soll.

![comment for pullRequest](picture/pullRequest2.png)

Der Verwalter des Projekts muss nun die _pull request_ annehmen. Nachdem er den Fork annimmt wird der Text, den man vorhin eingetragen hat, in _Contributors.md_ angezeigt.

## 4. nützliches Wissen

### Wiederherstellung einer bestimmten Version des Projekts

Die Wiederherstellung einer füheren Version des Projekts kann ganz einfach mit der Erweiterung _gitLense für VS-Code_ erreichen.

Nach der Installation sollte ein neues Icon in der rechten Leiste erscheinen, welches nach ein neues Fenster in der rechten Spalte öffnet. Hier kann man den Reiter Commit-Graph wählen, welches wieder ein Fenster aufmacht in dem alle _Commits_ gezeigt werden. Nun wählt man lediglich den Commit zu dem man schauen möchte aus und klickt die drei Punkte. In diesem Fenster wählt man _Switch to Commit_ um mit dem _HEAD_ (der Stand der in VS-Code angezeigt wird) in diesn Commit zu wechseln.

<img src="picture/restorePicture1.png" alt="picture of commit Messages" width="600"/>

Um nun das Projekt auf diesen Stand zurück zusetzten, wählt man wieder die drei Punkte aber jetzt anstelle von _Switch to Commit_, _Rebase to Commit_ dies setzt den Branch _master_ auf den Stand dieses Commits.

<img src="picture/restorePicture2.png" alt="picture of commit Messages" width="600"/>

### Mergen von zwei Branchen mit einem diff-Tool

Um VS-Code als diff-Tool zu verwenden muss man die .gitconfig Datei bearbeiten.

```
# Befehl um .gitconfig aufzurufen
$ git config --global -e
```

In diese Datei müssen folgenden Zeilen Code hinzugefügt werden:

```
[diff]
  tool = vscode
[difftool "vscode"]
  cmd = code --wait --diff $LOCAL $REMOTE
[merge]
  tool = vscode
[mergetool "vscode"]
  cmd = code --wait $MERGED
```

Man kann jetzt zwei Branches _mergen_ in dem man mit _git switch_ zu dem Branch navigiert in den der andere Branch hinein gemerged werden soll. Als nächstes kann mit _Strg + Shift + P_ nach dem Command _"Git: Merge Branch"_ nun muss man lediglich den zweiten Branch auswählen.

Falls während dem Merge ein Widersprüche auftreten können dieses mit dem in VS-Code eingebautem _diff-Tool_ gelöst werden. In diesem Tool kann gewählt werden welche Version des Codes genommen werden soll.

### Integration in VS-Code

In VS-Code kann man auch ohne _Cmd_ Änderungen _adden, commiten und pushen_. Im Fenster _Source Control_ kann mit dem Plus-Symbol sozusagen der Befehl _git add_ ausgeführt werden. Mit dem Commit-Knopf können dann alle so hinzugefügten Änderungen _commited_ werden. Nachdem alles so gespeichert wured kann mit --- das Online-Repository auf den neusten Stand gebracht werden.

### nicht alles Hochladen -> .gitignore

Mit einer .gitignore Datei kann können bestimmte Datein bestimmt werden, die _git_ nicht tracken soll und somit auch nicht bei _Commits_ mitnehmen soll. Dies sind Dateien die nicht für die öffentlichkeit bestimmt sind und auch nicht auf gitHub landen sollten. Ein beispiel für solche Datein wären welche, die SSH-Keys, die für jede Person unteschielich sind, enthalten.

Ein Beispiel für eine .gitignore Datei wäre:

```
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

node_modules
dist
dist-ssr
*.local

# Editor directories and files
.vscode/*
!.vscode/extensions.json
.idea
.DS_Store
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?
```
