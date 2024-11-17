# SECURITY DATA ANALYSIS

## Requirements  
- [Python 3.11](https://www.python.org/downloads/release/python-31110/)
- [Conda](https://docs.anaconda.com/miniconda/) 


### Installation recommanded

```bash
    conda env create -f environment.yml
```
### Report

Report is available in the `report` folder. The report is written in LaTeX and the pdf is available in the `report` folder with the name `report.pdf`.

## Dataset preprocessing :

Dropped columns : 
'alternative',
'region', 
'attacktype1', 
'attacktype2', 
'attacktype3', 
'weaptype1', 
'weapsubtype1', 
'weapsubtype3', 
'weaptype4', 
'weapsubtype4', 
'targtype1', 
'targsubtype1', 
'natlty1', 
'targtype2', 
'targsubtype2', 
'natlty2', 
'targtype3',  
'targsubtype3', 
'natlty3',
'propextent',
'claimmode',
'hostkidoutcome',
'country'


## DATE PREPROCESSING

Concatenation of the columns : "iday", "imonth", "iyear" => "begin_date" of type Datetime

"resolution", "extended" have been compressed into "end_date"
=> If the event doesn't last for more than 24 hour, end_date == begin_date

col "approxdate" have been dropped

## Property Damage

If no property damage (ie. property == 0) : "propextent_txt" has value "None"
If no property damage (ie. property == 0) : "propvalue" has value 0
If property damage is Unknown (ie. property == -9) : "propvalue" has value NaN

## Removing US Related columns

As we're not searching for US related analysis, we won't exploit these columns

'nkillus', 'nwoundus', 'nhostkidus'

## Natural Language columns

Dropped columns filled with natural language that isn't label encodable as we won't exploit them


# Variable correlation
Target Military => All 3 criterion
Crit 3 => Claim Letter
ishostkid => Attack type kidnapping

Attack hijacking => Target maritime & aéroport

Infrastructure => Abortion_related
we 


# Clustering analysis

Kmodes 
=> Cluster 1 seems related to bombing attacks
=> Cluster 2 armed assaults on police and military
=> Cluster 3 Armed assault on citizens & properties

KMeans
=> Cluster 1 : Attacks armed/ kidnapping on citizens
=> Cluster 2 : Bombing on citizen & property
=> Cluster 3 : Bombing on police more suicide / Probably for intimidation

Agglo
=> Cluster 1 : Attacks of all kinds on citizens (assassination, kidnapping, armed assault)
=> Cluster 2 : Bombing attacks
=> Cluster 3 : Armed/Bombing attacks on the police


DBScan to much clusters to make interpretations
