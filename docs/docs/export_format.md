# Export format

Since version 2.0, a Catima export is a Zip file containing:

1. A single catima.csv file
2. All image files as .png

Continue reading for more details about both.

Before 2.0, the backup format was just the .csv file, not inside a .zip file. It can still be imported in 2.0+. To import a 2.0+ backup into older Catima versions, one should extract the .csv file and import that instead.

## catima.csv
The catima.csv file is a CSV file in the following format:

```
[version number]

[group database table description]
[one line per group]

[card database table description]
[one line per card]

[card to group linking database table description]
[one line per link]
```

Version number is always 2. If a database table is empty, there are simply no lines. For valid possible values for each table, see https://github.com/TheLastProject/Catima/wiki/Card-sharing-URL-format.

Example full export:
```
2

_id
Health
Food
Fashion

_id,store,note,expiry,balance,balancetype,cardid,headercolor,barcodetype,starstatus
8,Clothes Store,Note about store,,0,,a,-5317,,0
2,Department Store,,,0,,A,-9977996,,0
3,Grocery Store,,,150,,dhd,-9977996,,0
4,Pharmacy,,,0,,dhshsvshs,-10902850,,0
5,Restaurant,Note about restaurant here,,0,,98765432,-10902850,CODE_128,0
6,Shoe Store,,,12.50,EUR,a,-5317,AZTEC,0

cardId,groupId
8,Fashion
3,Food
4,Health
5,Food
6,Fashion
```

## Image files
The image files are named using the following pattern:
```
card_<id>_<side>.png
```

With id referring to the id of the loyalty card it belongs to and side being either `front` or `back`.
