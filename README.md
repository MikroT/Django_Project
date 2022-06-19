Django Project
===
Preparazione VS Code:
* Installare le estensioni di '**python**' e '**remote container**'

Creazione della cartella locale del progetto

Dal terminale digitare il comando '**git init**'

Aprire la cartella in VS Code

Creare il file **README.md** file con estensione markdown

Creare il container di sviluppo .devcontainer:
* Premere il tasto verde in basso a sinistra ><
* Scegliere '**Add development container configuration file**'

    Verrà creata una cartella all' interno della cartella del progetto chiamata .devcontaier
    Dentro la cartella **.devcontainer** troverete un file *devcontainer.json* ed un file *Dockerfile*.

Aprire il container di sviluppo premendo il tasto verde in basso a sinistra >< e selezionare 'Reopen in container'

Creare un file **requirements.txt** per inserire le dipendenze da installare all'interno del container.

Per installare Django nella documentazione ufficiale troveremo il comando '**python -m pip install Django**' che serve per l'installazione locale.
Nel nostro caso dovremmo installarla nel container pertanto seguire i passaggi:
* Scrivere **Django** nel file *requirements.txt*
* nella console del devcontainer di python aperta precedentemente, digitare il comando '**pip install -r requirements.txt**'

Installato Django nel container dobbiamo importarlo in python
* Nel terminale digitare '**python**' per aprire una shell di python
* In python digitare '**import django**'
* Verificare l'installazione di django con il comando '**print(django.get_version())**'
* Uscire dalla shell di pytho ctrl-D

Verificare la versione '**python -m django --version**'

Creare la cartella del progetto Django '**django-admin startproject django_project**'

