# 🎬 Il successo nell'audiovisivo 2000-2025: gradimento del pubblico e premi

Progetto Capstone – Master Data Analyst, Epicode · **Francesco Autorino**

Strumenti: 🐍 **Python** per raccolta, pulizia, collegamento e analisi dei dati · 📊 **Power BI** per la dashboard interattiva
· 📗 **Excel** solo per leggere in una tabella ordinata il campione di collegamenti controllato a mano.

| File | Contenuto |
|---|---|
| `CapstoneAutorinoPython.ipynb` | Notebook Python: preparazione dei dati, collegamento dei premi, analisi e tabelle per Power BI |
| `CapstoneAutorinoPowerBi.pbix` | Dashboard Power BI con 7 pagine, già completa dei dati |
| `CapstoneAutorinoPowerBiPDF.pdf` | Le 7 pagine della dashboard esportate in PDF |
| `CSVCreati/controllo_collegamenti.csv` | Il campione di 62 collegamenti che ho controllato a mano: è il file che legge il notebook |
| `CapstoneAutorinoExcel.xlsx` | Lo stesso campione in una tabella Excel più leggibile |
| `VideoProgettoCapstoneDAFrancescoAutorino.mp4` | Il video di presentazione del progetto (pitch di circa 3 minuti) |

---

## 🎯 Di cosa parla il progetto

Sono molto appassionato di film e serie TV: tutto quello che guardo lo segno in un'app e gli do il mio voto
personale. Da qui è nata la domanda del progetto: **il rating del pubblico e i premi ci dicono davvero se un film è
migliore di un altro?**
Il progetto prova a rispondere guardando film, serie TV e miniserie usciti tra il 2000 e il 2025 da due punti di vista:

- il **pubblico**: il voto medio e il numero di voti su IMDb;
- la **critica**: le candidature e le vittorie a Oscar, Golden Globe ed Emmy.

"Critica" è una semplificazione: gli Oscar li assegnano i professionisti del cinema dell'Academy, i Golden Globe i
giornalisti, gli Emmy la Television Academy. Sono quindi giurie di settore e di stampa, non critici in senso stretto.

Accanto ai titoli c'è il **cast**: attori, attrici e registi, i premi che hanno ricevuto e chi lavora sia nel cinema
sia in TV. Per le serie c'è anche un approfondimento su come cambia il gradimento da una stagione all'altra.

## ❓ Le domande

1. Come si distribuiscono gradimento, voti e generi di film, serie e miniserie, e quanti titoli ricevono candidature?
2. Pubblico e critica vanno d'accordo? I titoli candidati sono anche i più graditi dagli spettatori? Miniserie e
   serie TV si comportano in modo diverso?
3. Per le serie TV: come cambia il gradimento stagione dopo stagione? L'ultima stagione è davvero gradita meno
   delle precedenti?

## 🗂️ Da dove vengono i dati

| Dati | Fonte |
|---|---|
| Film, serie, miniserie ed episodi, con voti, cast e registi | [IMDb Non-Commercial Datasets](https://developer.imdb.com/non-commercial-datasets/) |
| Popolarità, lingua, paesi, case di produzione e budget dei film | [TMDB su Kaggle (aggiornato al 2025)](https://www.kaggle.com/datasets/asaniczka/tmdb-movies-dataset-2023-930k-movies) |
| Premi Oscar | [The Oscar Award](https://www.kaggle.com/datasets/unanimad/the-oscar-award) |
| Premi Golden Globe | [Golden Globe Awards](https://www.kaggle.com/datasets/unanimad/golden-globe-awards), completato con le edizioni 2021-2025 da Wikipedia ([78ª](https://en.wikipedia.org/wiki/78th_Golden_Globe_Awards), [79ª](https://en.wikipedia.org/wiki/79th_Golden_Globe_Awards), [80ª](https://en.wikipedia.org/wiki/80th_Golden_Globe_Awards), [81ª](https://en.wikipedia.org/wiki/81st_Golden_Globe_Awards), [82ª](https://en.wikipedia.org/wiki/82nd_Golden_Globe_Awards)) |
| Premi Emmy | [TidyTuesday](https://github.com/rfordatascience/tidytuesday/blob/main/data/2021/2021-09-21) e [Emmy Awards](https://www.kaggle.com/datasets/unanimad/emmy-awards), completati da Wikipedia con le edizioni 2022-2025 per le serie e 2020-2025 per le persone ([72ª](https://en.wikipedia.org/wiki/72nd_Primetime_Emmy_Awards), [73ª](https://en.wikipedia.org/wiki/73rd_Primetime_Emmy_Awards), [74ª](https://en.wikipedia.org/wiki/74th_Primetime_Emmy_Awards), [75ª](https://en.wikipedia.org/wiki/75th_Primetime_Emmy_Awards), [76ª](https://en.wikipedia.org/wiki/76th_Primetime_Emmy_Awards), [77ª](https://en.wikipedia.org/wiki/77th_Primetime_Emmy_Awards)) |

## 🔁 Come rieseguire il notebook

1. Prepara l'ambiente con **Anaconda**: io ho sviluppato il progetto con Anaconda e Python 3.13. Basta l'ambiente
   `base`, che ha già tutte le librerie tranne `rapidfuzz`. Per installarla, da Anaconda Prompt (Windows) o dal
   Terminale (macOS): `conda install -c conda-forge rapidfuzz`.

   In ogni caso nella prima cella del notebook controllo le librerie (pandas, numpy, matplotlib, seaborn, scipy,
   statsmodels, rapidfuzz) e installo con `conda` quelle che mancano. Chi non usa Anaconda può installarle con
   `python -m pip install pandas numpy matplotlib seaborn scipy statsmodels rapidfuzz`.
2. Scarica i dati dalle fonti qui sopra (circa 9 GB, per questo non sono nel repository), rinominali come nella
   tabella sotto e mettili nella cartella `DataSetProgettoCapStone/Grezzi/`, allo stesso livello della cartella
   che contiene il notebook.
3. Esegui il notebook dall'inizio alla fine. Le tabelle pulite finiscono in `CSVCreati/`, quelle per la dashboard
   in `powerbi/`.
4. Alla prima esecuzione la sezione 3.5 crea `CSVCreati/controllo_collegamenti.csv`, il campione di collegamenti da
   verificare a mano (50 con titolo identico e tutti i 12 con titolo solo simile). Compilato il file, rieseguendo la
   cella si ottiene la precisione stimata dei collegamenti. Se il file esiste già non viene riscritto: nel repository
   c'è già quello con il mio controllo, quindi il notebook calcola subito la precisione.
5. In Power BI imposta il parametro `CartellaDati` sul percorso della cartella `powerbi/` e aggiorna i dati.

**Nomi dei file grezzi**

| Nome usato nel notebook | File originale |
|---|---|
| `title.basics.tsv` | IMDb `title.basics.tsv` |
| `IMDb - Voti e rating.tsv` | IMDb `title.ratings.tsv` |
| `IMDb - Elenco episodi.tsv` | IMDb `title.episode.tsv` |
| `IMDb - Nomi delle persone.tsv` | IMDb `name.basics.tsv` |
| `IMDb - Registi e sceneggiatori.tsv` | IMDb `title.crew.tsv` |
| `IMDb - Cast principale.tsv` | IMDb `title.principals.tsv` |
| `TMDB - Film aggiornati al 2025.csv` | Kaggle TMDB `TMDB_movie_dataset_v11.csv` |
| `Premi Oscar 1927-2025.csv` | Kaggle `the_oscar_award.csv` |
| `Golden Globe 1944-2025.csv` | Kaggle `golden_globe_awards.csv` + righe 2021-2025 da Wikipedia |
| `Emmy 1949-2025, per serie TV.csv` | TidyTuesday `nominees.csv` + righe 2022-2025 da Wikipedia |
| `Emmy 1949-2019, con nome attore o regista.csv` | Kaggle `the_emmy_awards.csv` |
| `Emmy 2020-2025, con nome attore o regista (da Wikipedia).csv` | costruito dalle pagine Wikipedia delle edizioni 72-77 |

Le righe aggiunte da Wikipedia hanno le stesse colonne del file a cui sono state aggiunte, così il notebook le legge
insieme alle altre:

| File | Colonne usate |
|---|---|
| Golden Globe | `year_film`, `year_award`, `category`, `nominee`, `film`, `win` |
| Emmy per serie | `year`, `category`, `title`, `type` (Winner / Nominee) |
| Emmy per persona, 2020-2025 | `year`, `category`, `person`, `show`, `win` |

## ⚙️ Come ho lavorato i dati

1. **Selezione del catalogo.** Ho tenuto film, serie TV e miniserie usciti dal 2000 al 2025 con almeno 1.000 voti
   su IMDb, per concentrarmi su titoli con un pubblico reale. Per le serie ho raccolto tutti gli episodi e li ho
   raggruppati in stagioni.
2. **Arricchimento.** Ai film ho aggiunto i dati di TMDB: popolarità, lingua, paesi, casa di produzione e budget.
3. **Collegamento dei premi.** Le fonti dei premi e IMDb non hanno un codice in comune, quindi ho collegato le
   candidature ai titoli confrontando **titolo e anno** con il fuzzy matching. Ho controllato a mano sui siti ufficiali
   i collegamenti più incerti, e dagli errori trovati ho ricavato delle regole: titoli omonimi, titoli scritti in modo
   diverso, film per la TV. Nel periodo è collegato il 76% delle candidature; le altre riguardano soprattutto opere
   fuori dal catalogo.
4. **Controllo a campione.** Per misurare quanti collegamenti sono giusti ho verificato a mano 62 collegamenti: 50
   estratti a caso tra quelli con titolo identico e tutti i 12 con titolo solo simile, i più a rischio. Non è emerso
   nessun errore: la precisione stimata è del 100%, con un limite inferiore prudente del 93% (intervallo di Wilson,
   pesato per la dimensione dei due gruppi). Il problema dei premi quindi è quanti collegamenti mancano, non quanti
   sono sbagliati.
   Il campione con il mio controllo è in `CSVCreati/controllo_collegamenti.csv`. Il CSV però era difficile da leggere,
   perché Excel lo apre con tutto il testo in una sola colonna: per renderlo più leggibile l'ho riportato in Excel
   (`CapstoneAutorinoExcel.xlsx`) diviso in una tabella ordinata: una colonna per ogni informazione, intestazioni chiare e il link alla scheda IMDb di ogni titolo.
   Excel l'ho usato solo per questo, come supporto alla lettura: la pulizia dei dati e le analisi le ho fatte tutte in
   Python, la dashboard in Power BI, e il notebook legge il file CSV, non quello Excel.
5. **Cast e premi delle persone.** Per ogni titolo ho preso i cinque interpreti principali e i registi. Collego un premio
   a una persona cercandola solo nel cast del titolo premiato, per non confondere persone con lo stesso nome.
6. **Premi e gradimento.** Confronto i titoli con e senza candidature prima nel complesso, poi tra titoli con un numero
   di voti simile (per decili) e infine con una regressione lineare che tiene conto di anno, genere e voti.
7. **Analisi delle serie.** Ogni stagione è confrontata con la media della propria serie, così serie lunghe e corte
   diventano confrontabili. L'ultima stagione è confrontata con le precedenti con il t-test e il test di Wilcoxon,
   guardando anche quanto è grande la differenza (Cohen's d).
8. **Tabelle per la dashboard.** Nell'ultima parte del notebook preparo le 8 tabelle lette da Power BI. Le preparo in
   Python e non in Power Query perché con oltre 600 mila episodi Power Query era troppo lento.
9. **Dashboard.** In Power BI le 8 tabelle formano un modello dati con al centro la tabella dei titoli. Le misure DAX
   riproducono i risultati del notebook.

**Perché non ci sono budget e incassi.** Il budget c'è solo per circa un film su quattro, quasi solo per le produzioni
più famose e sempre meno negli anni recenti. Un'analisi economica avrebbe raccontato solo una parte del cinema, quindi
l'ho esclusa.

## 📌 Cosa è emerso

- **Le serie piacciono più dei film.** Il voto mediano è 7,3 per le serie TV e 6,3 per i film. In parte dipende dalla
  soglia: una serie arriva a mille voti solo se si costruisce un pubblico fedele.
- **I premi sono rari.** Ha almeno una candidatura collegata circa il 4% dei film e l'8% di serie e miniserie.
- **Pubblico e critica vanno nella stessa direzione.** I titoli candidati hanno un voto più alto (film 7,3 contro 6,2;
  serie 7,7 contro 7,3) e molti più voti. Anche a parità di numero di voti per i film resta
  un vantaggio tra circa 0,3 punti (regressione che tiene conto di anno, genere e voti) e 0,9 (confronto per decili,
  che riguarda soprattutto i film più votati); per le serie scende a circa un decimo, perché gran parte del vantaggio
  va insieme alla visibilità.
  Il numero di voti però è anche una conseguenza della candidatura, quindi questo confronto è prudente. In ogni caso
  è un'associazione: non dimostra che il premio faccia salire il gradimento.
- **La popolarità non è il gradimento.** La popolarità di un film su TMDB non è legata al suo voto medio.
- **Miniserie e serie TV** hanno un gradimento molto simile.
- **Cast e registi.** Considerando solo i titoli con almeno 100.000 voti, tra i registi più apprezzati ci sono
  Christopher Nolan (rating mediano 8,4), Denis Villeneuve e Quentin Tarantino. Tra gli interpreti più premiati ci
  sono Kate Winslet (8 vittorie) e Meryl Streep (25 candidature). Quasi 13.000 persone lavorano sia nel cinema sia in
  TV. La classifica per gradimento risente delle saghe: chi ha recitato in molti capitoli di una saga di successo
  sale in alto.
- **Le serie nel tempo.** Il gradimento è un po' più alto nelle prime stagioni e un po' più basso nelle ultime, ma
  la differenza è di pochi centesimi di punto. L'ultima stagione vale in media 0,036 punti meno delle precedenti, e la
  serie tipica non finisce peggio (mediana +0,007): la media scende per pochi crolli molto forti, come House of Cards
  (-4,27 punti) e Game of Thrones (-2,55).
- **Più una serie è lunga, più il finale cala.** Nella fase finale il calo è di 0,055 punti per le serie di 4-5
  stagioni, 0,079 per quelle di 6-8 e 0,151 per quelle di 9 o più. Con almeno 4 stagioni l'ultima stagione vale 0,09
  punti meno delle precedenti: entrambi i test lo confermano, ma resta una differenza piccola.

## 📊 La dashboard Power BI

La dashboard ha 7 pagine, con un menu laterale per spostarsi e filtri comuni per anno di uscita, genere e tipo di titolo.

| Pagina | Cosa mostra |
|---|---|
| **Dashboard generale** | I numeri del progetto (film, serie, miniserie, stagioni, episodi, candidature), i titoli per anno, la distribuzione del rating e i premi per fonte |
| **Film** | Rating e numero di voti di ogni film, rating per genere, lingue, andamento per anno e film più premiati |
| **Serie TV** | Le stesse analisi per serie TV e miniserie, con la distribuzione del rating dei due formati, lo stato delle serie e le serie più premiate |
| **Episodi** | Scelta una serie, il rating stagione per stagione ed episodio per episodio; per tutte le serie, l'andamento per fase e l'ultima stagione |
| **Cast e registi** | Interpreti e registi più apprezzati dal pubblico (sui titoli con almeno 100.000 voti) e più premiati |
| **Premi** | Rating e voti dei titoli con e senza candidature, candidature per anno, film e serie più premiati, tenuti separati perché una serie resta in gara ogni anno e un film una volta sola |
| **Conclusioni finali** | La risposta alle tre domande, con un grafico per ciascuna, i limiti e le fonti |

Il modello dati ha al centro la tabella dei **titoli** (film, serie e miniserie), collegata a stagioni, episodi,
generi, cast, registi e premi.

## ⚠️ Da tenere presente

- I voti IMDb riflettono chi sceglie di votare e sono aggiornati alla data di raccolta: i titoli più vecchi hanno
  avuto più tempo per accumularne.
- Le serie concluse e quelle cancellate non si possono distinguere.
- I premi conteggiati sono quelli collegati automaticamente: alcuni possono mancare, quindi i numeri sono un minimo.
- Dal 2022 le candidature Emmy per serie vengono da Wikipedia, che riporta meno categorie (circa 160 combinazioni
  l'anno contro circa 590 prima): il calo degli Emmy negli ultimi anni dipende dalla fonte, non è un trend.
- Il rating degli episodi c'è soprattutto per le serie più seguite.
- Tutti i risultati descrivono associazioni, non rapporti di causa ed effetto.
