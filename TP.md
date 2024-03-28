# TP Big Data
## Paul PONCET

## 3. HDFS

### 3.1 - Prise en main Commandes HDFS

1. **hadoop fs : cette commande affiche la liste des commandes supportées par HDFS (Vous pouvez utiliser la commande hdfs dfs, les deux commandes sont équivalente).Quelle est la difference ?**

Après avoir testé les 2 commandes, on peut voir qu'il n'y a pas de différence entre les 2. La commande hadoop fs peut être utilisé dans la plus part des environnements Hadoop contreairement à hdfs dfs qui est spécifique à HDFS. Sinon, le rendu est le même.


2. **Pour connaitre la version de hadoop, la commande est : hadoop version (ou hdfs version). Quelle est la version hadoop de sandbox 2.6.5?**
La version de Hadoop trouvé pour cette question est la suivante :
- version d’hadoop : 2.7.3

3. **Toutes les commande ont le format : hdfs dfs -COMMANDE (resp. hadoop fs -COMMANDE).**

Dans HDFS, les commandes semblent toutes commencé de la même manière, avec un "-" devant le nom de la commande dans avec hdfs dfs ou haddop fs.

4. **Pour afficher de l’aide d’une commande donnée : hadoop fs -help COMMANDE**

hadoop fs -help COMMANDE nous permets d'avoir les détails de différentes commandes ainsi que des explications de ses dernières.

### 3.2 - Importer et exporter des données

1. **hdfs dfs -ls : liste l'ensemble des fichiers du répertoire utilisateur HDFS.Quel est le résultat obtenu? Commentez!**

Il n'y a pas encore de fichier dans le répertoire car nous n'en n'avons pas encore crée. Il est donc vide.

2. **hdfs dfs -ls / : affiche ce qu’il y a à la racine HDFS.Quel est la commande pour lire le contenue de /user?**

La commande est :

```bash
hdfs dfs -ls /user
```

Found 15 items
```bash                                                                                             
drwxr-xr-x   - admin     hdfs            0 2018-06-18 14:52 /user/admin
drwxrwx---   - ambari-qa hdfs            0 2018-06-18 14:52 /user/ambari-qa     
drwxr-xr-x   - amy_ds    hdfs            0 2018-06-18 14:53 /user/amy_ds   
drwxr-xr-x   - root      hdfs            0 2018-06-18 14:52 /user/anonymous        
drwxr-xr-x   - druid     hadoop          0 2018-06-18 16:06 /user/druid    
drwxr-xr-x   - hbase     hdfs            0 2018-06-18 15:08 /user/hbase     
drwxr-xr-x   - hcat      hdfs            0 2018-06-18 15:12 /user/hcat           
drwxr-xr-x   - hive      hdfs            0 2018-06-18 15:18 /user/hive      
drwxrwxr-x   - livy      hdfs            0 2018-06-18 15:11 /user/livy          
drwxr-xr-x   - maria_dev hdfs            0 2018-06-18 14:52 /user/maria_dev             
drwxrwxr-x   - oozie     hdfs            0 2018-06-18 16:08 /user/oozie               
drwxr-xr-x   - raj_ops   hdfs            0 2018-06-18 14:53 /user/raj_ops             
drwxr-xr-x   - root      hdfs            0 2018-06-18 14:52 /user/root     
drwxrwxr-x   - spark     hdfs            0 2018-06-18 15:10 /user/spark            
drwxr-xr-x   - zeppelin  hdfs            0 2018-06-18 15:10 /user/zeppelin     
```

La commande hdfs dfs -ls /user affiche le contenu du répertoire /user sur HDFS, avec les sous-répertoires.

3. **Que ce passe-il si vous refaite toute les commandes précedentes avec hadoop fs au lieux de hdfs dfs ?**

Le résultat obtenu reste sensiblement le même pour les 2 commandes.

4. **Créez localement un fichier texte monfichier.txt, modifiez son contenu, sauvegardez et quittez. Sachant que vous êtes en ligne de commande décrivez ce que vous avez fait.**

Pour commencer nous avons taper la ligne de commande suivante afin de créer le fichier texte ainsi que son contenu :

```bash
vi monfichier.txt
```

Par la suite, nous avons réalisé l'étape suivante afi d'enregistrer et de sortir du fuchier :

```bash
Ctrl+O et taper :wq pour enregistrer
```

5. **Copiez ce fichier sur HDFS par hdfs dfs -put monfichier.txt. Utilisez hdfs dfs -ls -R pour vérifier.**

```bash
hdfs dfs -put monfichier.txt
hdfs dfs -ls -R
```

Resultat :
```bash
-rw-r--r--   1 maria_dev hdfs          5 2024-03-26 15:03 monfichier.txt
```

6. **Une autre commande permet aussi d’envoyer une copie de vos données sur HDFS est : hdfs dfs -copyFromLocal monfichier.txt**

```bash
hdfs dfs -put monfichier.txt
```

7. **Si vous voulez envoyer vos données vers HDFS sans garder une copie en local : Quel est la commande a effectuer hdfs dfs -... monfichier.txt**

```bash
hdfs dfs -moveFromLocal monfichier.txt
```

Résultat : copy du fichier en local

### 3.3 - Manipulation des données dans HDFS

1. **Affichez le contenu du fichier créer mais sur HDFS. Completez la commande ci-dessous:**

```bash
hdfs dfs -cat monfichier.txt
```

Résultat : Le contenu du fichier

2. **Pour les fichiers longs, vous pouvez faire hdfs dfs -cat monfichier.txt | less ou hdfs dfs -cat bonjour.txt | more**

```bash
hdfs dfs -cat monfichier.txt | less 
hdfs dfs -cat monfichier.txt | more 
```
Le "less" montre le fichier dans son entiereté alors que le "more", nous a sorti que le texte présent dans le fichier.

3. **Supprimer un fichier depuis le système de fichiers HDFS : Completez la commande ci-dessous hadoop fs .. monfichier.txt**

```bash
hadoop fs -rm monfichier.txt
```

4. **Pour créer les répertoires du chemin 1 puis chemin2, … etc.**

```bash
hdfs dfs -mkdir CHEMIN1 CHEMIN2
```

5. **Créez localement un dossier nommé data et envoyez-le sur HDFS.**

```bash
mkdir data

hdfs dfs -put data/
```

Permet de voir les dossiers :
```bash
hdfs dfs -ls 
```


6. **Copiez le fichier monfichier.txt dans le répertoire data à l’aide de la commande -cp (vérifiez).**

```bash
hdfs dfs -cp monfichier.txt data/
```

Pour vérifier nous avons fait :
```bash
hdfs dfs -ls data/ 
```


7. **Créez un dossier datasets dans le dossier data, puis déplacez monfichier.txt dans datasets à l’aide de la commande -mv, décrivez vos commandes.**

Dans un premier temps nous avons réalisé la commande suivante afin de créer le dossier en indiquant le chemin dans lequel nous allons le placé, en l'occurence, ici le dossier data :

```bash
hdfs dfs -mkdir data/datasets/
```

Nous avons par la suite déplacé le fichier dans le nouveau dossier datasets :

```bash
hdfs dfs -mv monfichier.txt data/datasets/
```


7. **Créer une copie de monfichier.txt dans le répertoire data sous le nom copiedemonfichier.txt.**

```bash
hdfs dfs -cp data/datasets/monfichier.txt data/copiedemonfichier.txt
```

8. **Avant de lancer cette commande, il faut vérifier que l’espace local disponible est suffisant pour recevoir les données HDFS, décrivez vos commandes.**

```bash
df -h
```

9. **Si on veut supprimer un répertoire depuis le système de fichiers HDFS. Quelle est la commande à executer ?**

La commande à exécuter est :

```bash
hdfs dfs -rm -r chemin/vers/le/dossier/
```

10. **Une commande qui vous permet de voir « l’état de santé » de votre HDFS (elle vérifie les incohérences : blocks manquants, nom de réplicas insufusants,…) : hdfs fsck /user. Décrivez le résultat obtenu**

```bash
hdfs fsck /user -files -blocks
```
Le résultat est :
The filesystem under path '/user' is HEALTHY

Il semble donc que tout soit bon.

### 3.4 - Manipulation de fichiers télécharger depuis un serveur

1. **A partir de la VM, téléchargez les données disponibles sur le site :**
2. **Pour ce faire il vous faut la commande wget. Une erreur va apparaitre, décrivez comment vous avez pu faire pour télécharger le fichier.(Commentez la raison pour laqeulle l'erreur a lieu)**

```bash
wget https://files.grouplens.org/datasets/movielens/ml-1m.zip
```

wget sont utilisés pour télécharger des fichiers depuis internet

3. **Décompressez le fichier zip**

```bash
unzip ml-1m.zip
``` 
unzip est utilisé pour décompresser des fichiers.

4. **Créez un répértoire /datasets/movies en local et sur hdfs**
```bash
hdfs dfs -mkdir -p data/datasets/movies/
```

5. **Déroulez les étapes de création des deux dossier /datasets/movies et la copie du fichier rating.dat à partir du système local vers HDFS (dans movies).Affichez combien de blocs occupe le fichier avec la commande hdfs fsck [chemin vers votre fichier] -files -blocks (Commentez!)**

Nous avons du aller chercher le fichier ratings.data dans le dossier ml-m1 afin de pouvoir le copier dans le dossier movies créer lors de l'étape précédente, avec la première ligne de commande.

La deuxième ligne nous permets de connaître combien de blocs occupe le fichier.

```bash
hdfs dfs -put ml-m1/ratings.dat data/datasets/movies/
hdfs fsck data/datasets/movies/ratings.dat -files -blocks
```

La commande hdfs fsck [chemin] -files -blocks montre comment un fichier est divisé en blocs sur HDFS.

Résultat :
```bash
/user/maria_dev/data/datasets/movies/ratings.dat 24594131 bytes, 1 block(s):  OK
0. BP-243674277-172.17.0.2-1529333510191:blk_1073743061_2243 len=24594131 repl=1

Status: HEALTHY
 Total size:    24594131 B
 Total dirs:    0
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      1 (avg. block size 24594131 B)
 Minimally replicated blocks:   1 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    1
 Average block replication:     1.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          1
 Number of racks:               1
FSCK ended at Wed Mar 27 12:34:46 UTC 2024 in 15 milliseconds
```

Nous avons donc 1 block

6. **Pour voir la décomposition d’un fichier en plusieurs blocs, récupérez le fichier zip MovieLens 25M Dataset.Récuperez le fichiers qui se trouve:https://files.grouplens.org/datasets/movielens/ml-25m.zip**

```bash
wget https://files.grouplens.org/datasets/movielens/ml-25m.zip
```

7. **Décompressez-le puis copiez le fichier ratings.csv dans un autre répertoire dans HDFS et trouver le nombre de blocs occupé par ce dernier.**

```bash
unzip ml-25m.zip
hdfs dfs -put ml-25m/ratings.csv data/datasets/movies-2/
hdfs fsck data/datasets/movies-2/ratings.csv -files -blocks
```
La commande hdfs fsck [chemin] -files -blocks montre comment un fichier est divisé en blocs sur HDFS.

Résultat :
```bash
/user/maria_dev/data/datasets/movies-2/ratings.csv 678260987 bytes, 6 block(s):  OK
0. BP-243674277-172.17.0.2-1529333510191:blk_1073743062_2244 len=134217728 repl=1
1. BP-243674277-172.17.0.2-1529333510191:blk_1073743063_2245 len=134217728 repl=1
2. BP-243674277-172.17.0.2-1529333510191:blk_1073743064_2246 len=134217728 repl=1
3. BP-243674277-172.17.0.2-1529333510191:blk_1073743065_2247 len=134217728 repl=1
4. BP-243674277-172.17.0.2-1529333510191:blk_1073743066_2248 len=134217728 repl=1
5. BP-243674277-172.17.0.2-1529333510191:blk_1073743067_2249 len=7172347 repl=1

Status: HEALTHY
 Total size:    678260987 B
 Total dirs:    0
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      6 (avg. block size 113043497 B)
 Minimally replicated blocks:   6 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    1
 Average block replication:     1.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          1
 Number of racks:               1
```

Nous avons donc 6 blocks

### 3.5 - Fichiers de configuration HDFS

1. **Consultez le contenu de ce fichier. Quelle est la valeur du paramètre dfs.replication ? Ce dernier permet de préciser le nombre de réplication d'un block sur les noeuds d’un cluster. Justifiez !Vous pouvez afficher la valeur de réplication directement par la commande :hdfs getconf -confkey dfs.replication**

```bash
hdfs getconf -confkey dfs.replication
```

Le paramètre dfs.replication contrôle le nombre de réplicas d'un bloc dans HDFS.

Résultat :
```bash
1
```

2. **La taille du bloc : HDFS stocke les fichiers dans le cluster en les décomposant en blocs de taille fixe. Quelle est la taille du bloc sur votre HDFS ?**

HDFS stocke des fichiers en les décomposant en blocs de données, et la taille de ces blocs est spécifiée par le paramètre dfs.blocksize. La taille par défaut d'un bloc dans HDFS est généralement de 128 Mo (134217728 octets) pour les versions récentes d'Hadoop, bien que cela puisse varier en fonction de la configuration spécifique de votre cluster.

3. **On peut afficher la taille du bloc directement par une commande. Completez la commande ci-dessous: > hdfs getconf ....**

```bash
hdfs getconf -confKey dfs.blocksize
```

Le paramètre dfs.blocksize contrôle la taille des blocs dans HDFS.

Résultat :
```bash
134217728
```

4. **Vous pouvez changer la taille du bloc pour un fichier par la commande : hdfs dfs -D dfs.blocksize=67108864 -put Monfichier**

```bash
hdfs dfs -D dfs.blocksize=67108864 -put monfichier.txt
```

5. **Vérifiez en envoyant un fichier sur HDFS et commenter votre analyse. (hint: Je vous demande de faire les manipulations pour voir le nombres des blocs)**

```bash
hdfs fsck monfichier.txt -files -blocks
```

Résultat : 
```bash
/user/maria_dev/monfichier.txt 5 bytes, 1 block(s):  OK
0. BP-243674277-172.17.0.2-1529333510191:blk_1073743068_2250 len=5 repl=1

Status: HEALTHY
 Total size:    5 B
 Total dirs:    0
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      1 (avg. block size 5 B)
 Minimally replicated blocks:   1 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    1
 Average block replication:     1.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          1
 Number of racks:               1
```
On peut voir qu'il y a 1 block


## 4. Hadoop

### 4.1 - Préparation de la vm (MrJob, Python ...)

Nous allons avoir besoin de package comme Python, MrJob et Nano. Pour les installer nous allon utiliser yum et pip.


1. **Mise à jour de la SandBox HDP**

```bash
sudo yum-config-manager --save --setopt=HDP-SOLR-2.6-100.skip_if_unavailable=true
sudo yum install https://repo.ius.io/ius-release-el7.rpm https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

2. **Installation de python-pip**

```bash
sudo yum install python-pip
```

3. **Installation de MrJob**

```bash
sudo pip install pathlib
sudo pip install mrjob==0.7.4
sudo pip install PyYAML==5.4.1
```

4. **Installation de Nano**

```bash
sudo yum install nano
```

### 4.2 - Execution du MapReduce en local

Le script filmEvaluation.py est exécuté en local puis sur Hadoop pour analyser un fichier de données (evaluation.data). Les résultats montrent le nombre d'évaluations par note (de 1 à 5), démontrant la capacité de MapReduce à traiter et agréger de grandes quantités de données distribuées.

1. **Récuperation du code**

```bash
wget https://github.com/juba-agoun/iut-hadoop/raw/main/filmEvaluation.py
wget https://github.com/juba-agoun/iut-hadoop/raw/main/evaluation.data

sudo python filmEvaluation.py evaluation.data
```

### 4.3 - Execution du MapReduce en local

```bash
sudo python filmEvaluation.py -r hadoop --hadoop-streaming-jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-streaming.jar evaluation.data
```

Résultat
```bash
"1"     6111
"2"     11370
"3"     27145
"4"     34174
"5"     21203
```
