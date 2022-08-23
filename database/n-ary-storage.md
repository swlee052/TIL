# N-ary Storage Model (row store)

- The DBMS stores all attributes for a single tuple contiguously in a page.

- Table data is stored row by row.

- Assuming the relation is N-ary, the storage is a sequence of N-tuples.

- Ideal for OLTP workloads where queries tend to operate only on an individual entity and insert-heavy workloads.
  
- use case: commercial applications with user interaction

- Inefficient for accessing a small number of columns within an entity, because the data is retrieved from persistent storage by row. (Bad for analytics)

# Decomposition Storage Model (column store)

- Ideal for OLAP works (read-only queries perform large scans over a subset of the table's attributes)

- use case: analytics on information of many users.

- compression techniques are possible because single attribute of all tuples are stored contigousuly.

- slow for point queries, inserts, updates, and deletes because of tuple splitting / stitching.