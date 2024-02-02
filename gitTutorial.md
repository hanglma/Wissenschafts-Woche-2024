# Versionsverwaltung der Zukunft: Beispiele mit git

## 1. Installation und Einrichtung

### Installation der Programme

Als erstes muss _git_ installiert werden. Dafür müssen die Download-Files von https://git-scm.com/download/win heruntergeladen werden.
Dieser Link führt zum Download für die Windows Version von _git_.

Um nun _git_ zu installieren muss man die gerade heruntergeladene .exe Datei ausführen. Nun erscheint ein Dialogfenster, das Optionen zur Installation von _git_ enthält. Die Voreinstellungen passen so wie sie sind, d.h. es kann einfach durch geklickt werden.

Außerdem braucht man einen Code-Editor. Im folgenden wird Visual Studio Code genutzt. In diesem Tutorial ist leider keine Zeit für eine vollständige Einführung in VS-Code. Hier ist ein Video, das trotzdem nützlich sein könnte 😉 https://www.youtube.com/watch?v=r5jNl-IOSZg

### Anmeldung bei gitHub oder gitLab

Um mit _git_ Repositories/Projekte zu verwalten braucht man Repositories. Hierfür muss ein gitHub oder gitLab Account erstellt werden. Beide Websites funktionieren gut. GitHub ist jedoch die größere Plattform, deshalb gibt es dort mehr Projekt von Anderen.

Für die Registrierung bitte diesem Link folgen: https://github.com (Nutzerdaten merken!!!)

### Einrichtung Username & E-Mail

Um das _git_ des Computers mit gitHub zu verbinden, muss die _.gitconfig-Datei_ bearbeitet werden. Dies geschiet mit dem Befehl _git config_.

```
# Befehl zum setzten des Nutzernamen
$ git config --global user.name hanshuber

# Befehl zum setzen der E-Mail
$ git config --global user.email hans.huber@gmail.com
```

Die ersten Schritte sind geschafft 😁 _git_ ist jetzt berteit für das erste Projekt. Aber welche Befehle werden wie eingesetzt? Das kommt im folgenden Abschnitt.

## 2. Grundlegende Begriffe und Befehle + erstes Projekt

Um die Grundlegenden Begriffe und Befehle zu lernen, kann man an einem Projekt namens _first-contributions_ teilnehmen. Hier werden die Grundlagen vermittelt, die das Zusammenarbeiten von Programmierern aus der ganzen Welt ermöglichen.

Der Link für dieses Projekt lautet: https://github.com/firstcontributions/first-contributions/tree/main

### Repositories _"forken"_

Als erstes muss man das Repository _"forken"_, damit Änderungen daran vorgenommen werden können. Hierzu muss auf den Button namens Fork geklickt werden.

![Picture of where to Fork](/pages/picture/forkPicture1.png)

Als nächstes auf Create Fork klicken (alle anderen Einstellungen passen so wie sie sind). Dies sollte nun eine Kopie des Repositorys im persöhnlichen Account erstellen.

<img src="pages/picture/forkPicture2.png" alt="picture of how to fork" width="400"/>

### das Projekt auf den eigenen Computer laden (_git clone_)

Jetzt wird das vorher _"geforkte"_ Repository auf den Computer _geklont_. Dazu öffnet man das Repository in seinem Account und klickt auf den Button "Code".

![picture of where to clone](/pages/picture/clonePicture1.png)

Nun öffnet sich ein Fenster mit einer URL. Diese muss kopiert werden.

![picture of how to clone](/pages/picture/clonePicture2.png)

Um das Repositroy zu klonen gibt man jetzt den Befehl _git clone_ gefolgt von der gerade kopierten URL.

Dieser Befehl muss in _Commandline_ oder _Cmd_ eingegeben werden (Cmd öffnet sich in VS-Code mit Strg + Ö)

```
# git clone "URL für Repository"
$ git clone https://github.com/firstcontributions/first-contributions.git
```

### Erstellung eines Branch (_git switch -c_)

Bei der Verwendung von _git_ erstellt man für jedes neue Feature einen Branch, den man danach wieder in den Branch _main_ einbettet.

Um einen Branch zu erstellen wird der Befehl _git switch_ verwendet. Jedoch muss man sich dafür mit der _Commandline_ innerhalb des Repositorys befinden.

```
# cd "Ordner wohin man möchte"
$ cd first-contributions
```

Hans befindet sich im richtigen Ordner, da der Pfad den Namen seines Repositroys enthält.

```
C:\Users\hans\Dokumente\first-contributions>
```

Um einen Branch zu erstellen benötigt man einen sinnvollen Namen. Dieser sollte das Feature beschreiben, das man umsetzen will.

```
# git switch -c "Branchname"
$ git switch -c added_Hans_Peter
```

Das "-c" steht hierfür "create". Das heißt, falls man zwischen mehreren Branches wechseln will, ohne einen neuen zu erstellen, lässt man "-c" weg.

Um zu sehen in welchem Branch man sich befindet, nutzt man den Befehl _git branch_. Hierbei gibt es auch die Optionen -r oder -a (-r zeigt remote Repositories und -a zeigt lokale & remote Repositories)

```
$ git branch
    * added_Hans_Peter
      master
```

Super! Jetzt darf man seinen Namen in die Datei Contributers.md schreiben 😎

### Änderungen speichern (_git status_, _git add_ & _git commit_)

Zum Speichern der Änderungen reicht _Strg + S_ leider nicht.Man benötigt drei Schritte.

1. Die Änderungen müssen mit _git status_ ausgegeben werden.

```
$ git status
    Changes not staged for commit:
      (use "git add/rm <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
        modified: Contributors.md
```

2. Alle Datein, die gespeochert werden sollen, müssen mit _git add_ zum nächsten "commit" hinzugefügt werden.

```
# git add "Dateiname"
$ git add Contributors.md
```

3. Nun müssen diese Änderungen abgegeben/commited werden. Hierzu wird der Befehl _git commit_ verwendet. Jeder _commit_ muss eine Commit-Message enthalten. Diese wird mit -m hinzugefügt und beschreibt was seit dem letzten commit geändert wurde.

```
# git commit -m "Commit-Message"
$ git commit -m "Add Hans to Contributors list"
```

<img src="pages/picture/commitMessages.png" alt="picture of commit Messages" width="400"/>

### Änderungen hochladen/pushen (_git push_)

Alle Änderungen, die bis jetzt vorgenommen wurden, waren local. Um nun das Projekt online zu sichern muss es auf gitHub hochgeladen/gepusht werden. Dafür wird der Befehl _git push_ verwendet.

```
# git push origin "Branchname"
$ git push origin added_Hans_Peter
```

Origin beschreibt hier, dass der Branch zu einem Online-Repository gehört.

### Projekt in das Orginal-Projekt integrieren (_pull request_)

Jetzt, da alle Änderungen vorgenommen wurden, kann das Projekt wieder in das Orginal-Projekt integriert werden. Hierzu navigiert man auf gitHub zurück zu seinem Projekt und erstellt eine sogenannte _pull request_.

![where to pullRequest](/pages/picture/pullRepuest1.png)

Nun öffnet sich ein Fenster indem man den Namen seiner _pull request_ und einen Kommentar eingibt. Beides sollte definieren was mit dieser _pull request_ erreichent werden soll.

![comment for pullRequest](/pages/picture/pullRequest2.png)

Der Verwalter des Original-Projekts muss nun die _pull request_ annehmen. Nachdem er diese annimmt wird der Text, den man vorhin eingetragen hat, in _Contributors.md_ angezeigt.

Das erste Projekt ist nun geschafft 😊

## 3. nützliches Wissen

### Integration in VS-Code

In VS-Code kann man auch ohne _Cmd_ Änderungen _adden, commiten und pushen_. Im Fenster _Source Control_ wird mit dem Plus-Symbol sozusagen der Befehl _git add_ ausgeführt. Mit dem Commit-Button können dann alle so hinzugefügten Änderungen _commited_ werden. Nachdem alles so gespeichert wurde kann mit _Sync all Changes_ das Online-Repository auf den neusten Stand gebracht werden.

### Wiederherstellung einer bestimmten Version des Projekts

Die Wiederherstellung einer früheren Version des Projekts kann ganz einfach mit der Erweiterung _gitLense für VS-Code_ erreicht werden.

Nach der Installation sollte ein neues Icon in der rechten Leiste erscheinen, welches bei klick ein neues Fenster in der rechten Spalte öffnet. Hier kann man den Reiter Commit-Graph wählen, welches wieder ein Fenster aufmacht in dem alle _Commits_ gezeigt werden. Nun wählt man lediglich den Commit, den man betrachten möchte, aus und klickt auf die drei Punkte. In einem neu geöffneten Fenster wählt man _Switch to Commit_ um mit dem _HEAD_ (der Stand der in VS-Code angezeigt wird) in diesen Commit zu wechseln.

<img src="pages/picture/restorePicture1.png" alt="picture of gitlense" width="600"/>

Um nun das Projekt auf diesen Stand zurück zusetzten, wählt man wieder die drei Punkte, aber jetzt anstelle von _Switch to Commit_ _Rebase to Commit_. Dies setzt den aktuellen Branch auf den Stand dieses Commits.

<img src="pages/picture/restorePicture2.png" alt="picture of where to rebase" width="600"/>

### Mergen von zwei Branches mit einem diff-Tool

Um VS-Code als diff-Tool zu verwenden muss man die .gitconfig Datei bearbeiten.

```
# Befehl um .gitconfig aufzurufen
$ git config --global -e
```

Dazu müssen in diese Datei folgende Zeilen Code hinzugefügt werden:

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

Jetzt kann man zwei Branches _mergen_ in dem man mit _git switch_ zu dem Branch navigiert, in den der andere Branch hinein gemerged werden soll. Als nächstes kann mit _Strg + Shift + P_ nach dem Command _"Git: Merge Branch"_ suchen. Nun muss lediglich der zweite Branch ausgewählt werden..

Falls während einem Merge Widersprüche auftreten, können diese nun mit dem in VS-Code eingebauten _diff-Tool_ gelöst werden. Mit diesem Tool kann gewählt werden, welche Version des Codes verwendet werden soll.

### nicht alles Hochladen -> .gitignore

Mit einer .gitignore Datei können bestimmte Datein ausgewählt werden, die _git_ nicht tracken soll und somit auch nicht bei _Commits_ hochladen soll. Dies sind Dateien, die nicht für die Öffentlichkeit bestimmt sind und auch nicht auf gitHub landen sollten. Ein Beispiel für solche Datein wären Dateien, die SSH-Keys (sind für jede Person unteschiedlich) enthalten.

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
