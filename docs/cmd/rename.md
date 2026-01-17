<!-- Generated -->
# xan rename

```txt
Rename columns of a CSV file. Can also be used to add headers to a headless
CSV file. The new names must be passed in CSV format to the column as argument,
which can be useful if the desired column names contains actual commas and/or double
quotes.

Note that to be as performant as possible, this command does not try
to be clever and only parses the first CSV row to drop it. The rest of
the file will be flushed to the output as-is without any kind of normalization.

Renaming all columns:

    $ xan rename NAME,SURNAME,AGE file.csv

Renaming a selection of columns:

    $ xan rename NAME,SURNAME -s name,surname file.csv
    $ xan rename NAME,SURNAME -s '0-1' file.csv

Adding a header to a headless file:

    $ xan rename -n name,surname file.csv

Prefixing column names:

    $ xan rename --prefix university_ file.csv

Column names with characters that need escaping:

    $ xan rename 'NAME OF PERSON,"AGE, ""OF"" PERSON"' file.csv

Using a mapping file to rename columns:

    $ xan rename --mapping renames.csv file.csv
    $ xan rename --mapping renames.csv --mapping-source Source --mapping-dest Dest file.csv

Usage:
    xan rename [options] --replace <pattern> <replacement> [<input>]
    xan rename [options] --prefix <prefix> [<input>]
    xan rename [options] --suffix <suffix> [<input>]
    xan rename [options] --slugify [<input>]
    xan rename [options] --mapping <file> [<input>]
    xan rename [options] <columns> [<input>]
    xan rename --help

rename options:
    -s, --select <arg>     Select the columns to rename. See 'xan select -h'
                           for the full syntax. Note that given selection must
                           not include a same column more than once.
    -p, --prefix <prefix>  Prefix to add to all column names.
    -x, --suffix <suffix>  Suffix to add to all column names.
    -S, --slugify          Transform the column name so that they are safe to
                           be used as identifiers. Will typically replace
                           whitespace & dashes with underscores, drop accentuation
                           etc.
    -R, --replace          Replace matches of a pattern by given replacement in
                           column names.
    -m, --mapping <file>        Path to a CSV file containing the column rename mapping.
        --mapping-source <col>  Column in mapping file with source names. [default: 0]
        --mapping-dest <col>    Column in mapping file with dest names. [default: 1]
    -f, --force            Ignore unknown columns to be renamed.

Common options:
    -h, --help             Display this message
    -o, --output <file>    Write output to <file> instead of stdout.
    -n, --no-headers       When set, the first row will not be interpreted
                           as headers. (i.e., They are not searched, analyzed,
                           sliced, etc.)
    -d, --delimiter <arg>  The field delimiter for reading CSV data.
                           Must be a single character.
```
