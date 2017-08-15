---
title: [Set the format to use when showing numbers]
tags: [formatting]
keywords: tbd
last_updated: tbd
summary: "blerg"
sidebar: mydoc_sidebar
---
You can set a format for how numbers are displayed in tables and charts. For example, you can display numbers with a different number of digits after the decimal point, based on the data modeling setting **Format Pattern**.

You can use any of the supported number formats for delimiters and number of digits to show using [Java Decimal Notation](http://docs.oracle.com/javase/7/docs/api/java/text/DecimalFormat.html). Currency symbols are not supported.

The default values are:

-   \#,\#\#\# for integer data types \(INT, BIGINT\).
-   \#,\#\#\#.00 for decimal data types \(DOUBLE and FLOAT\).

These are some examples of formats you can use:

|Stored Value|Format Pattern|Display Value|
|------------|--------------|-------------|
|12345.6789|\#,\#\#0.\#\#|12,345.68|
|12345.6789|\#,\#\#0.\#\#\#|12,345.68|
|12345.6789|\#,\#\#0.00000|12,345.68|
|12345.6789|\#,\#\#0|12,345|
|12345.6789|\#,\#\#0.00|12,345.68|
|12345|\#,\#\#0.\#\#|12,345|
|12345|\#,\#\#0.00|12,345.00|

To change the date format used to display a column's values:

1.   Find the **Format Pattern** for the column whose display format you want to change.
2.   Change it to the format you want to use.
3.   Save your changes.

-   **[Locale-based number formatting](../../admin/data_modeling/locale_based_number_formatting.html)**  
Number formatting is set by default based on your browser locale setting. This has been set in order to accommodate users in various geographical locations, primarily in the US and Europe regions.

**Parent topic:** [Data modeling settings](../../admin/data_modeling/data_modeling_settings.html)

**Related information**  


[Model the data for searching](semantic_modeling.html#)