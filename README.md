# octo-impaginator

Impaginatore per il sistema di stampa dei laboratori del Dipartimento di Matematica.

Il sistema di stampa presente nei laboratori del Dipartimento di Matematica dell'Università degli Studi di Padova stampa *male* quando si scelgie di stampare più di una pagina per foglio.
In particolare la stampa sul retro del foglio viene fatta ruotata di 180° e quindi, quando viene stampato un documento di varie pagine, è necessario rilegare le stampe in modo che queste vengano sfogliate lungo il lato lungo del foglio, il che è molto scomodo.

Graficamente:

```
  ===================== <-- rilegatura
  |         |         |
  |  pag.1  |  pag.2  |
  |         |         |
  ---------------------

  ---------------------
  |         |         |
  |  pag.3  |  pag.4  |
  |         |         |
  ===================== <-- rilegatura
  |         |         |
  |  pag.5  |  pag.6  |
  |         |         |
  ---------------------
```

Questo problema si verifica solo se viene impostata la stampa di più pagine del documento sullo stesso lato del foglio.
Quindi un modo per raggirarlo è quello di pre-elaborare il PDF in modo che abbia già due pagine sullo stesso lato del foglio.

Qui entra in gioco `impaginator.py` che effettua la preelaborazione in modo automatico.

Il PDF generato risulta quindi pronto per essere mandano in stampa con le impostazioni di default (una pagina per foglio).

Le stampe ottenute potranno quindi essere rilegate normalmente:

```
  rilegatura
  ⌄
  |---------------------
  ||         |         |
  ||  pag.1  |  pag.2  |
  ||         |         |
  |---------------------

                  rilegatura
                       ⌄
  ---------------------|---------------------
  |         |         |||         |         |
  |  pag.3  |  pag.4  |||  pag.5  |  pag.6  |
  |         |         |||         |         |
  ---------------------|---------------------

```


## Utilizzo

```
$ python impaginator.py -i <percorsoPDFInput> -o <percorsoPDFOutput>
```

Richiede `PyPDF2`: https://github.com/mstamy2/PyPDF2
