# Pitfalls

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

<br>
