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
