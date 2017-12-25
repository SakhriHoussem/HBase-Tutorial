# HBase in Practice

## Learn How HBase Work in Simple Example

```shell
# HBase Shell startup
hbase shell
```

```shell
# get Hbase Shell commande list 
table_help
```

```shell
# show TABLES in HBase Shell
list
```

```shell
# if a TABLE exists in HBase
exists 'table_name'
```

```shell
# Hbase Shell shutdown
exit
```

### Create HBase TABLE Randonnee :  

```shell
# commande to create HBase TABLE with family columns  
CREATE 'table_name', 'family_column1','family_column2',....
```

```shell
# show HBase TABLE structure
DESCRIBE 'table_name'
```

      Randonnee(idRando, nomRando, region, distance , denivele, suiteRando)

#### devide 'Randonnee' TABLE on 2 family column :

      InfoRandonnee: nomRando, region et suiteRando
      InfoTechnique: distance et denivele

commande : 
```shell
# create table with 2 family columns
CREATE 'Randonnee', 'InfoRandonnee','InfoTechnique'
```
      
### Write in 'Randonnee' TABLE :

```shell
# write in TABLE 
put 'table_name', 'id', 'family_column:column', 'value'
```
We will to write this information in 'Randonnee' TABLE
      
      (1, 'Monts du Djurdjura', 'Tizi Ouzou', 35, 1000, NULL);
      (2, 'Circuit de Misserghin', 'Oran', 25 , 514, NULL);
      (3, 'Montagne de Murdjadju', 'Oran', 31, 1100, NULL);
      (4, 'Canastel', 'Oran', 18, 890, 3);
      (5, 'Yama Gouraya', 'Bejaia', 19, 900, NULL);
      (6, 'Sidi Makhlouf', 'Blida', 8, 165, 8);
      (7, 'Tikjda', 'Tizi Ouzou', 10, 1900, NULL);
      (8, 'Feroukha', 'Blida', 14.18, 454, NULL);
      (9, 'Chrea Azzazga', 'Tizi Ouzou', 6.23, 1548, 11);

commande : 

```shell
# (1, 'Monts du Djurdjura', 'Tizi Ouzou', 35, 1000, NULL);
put 'Randonnee', '1', 'InfoRandonnee:nomRando', 'Monts du Djurdjura'
put 'Randonnee', '1', 'InfoRandonnee:region', 'Tizi Ouzou'
put 'Randonnee', '1', 'InfoTechnique:distance', 35
put 'Randonnee', '1', 'InfoTechnique:denivele', 1000

# (2, 'Circuit de Misserghin', 'Oran', 25 , 514, NULL);
put 'Randonnee', '2', 'InfoRandonnee:nomRando', 'Circuit de Misserghin'
put 'Randonnee', '2', 'InfoRandonnee:region', 'Oran'
put 'Randonnee', '3', 'InfoTechnique:distance', 25
put 'Randonnee', '2', 'InfoTechnique:denivele', 514

# (3, 'Montagne de Murdjadju', 'Oran', 31, 1100, NULL);
put 'Randonnee', '3', 'InfoRandonnee:nomRando', 'Montagne de Murdjadju'
put 'Randonnee', '3', 'InfoRandonnee:region', 'Oran'
put 'Randonnee', '3', 'InfoTechnique:distance', 31
put 'Randonnee', '3', 'InfoTechnique:denivele', 1100

# (4, 'Canastel', 'Oran', 18, 890, 3);
put 'Randonnee', '4', 'InfoRandonnee:nomRando', 'Canastel'
put 'Randonnee', '4', 'InfoRandonnee:region', 'Oran'
put 'Randonnee', '4', 'InfoTechnique:distance', 18
put 'Randonnee', '4', 'InfoTechnique:denivele', 890
put 'Randonnee', '4', 'InfoRandonnee:suiteRando', 3

# (5, 'Yama Gouraya', 'Bejaia', 19, 900, NULL);
put 'Randonnee', '5', 'InfoRandonnee:nomRando', 'Yama Gouraya'
put 'Randonnee', '5', 'InfoRandonnee:region', 'Bejaia'
put 'Randonnee', '5', 'InfoTechnique:distance', 19
put 'Randonnee', '5', 'InfoTechnique:denivele', 900

# (6, 'Sidi Makhlouf', 'Blida', 8, 165, 8);
put 'Randonnee', '6', 'InfoRandonnee:nomRando', 'Sidi Makhlouf'
put 'Randonnee', '6', 'InfoRandonnee:region', 'Blida'
put 'Randonnee', '6', 'InfoTechnique:distance', 8
put 'Randonnee', '6', 'InfoTechnique:denivele', 165
put 'Randonnee', '6', 'InfoRandonnee:suiteRando', 8

# (7, 'Tikjda', 'Tizi Ouzou', 10, 1900, NULL);
put 'Randonnee', '7', 'InfoRandonnee:nomRando', 'Tikjda'
put 'Randonnee', '7', 'InfoRandonnee:region', 'Tizi Ouzou'
put 'Randonnee', '7', 'InfoTechnique:distance', 10
put 'Randonnee', '7', 'InfoTechnique:denivele', 1900

# (8, 'Feroukha', 'Blida', 14.18, 454, NULL);
put 'Randonnee', '8', 'InfoRandonnee:nomRando', 'Feroukha'
put 'Randonnee', '8', 'InfoRandonnee:region', 'Blida'
put 'Randonnee', '8', 'InfoTechnique:distance', 14.18
put 'Randonnee', '8', 'InfoTechnique:denivele', 454

# (9, 'Chrea Azzazga', 'Tizi Ouzou', 6.23, 1548, 11);
put 'Randonnee', '9', 'InfoRandonnee:nomRando', 'Chrea Azzazga'
put 'Randonnee', '9', 'InfoRandonnee:region', 'Tizi Ouzou'
put 'Randonnee', '9', 'InfoTechnique:distance', 6.23
put 'Randonnee', '9', 'InfoTechnique:denivele', 1548
put 'Randonnee', '9', 'InfoRandonnee:suiteRando', 11
 ```
### Update TABLE :

Update the distance of the first Randonnee (55 instead of 35)

```shell
put 'Randonnee', 1, 'InfoTechnique:distance', 55
```
### get From TABLE :

```shell
# for a single line
get 'table_name', 'id'
get 'table_name', 'id', 'family'
get 'table_name', 'id', 'family:colonne'
get 'table_name', 'id', {COLUMN=>'family'}
get 'table_name', 'id', {COLUMN=>'family:colonne'}
```
```shell
# for a several line
1- scan 'table_name'
2- scan 'table_name', {COLUMN=>['family']}
3- scan 'table_name', {COLUMN=>['family:colonne']}
```
get from TABLE Randonnee 4

```shell
get 'Randonnee', '4'
```
get InfoRandonnee of Randonnee 5.

```shell
get 'Randonnee', 5, 'InfoRandonnee'
```
### use FILTER : 
[Filters In Hbase Shell Tutorial](http://www.hadooptpoint.org/filters-in-hbase-shell/)

```shell
# for a single line
get 'table_name', 'id', {FILTER=>"filter"}
```
or :
```shell 
# for a several line
scan 'table_name', {FILTER=>"filter"}
```
show the list of filters available in HBase
```shell
show_filters
```


get the distance of the Randonnee 'Murdjadu Mountain'

```shell
scan 'Randonnee',{FILTER=>
	"SingleColumnValueFilter('InfoRandonnee', 'nomRando', =,'binary:Montagne de Murdjadju')
	AND ColumnPrefixFilter ('distance')
	"}
```
```shell
scan 'Randonnee',{FILTER=>
		"SingleColumnValueFilter('InfoRandonnee', 'nomRando', =,'binary:Montagne de Murdjadju')
		AND QualifierFilter(=,'binary:distance')
	"}
```

get the distance of the Randonnee in the region of 'Tizi Ouzou'.

```shell
scan 'Randonnee',{FILTER=>
		"SingleColumnValueFilter('InfoRandonnee', 'region', =,'binary:Tizi Ouzou')
		AND QualifierFilter(=,'binary:distance') 
	"}
```


