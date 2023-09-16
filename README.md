# Pitfalls

<br>

## Orders In Between

Querying orders in-between a certain date range seems simple at first,  
after all the search query syntax allows one to specify the `created_at`  
property with `:>` , `:>=` , `:` , `:<=` , `<` operators.

You'd think you could use a query such as this one:

```
created_at:>=2023-07-23T18:43:48.000Z AND created_at:<=2023-07-23T18:43:50.000Z
```

This however won't return any results, instead you  
will have to make sure the timestamps are quoted.

```
created_at:>'2023-07-23T18:43:48.000Z'
```

Also don't bother using the `>` & `<` operator in this  
context as they seem to behave exactly like `>=` & `<=`

<br>
<br>

## Order Names

An order's name is made up of the actual order  
number combined with an optional prefix / suffix.

The pre & suffix can be changed in a store's settings at any  
time, however existing orders keep their existing names.

If you now want to determine the orders number, you cannot rely  
on querying and removing the store's current prefix / suffix.

Next you might consider matching **1+** digits found in the order  
name, however some stores might use a format like `ED1-1000`.

As orders start at `1000`, you could refine the pattern match only  
**4+** digits, though even that can become problematic in say stores  
that add the current year to their order name `2023_1000`.

A mistake in a pre / suffix can also be highly problematic  
as is apparent with a prefix of `Test-1` that would turn an  
order number of `1000` into `Test-11000`.

<br>
