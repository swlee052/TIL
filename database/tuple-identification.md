# Tuple Identification
1) Fixed length offsets
> Each value is theh same length for an attribute. (otherwise, offset calculation wouldn't work)

`Id A B C D`

`0`

`1`

`2`

2) Embedded
> - Each value is stored with its tuple id in a column
> - Has huge storage overhead

`A B C D`

`0 0 0 0`

`1 1 1 1`

`2 2 2 2`