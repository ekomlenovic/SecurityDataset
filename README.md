# SECUTIRY DATA ANALYSIS

## Requirements  
- [Python 3.11](https://www.python.org/downloads/release/python-31110/)
- [Conda](https://docs.anaconda.com/miniconda/) 

### Installation recommanded

```bash
    conda env create -f environment.yml
```


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
Crit1/Target Abortion related
