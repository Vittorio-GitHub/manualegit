# Manuale Comandi Git

## git **init**

Primo comando per inizializzare un repository git in locale

```Bash
git init
```

### README

File di testo in formato MarkDown, utile per sintetizzare il contenuto del repository

> per creare il file

```Bash
touch README.md
```

### .gitignore

File in cui inserire tutte le cartelle e i file da escludere dall'indice Git (ad esempio file di log o temporanei)

> per creare il file

```Bash
touch .gitignore
```

---

## git **status**

Mostra lo stato del repository, indicando ad esempio file non ancora nell'indice, file modificati, file in attesa di commit, file aggiornati in remoto etc.

```Bash
git status
```

## git **add**

Comando per aggiungere file all'indice git per poter effettuare il commit in modo da includerli in una "vesione" del repository

```Bash
git add nomefile
```

> Posso aggiiungere intere cartelle o tutti i file di uno stesso tipo oppure direttamente tutti i file modificati

```Bash
git add nomefile
git add nomecartella
git add *.txt
git add --all
```

## git **commit**

Comando per creare una nuova "versione" del repository con tutti i file aggiornati alle ultime modifiche aggiunte all'indice con il comando add.

Fondamentle è il commento del commit in modo da poter individuare facilmente il contenuto delle varie versioni ed eventualmente ripristinarne una più vecchia

```Bash
git commit -m "Titolo Commit"
```

## git **log**

Mostra tutta la storia del repository, con la sequenza temporale di tutti i commit avvenuti, indicando anche eventuali branch.

Indica con la voce "HEAD" il commit attivo in quel momento

```Bash
git log
```

> Per vedere tutti i branch esistenti

```Bash
git log --all
```

> Per una visione più sintetica

```Bash
git log --oneline
```

> per uscire: **q**

Il codice iniziale è l'ID del commit, da utilizzare in caso si voglia ripristinare quel commit, quindi quella versione del repository

---

## git **restore**

Comando inverso di **add** serve per eliminare dall'indice qualcosa che non si vuole più includere

```Bash
git restore --staged nomefile
```

## git **reset**

Comando per ripristinare il repository ad uno stato (commit) precedente

> L'indice del commit lo si può trovare con il comando **git log**

```Bash
git reset indicecommit
```

> In alternativa è possibile indicare di quanti "passi" si vuole tornare indietro sostituendo all'indice del commit il testo **HEAD** con tanti **^** quanto il numero di "passi" indietro

```Bash
git reset HEAD^
```

Inoltre abbiamo tre versioni del comando: SOFT, MIXED, HARD.

MIXED è quello predefinito (attivo se non aggiungo nulla), crea un nuovo commit con la versione che vogliamo ed elimina i file aggiunti all'indice, ma non le modifiche fatte ai file

```Bash
git reset  HEAD^
```

SOFT è quella più leggere, crea un nuovo commit con la versione che vogliamo ma lascia tutti i file nell'indice (se facessimo di nuovo commit tutto torna come prima)

```Bash
git reset --soft HEAD^
```

HARD è quella forte, crea un nuovo commit con la versione che vogliamo ed elimina completamete, anche dalla cartella locale, i file non più in linea con quella versione ripristinata (o parte di essi)

```Bash
git reset -- hard HEAD^
```

---

## git **branch**

Comando usato per creare un nuovo ramo del repository, in modo da poter fare modifiche lasciando intatto il principale (main)

```Bash
git branch nomenuovobranch
```

> per eliminare un brach non più utilizzato

```Bash
git branch -d nomenuovobranch
```

## git **checkout**

Comando usato per spostarsi tra i branch di un repository, spostando il puntatore **HEAD**

```Bash
git checkout nomebranchdaaprire
```

## git **log** approfondimento

Utilizzando molti branch è comodo usare questo comando per vedere una sorta di grafico dei vari rami creati e delle relative versioni (commit)

```Bash
git log --all --oneline --decorate --graph
```

## git **merge**

Comando per unire due versioni diverse del repository, sia derivanti da un branch che eventualmente dal repository remoto

Bisogna essere nel branch che prenderà le modifiche fatte nel secondo branch (devo essere in quello che rimarrà vivo)

```Bash
git checkout nomebranchprincipale
git merge nomebranchsecondario
```

---

## git **clone**

Copia in locale di un repository remoto

```Bash
git clone https://LinkGitHub
```

## git **remote**

Lo uso quando invece ho creato un repository locale ma voglio aggiungergli un collegamento ad un repository remoto vuoto in modo che da questo momento in poi sia sincronizzato

Dopo aver creato il repository locale e aver eventualmente aggiunto dei file

Aggiungo l'origine remota

```Bash
git remote add origin https://https://LinkGitHub
```

> Invio tutte le modifiche al server remoto

```Bash
git push -u origin main
```

## git **fetch**

Serve per sincornizzare la directory locale con il server locale in modo da vedere eventuali modifiche presenti online e non ancora sincronizzate in locale

```Bash
git fetch
```

Posso poi vedere informazioni sullo stato del repository con **git status**

Per applicare le modifiche devo utilizzare il comando **git merge**

## git **pull**

Se uso questo comando faccio sia il **fetch** che il **merge** delle modifiche presenti in remoto. In pratica aggiornando la cartella locale all'ultima versione

```Bash
git pull
```

## git **push**

Serve ad inoltrare tutte le modifiche fatte in locale (tutto quello per cui è già stato fatto il **commit**) sul server remoto in modo da aggiornare il repository online

In altre parole applico al repository remoto l'ultimo commit effetuato sul repository locale

```Bash
git push
```

---
