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

Per consultare il funzionamento dei file **.py** all'interno del django_project appena creato, andare al link [Django_tutorial01](https://docs.djangoproject.com/en/4.0/intro/tutorial01/)

Per far partire Django spostarsi nel terminale all'interno della cartella Django_project e lanciare il file manage.py col comado '**python manage.py runserver**'

Vedremo che in console sarà partito un webserver sulla porta 8000 in localhost accessibile all'indirizzo 'http://127.0.0.1:8000/'

Digitando il link sul browser se tutto va bene vedremo la pagina che indicherà il corretto avvio di Django.

Nel file **manage.py** inserire i modelli python necessari alla nostra applicazione

Dopo l'avvio del server Django vedremo un stringa come la seguente:
    
    Watching for file changes with StatReloader
    Performing system checks...
    System check identified no issues (0 silenced).
    You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
    Run 'python manage.py migrate' to apply them.
    June 21, 2022 - 18:42:57
    Django version 4.0.5, using settings 'django_project.settings'
    Starting development server at http://127.0.0.1:8000/
    Quit the server with CONTROL-C.

Django sta indicando che ci sono 18 migrazioni non applicate; le migrazioni un metodo usato da Django per modifiche al database dal python, e che Django ci lascia la possibilità di applicare a mano, evitando quindi un probabile errore in caso in cui le applicasse in maniera automatica.

Alla prima installazione Django ha delle app preinstallate che effettivamente hanno apportato modifiche al DB, e per questo Django ci chiede se vogliamo applicare le migrazioni
* Per applicare le modifiche dovremo eseguire il comado **python manage.py migrate**

**CREAZIONE APP IN DJANGO**

Per creare un'app in Django eseguire il comando **python manage.py startapp myapp** dove myapp è il nome dell'app che vogliamo creare all'interno di Django.

Vedremo che è stata creata una cartella con il nome dell'app ed all'interno troveremo un file models.py