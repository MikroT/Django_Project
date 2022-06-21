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

Vedremo che è stata creata una cartella con il nome dell'app ed all'interno troveremo un file models.py dove inseriremo i nostri modelli.

Dopo l'inserimento dei modelli nella nostra app, se avviamo il Django server, noteremo che Django non avvierà la nuova app, questo perchò dovremo andare all'interno del file **settings.py** presente nella cartella del progetto ed inserire la nuova app nella lista **INSTALLED_APPS**

la stringa dovrà essere inserita **ALL'INIZIO** della lista e definita come: **'myapp.apps.MyappConfig'**

**QUESTO INSERIMENTO DEVE ESSERE FATTO OGNI VOLTA CHE VIENE CREATA UN'APP**

Dopo aver inserito la nuova app, l'applicazione fa parte di Django, che tuttavia ancora non conosce il fatto di voler aggiornare il database con delle nuove caratteristiche. Per farlo dobbiamo lanciare la migrazione che dipende da che cosa è stato inserito nel file **models.py** presente nella cartella del progetto.

Per chiedere a Django di preparare la migrazione a partire da un nuovo file eseguire i comandi:

**python manage.py makemigrations**

**python manage.py migrate**

Noteremo che Django applicherà la migrazione, creerà dei nuovi file ed aggiornerò il DB.

Riepilogo:

* Creare Progetto Django
* Creare App Django
* Dentro App in Django c'è un file models
* Il file models.py rappresenta la chiave dei modelli dati dove creare le tabelle dati

L'ultimo passaggio da fare è abilitare l'interfaccia WEB in Django; l'applicazione 'admin' gia presente sarà responsabile di questo.

Per abilitarla dobbiamo:
1. Creare un utente
2. Indicare a Django che vogliamo visualizzare la nostra applicazione

    1. Creare un utente amministratore con il comando **python manage.py createsuperuser**
    * Indicare i dati richiesti come e-mail e password 
    * Accedre alla console amministrazione aggiungendo /admin alla fine dell'url dopo aver eseguito il comando per far partire il django server

    2. Per rendere la nostra applicazione modificabile dall'interfaccia admin di Django editare il file *admin.py* presente nella cartella dell'applicazione ed aggiungere le stringhe necessarie per esempio (Question è il nome di un modello di esempio)
    * **from .models import Question**
    * **admin.site.register(Question)**