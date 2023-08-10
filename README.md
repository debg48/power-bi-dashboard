# Power BI Dashboard

The data contains three tables Budget, Sales and Product Master
Budget table consists of monthwise budget with respect to product id.
The Sales table contains datewise sales amount of different products.
Product Master table contains name and category of each product.

We loaded the data in PowerBI 

We createed a new table using CALENDERAUTO() DAX function , we end up having a table with a column of all the dates from or model . We add three more colums to this data using 'date dim'[Date] function as follows:

``` 'date dim'[Date].[Year] ```

``` 'date dim'[Date].[Month] ```

``` 'date dim'[Date].[Quater] ```

Now we check the model view to see that Power BI has automatically found relation between the three tables on basis of product id 

<img src="Screenshot 2023-08-10 172627.png">

Now we create a relation between Date of Sales table and Date Dim table we just created  and month of Budget table and Date of Date dim table by simply draging Date to the respective column names 

<img src="Screenshot 2023-08-10 173241.png">

We will hide the following colums from report view :

 * From Budget table month and product id
 * From Product Master product id
 * From Sales date and product id

In the report view we will create new measures in Sales Table as follows :

```
CY Sales = 
Var CY = MAX('Date Dim'[Year])

Return
CALCULATE(SUM(Sales[Sale Amount]),'Date Dim'[Year]=CY)
```

```
PY Sales = CALCULATE(([CY Sales],SAMEPERIODLASTYEAR('Date Dim'[Date]))
```

```
YOY Sales Growth % = DIVIDE([CY Sales]-[PY Sales],[PY Sales],BLANK())
```

THe following measures for Budget Table :

```
Budget Sale = 
Var CY = MAX('Date Dim'[Year])

Return
CALCULATE(SUM(Budget[Budgeted Amt]),'Date Dim'[Year]=CY)
```


