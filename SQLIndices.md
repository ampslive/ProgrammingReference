# SQL Indices

## Table Scan
A retrieve operation that will look at all the records on the table

## Table Seek
A operation that will retrieve fewer number of rows based on an index

## Heap 
- A heap is created when a Create Table operation is done without adding any indices
- It will not re sort data when a new row is added to the table
- Pro's
  - When data is small
  - Dump huge amounts of data to process it later 
- Con's
  - When data needs to be stored in order or grouped together
  - When data needs to be retrieved as a rande
  - Retrieving a row(s) from large data as it will scan through all the records

## B-Tree (Balanced-Tree)
- B-Tree allows the data to be indexed and sorted
- Depending on the size of the page, the data will be split into a tree structure
- Convert a Heap into a B-Tree by using a `Clustered Index` or `Primary Key`
- Using `Clustered Index`... it sorts data based on the index/column specified
- When `Table Scan` is performed (without `where` clause), it does a scan only on `Clustered Index` called `Clustered Index Scan` instead of all columns
- When `Table Seek` is performed (with `where` clause), it does a seekonly on `Clustered Index` called `Clustered Index Seek` instead of all columns
- Pro's
  - Number of operations to retrieve a particular record is lesser as it only needs to parse the tree for the nearest node
- Con's
  - Insertion is slower since it sorts entire data into trees each time a new record is added


## Clustered Index
- `Clustered index` sorts the table and creates an index
- Does not need to be unique
- Only one `clustered index` per table as the table can sort by only one field at a time

## Non Clustered Index
- Creates an index but does not re-sort the table
- Does not need to be unique
- More than one `non-clustered` can exist in a table
- When data is retrieved using the `non clusered index`; a `table seek` operation is done. But if other columns are retrieved along with the `non clustered index`, then a `table scan` is performed on the `clustered index`.
- Too many `non clustered` indices can also cause a performance overhead.

## Filtered Indices
- When a `non clustered index` needs to be created for data with a certain criteria, then a filtered `non clustered index` is created only for the data meeting the filter criteria.
- This reduces the size of the index since all data of a column does not need to be stored in the index

## Using Include
- A `non clustered index` can also be created efficiently by creating a `non clustered index` for the index column (eg. EmployeeId) and using `Include` to add values (ed. EmployeeFirstName, EmployeeLastName) which will get stored along with the index column.
- This avoids the unnecessary costs of adding `non-clusterd indices` to fields that actually do not need to be indexed but is always retrieved along with the `non-clustered index`
