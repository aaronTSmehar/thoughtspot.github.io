# Delete a data source

When you want to delete a data source, you first need to handle any dependent objects that have been built on top of it. You can easily see these dependencies, and choose how to handle them before deleting the data source.

There are two separate ways to delete a data source. Both of these methods will check for dependencies and warn if any are found:

-   [Delete or change a table in TQL](check_dependencies_tql.html#) describes the dependency checking that occurs when deleting or changing a table using TQL.
-   [Delete a data source from the browser](delete_data_source_UX.html#) describes the dependency checking that occurs when deleting a data source through the ThoughtSpot application.

You can also [Check dependencies in the browser](check_dependency_ux.html#) before attempting to delete a data source.
