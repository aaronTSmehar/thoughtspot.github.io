---
title: [elephant]
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: "blerg"
sidebar: mydoc_sidebar
---
# About the worksheet join rule with Legacy Row Level Security

When working with worksheets and Legacy Row Level Security, you need to understand how joins are applied. This section gives some examples to explain the interaction between these two concepts.

This section applies only to the older [Legacy Row Level Security](../data_security/about_legacy_row_security.html#). If you are using the newer, [Rule-Based Row Level Security](../data_security/new_row_level_security.html#) \(recommended\), see [About the worksheet join rule with Rule-Based Row Level Security](joins_and_RLS_rule_based.html#). If your schema includes any [chasm traps](../loading/chasm_trap.html#), you must use the newer Rule-Based Row Level Security.

## Worksheet schemas and the root table

To understand how the worksheet join rule is applied, you first need to understand worksheet schemas and the concept of root tables. When you create a worksheet, you're effectively creating a self-contained schema made up of the tables in the worksheet and the relationships \(joins\) between the tables. The joins \(represented by arrows in the diagram\) reflect the primary key/foreign key relationships between the tables in the underlying database schema. The concept of the "root" table in the worksheet schema becomes important for understanding how the joins are applied when searching. In this context, the root table is specific to the schema structure defined for that worksheet.

Suppose you created a worksheet with a schema like the example in the diagram:

 ![](../../images/joins_and_row_level_security.png "Example of a worksheet data schema") 

Imagine your schema as a tree, with a root, branches, and leaves. In this diagram, the root table is the fact table Sales. The root table is typically a fact table. It is the table that does not have a foreign key pointing to it. So if you draw out the schema like the diagram, the tables at the bottom can be referred to as the "leaves" in the schema. If the worksheet only included the tables Products, Departments, and Suppliers, then the root table would be the Products table. Similarly, if the worksheet only included Inventory and Warehouses, the root table would be Inventory.

## Apply all joins

When you choose **Apply all joins** when creating a worksheet, all joins between the tables get pre-applied, whether or not there is row level security present. This is the simplest case.

## Apply joins progressively without row level security

What if you choose **Apply joins progressively** when creating a worksheet, and none of the tables in ThoughtSpot have row level security applied? In this case, the joins will be applied using the worksheet schema as in these examples:

## Example 1: Progressive join with tables from one branch

Joins are applied from the root table of the worksheet down to the lowest leaf table involved in the search. If the worksheet includes all of the tables in the diagram, but when doing a search we choose only columns from Products and Departments, the joins get applied starting at the root table and moving down to all of the tables included in the search. That is, joins from Sales to Products to Departments \(Join 1 and Join 2\) will be used.

## Example 2: Progressive join with tables from different branches

Joins are applied from the root table of the worksheet, moving down each branch, to the lowest leaf tables involved in the search. If we searched on columns from only the Suppliers and Warehouses tables, the join path would traverse down the tree to reach the lowest leaf table in each branch. That is, the joins applied would be:

-   Join 1
-   Join 3
-   Join 4
-   Join 5

## Apply joins progressively with row level security

If any of the tables in ThoughtSpot have level security applied to them, the joins used in your worksheet will be affected like this:

-   If the row level security is applied only outside the scope of the worksheet schema, the join behavior is the same as when there is no row level security in the system.
-   If the worksheet contains even a single table with row level security, non-progressive joins \(**Apply all joins**\) will be used if the join path includes the table with row level security. Remember that the join path begins at the root table and moves down to each of the leaf tables included in the search. So a table with row level security may occur in the join path even if its columns are not included in the search.

## Example 3: Progressive joins when a table outside of the join path has row level security

Assume the table Departments has row level security applied, so that department managers can only see the department they manage. If we did a search on the tables Suppliers and Products, progressive joins would be used. The join path would be Join 1, Join 3. The Department table row level security would not apply, since the Departments table is not in the join path.

## Example 4: Progressive joins when a table in the join path has row level security

Assume now that the table Products has row level security applied, so that buyers could only see the products they order. If we did a search on the tables Departments and Warehouses, **Apply all joins** would be used, so the Products row level security would apply. The join path would be Join 1, Join 2, Join 4, and Join 5. This join path takes us through the Products table, which explains why its row level security would affect the search results, even though no columns from the Products table are included in the search.

## Chasm trap

If you have a worksheet that includes a [chasm trap](../loading/chasm_trap.html#), you cannot use the Legacy Row Level Security. You must migrate your row level security settings to use [Rule-Based Row Level Security](../data_security/new_row_level_security.html#).
