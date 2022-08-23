# Fixed Point Decimals

- Rounding problems occur when storing decimals due to the binary nature of computers. For example, 0.1 and 0.2 cannot be stored as their exact values. These precision errors can accumulate and cause problems for certain applications.

- For applications where accurate precision is prioritized over performance, some DBMS will store the data in string along with its metadata of the attribute.

- When retrieving the data, the DBMS interprets the string, and reconstruct the original data therefore guaranteeing precision. This creates performance overhead as, for example, adding two decimals 0.1 and 0.2 is not a single line of execution anymore.
