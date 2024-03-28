# Exam Big Data
## Paul PONCET

## 5 - Mise en pratique (Examen)

1. **Trouvez combien de tags chaque film possède ?**

```bash
vi tags_par_film.py // Créer le fichier python

*** Copier le code qui est dans Exam-resultats/R5.1.md ***
:wq // Enregistrement du fichiers

sudo python tags_par_film.py -r hadoop --hadoop-streaming-jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar hdfs:///data/datasets/movies-2/tags.csv -o hdfs:///data/datasets/movies-2/tags_par_film
```


2. **Trouvez combien de tags chaque utilisateur a ajoutés ?**

```bash
vi tags_par_utilisateur.py // Créer le fichier python

*** Copier le code qui est dans Exam-resultats/question-5.2.md ***
:wq // Enregistrement du fichiers

sudo python tags_par_utilisateur.py -r hadoop --hadoop-streaming-jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar hdfs:///data/datasets/movies-2/tags.csv -o hdfs:///data/datasets/movies-2/tags_par_utilisateur
```

3. **Combien de blocs occupe le fichier dans HDFS dans chacune des configurations ?**

```bash
hdfs fsck / -files -blocks
```

Résultats :
```bash
Total blocks (validated):      1152 (avg. block size 2510786 B) (Total open file blocks (not validated): 1)
```

4. **Trouvez combien de fois chaque tag a été utilisé pour taguer un film ?**

Résultats :
<a href="Exam-resultats/R5-4.md" >click here</a>


