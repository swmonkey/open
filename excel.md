## How to remove everything after a specific character
e.g. ggg, gggg
LEFT(cell, SEARCH("char", cell) -1)

=LEFT(A2, SEARCH(",", A2) -1)

## How to remove everything before a specific character
e.g. ggg, gggg
RIGHT(cell, LEN(cell) - SEARCH("char", cell))

The formula is:

=RIGHT(A2, LEN(A2) - SEARCH(",", A2))

If the comma is followed by a space character. To avoid leading spaces in the results, we wrap the core formula in the TRIM function:

=TRIM(RIGHT(A2, LEN(A2) - SEARCH(",", A2)))
