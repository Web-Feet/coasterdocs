# Block Review CSV File

This file is used to set block data, overwriting anything set in the theme files or database.

It can be created in any theme at this location: `imports/blocks.csv`

The file should be a simple comma seperated CSV, which should be editable in most spreadheet programs.

## CSV Columns

Column headers should be in the first row of the CSV.
The only required column is the block name, the rest are all optional.
For each row of block data here are the possible values.

- Block Name - string
- Block Label - string
- Block Note - string
- Block Category - string (the name of the category not the Id)
- Block Type - string
- Global (show in site-wide) - yes/no/y/n/1/0
- Global (show in pages) - yes/no/y/n/1/0
- Templates - comma seperated list or * for all
- Block Order - number
- Block Active - yes/no/y/n/1/0

A blank value will be ignored if you don't want to set data on a spefici block.
