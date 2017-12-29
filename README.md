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

### Create HBase TABLE hiking :  
The syntax to create TABLE :
```shell
# commande to create HBase TABLE with family columns  
CREATE 'table_name', 'family_column1','family_column2',....
```

The syntax to descibe TABLE :
```shell
# show HBase TABLE structure
DESCRIBE 'table_name'
```
hiking Table Structure :

      hiking(id, name, region, distance , Altitude, suiteHiking)

#### Divide 'hiking' TABLE on 2 family column :

      InfoHiking: name, region et suiteHiking
      InfoTechnique: distance et Altitude

commande : 
```shell
# create table with 2 family columns
CREATE 'hiking', 'InfoHiking','InfoTechnique'
```
      
### Write in 'hiking' TABLE :
The syntax to write in TABLE :
```shell
# write in TABLE 
put 'table_name', 'id', 'family_column:column', 'value'
```
#### example : 

We will to write this informations in 'hiking' TABLE
      
      (1, 'Monts du Djurdjura', 'Tizi Ouzou', 35, 1000, NULL);
      (2, 'Circuit de Misserghin', 'Oran', 25 , 514, NULL);
      (3, 'Montagne de Murdjadju', 'Oran', 31, 1100, NULL);
      (4, 'Canastel', 'Oran', 18, 890, 3);
      (5, 'Yama Gouraya', 'Bejaia', 19, 900, NULL);
      (6, 'Sidi Makhlouf', 'Blida', 8, 165, 8);
      (7, 'Tikjda', 'Tizi Ouzou', 10, 1900, NULL);
      (8, 'Feroukha', 'Blida', 14.18, 454, NULL);
      (9, 'Chrea Azzazga', 'Tizi Ouzou', 6.23, 1548, 11);


```shell
# (1, 'Monts du Djurdjura', 'Tizi Ouzou', 35, 1000, NULL);
put 'hiking', '1', 'InfoHiking:name', 'Monts du Djurdjura'
put 'hiking', '1', 'InfoHiking:region', 'Tizi Ouzou'
put 'hiking', '1', 'InfoHiking:distance', 35
put 'hiking', '1', 'InfoHiking:Altitude', 1000

# (2, 'Circuit de Misserghin', 'Oran', 25 , 514, NULL);
put 'hiking', '2', 'InfoHiking:name', 'Circuit de Misserghin'
put 'hiking', '2', 'InfoHiking:region', 'Oran'
put 'hiking', '3', 'InfoTechnique:distance', 25
put 'hiking', '2', 'InfoTechnique:Altitude', 514

# (3, 'Montagne de Murdjadju', 'Oran', 31, 1100, NULL);
put 'hiking', '3', 'InfoHiking:name', 'Montagne de Murdjadju'
put 'hiking', '3', 'InfoHiking:region', 'Oran'
put 'hiking', '3', 'InfoTechnique:distance', 31
put 'hiking', '3', 'InfoTechnique:Altitude', 1100

# (4, 'Canastel', 'Oran', 18, 890, 3);
put 'hiking', '4', 'InfoHiking:name', 'Canastel'
put 'hiking', '4', 'InfoHiking:region', 'Oran'
put 'hiking', '4', 'InfoTechnique:distance', 18
put 'hiking', '4', 'InfoTechnique:Altitude', 890
put 'hiking', '4', 'InfoHiking:suiteHiking', 3

# (5, 'Yama Gouraya', 'Bejaia', 19, 900, NULL);
put 'hiking', '5', 'InfoHiking:name', 'Yama Gouraya'
put 'hiking', '5', 'InfoHiking:region', 'Bejaia'
put 'hiking', '5', 'InfoTechnique:distance', 19
put 'hiking', '5', 'InfoTechnique:Altitude', 900

# (6, 'Sidi Makhlouf', 'Blida', 8, 165, 8);
put 'hiking', '6', 'InfoHiking:name', 'Sidi Makhlouf'
put 'hiking', '6', 'InfoHiking:region', 'Blida'
put 'hiking', '6', 'InfoTechnique:distance', 8
put 'hiking', '6', 'InfoTechnique:Altitude', 165
put 'hiking', '6', 'InfoHiking:suiteHiking', 8

# (7, 'Tikjda', 'Tizi Ouzou', 10, 1900, NULL);
put 'hiking', '7', 'InfoHiking:name', 'Tikjda'
put 'hiking', '7', 'InfoHiking:region', 'Tizi Ouzou'
put 'hiking', '7', 'InfoTechnique:distance', 10
put 'hiking', '7', 'InfoTechnique:Altitude', 1900

# (8, 'Feroukha', 'Blida', 14.18, 454, NULL);
put 'hiking', '8', 'InfoHiking:name', 'Feroukha'
put 'hiking', '8', 'InfoHiking:region', 'Blida'
put 'hiking', '8', 'InfoTechnique:distance', 14.18
put 'hiking', '8', 'InfoTechnique:Altitude', 454

# (9, 'Chrea Azzazga', 'Tizi Ouzou', 6.23, 1548, 11);
put 'hiking', '9', 'InfoHiking:name', 'Chrea Azzazga'
put 'hiking', '9', 'InfoHiking:region', 'Tizi Ouzou'
put 'hiking', '9', 'InfoTechnique:distance', 6.23
put 'hiking', '9', 'InfoTechnique:Altitude', 1548
put 'hiking', '9', 'InfoHiking:suiteHiking', 11
 ```
### Update TABLE :

Update the distance of the first hiking (55 instead of 35) :

```shell
put 'hiking', 1, 'InfoTechnique:distance', 55
```
### Get From TABLE :
The syntax to get from TABLE :
```shell
# for a single line
get 'table_name', 'id'
get 'table_name', 'id', 'family'
get 'table_name', 'id', 'family:column'
get 'table_name', 'id', {COLUMN=>'family'}
get 'table_name', 'id', {COLUMN=>'family:column'}
```
```shell
# for a several line
1- scan 'table_name'
2- scan 'table_name', {COLUMN=>['family']}
3- scan 'table_name', {COLUMN=>['family:column']}
```
#### example:

get from TABLE hiking 4 :

```shell
get 'hiking', '4'
```
get InfoHiking of hiking 5.

```shell
get 'hiking', 5, 'InfoHiking'
```
### Use FILTER : 
[Filters In Hbase Shell Tutorial](http://www.hadooptpoint.org/filters-in-hbase-shell/)

The syntax to filter DATA :
```shell
# for a single line
get 'table_name', 'id', {FILTER=>"filter"}
```
or :
```shell 
# for a several line
scan 'table_name', {FILTER=>"filter"}
```
show the list of filters available in HBase :
```shell
show_filters
```
#### example : 
get the distance of the hiking 'Murdjadu Mountain' :

```shell
scan 'hiking',{FILTER=>
	"SingleColumnValueFilter('InfoHiking', 'name', =,'binary:Montagne de Murdjadju')
	AND ColumnPrefixFilter ('distance')
	"}
```
or :
```shell
scan 'hiking',{FILTER=>
		"SingleColumnValueFilter('InfoHiking', 'name', =,'binary:Montagne de Murdjadju')
		AND QualifierFilter(=,'binary:distance')
	"}
```

get the distance of the hiking in the region of 'Tizi Ouzou' :

```shell
scan 'hiking',{FILTER=>
		"SingleColumnValueFilter('InfoHiking', 'region', =,'binary:Tizi Ouzou')
		AND QualifierFilter(=,'binary:distance') 
	"}
```
