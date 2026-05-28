# football.db Quick Starter Datafile Templates


## What's news in 2026?

You can use the [`fbtxt2json` command-line tool](https://github.com/sportdb/footty/tree/master/fbtxt2json) to convert any (match data) file in the Football.TXT format to JSON.  Try in your shell / terminal:

```
$ fbtxt2json -h
```

resulting in:

```
Usage: fbtxt2json [options] DATAFILES or DIRS
        --verbose, --debug           turn on verbose / debug output (default: false)
    -o, --output PATH                output to file / dir
        --seasons SEASONS            turn on processing only seasons (default: false)
```

Note - the football.txt to .json converter works in two modes.

(i) you can pass in one or more (match data) files to concat(enate) into one .json output or <br>
(ii) you can pass in one or more directories to convert all (match data) files (automagically) one-by-one.


Let's try to convert the English Premier League 2025/26
in the Football.TXT format (see [`england/2025-26/1-premierleague.txt`](https://github.com/openfootball/england/blob/master/2025-26/1-premierleague.txt)) to JSON:

```
$ fbtxt2json england/2025-26/1-premierleague.txt -o en.1.json
```

Tip - Or try to convert the complete [`/england`](https://github.com/openfootball/england) repo at once:

```
$ fbtxt2json england
```

resulting in:

```
england/
   2024-25/
       1-premierleague.json
       2-championship.json
       3-league1.json
       4-league2.json
       5-nationalleague.json
       eflcup.json
       facup.json
...
```

Note - by default all `.txt` file extensions get changed to `.json` (if the include a season in the basename or the dirname).
To use a different output directory use the `-o/--output` option. Example:

```
$ fbtxt2json england -o ./o    
```


### Bonus -  fbtxt2csv - convert football.txt (match data) files to the (tabular) comma-separated values (.csv) format


Try in your shell / terminal:

```
$ fbtxt2csv -h
```

resulting in:

```
Usage: fbtxt2csv [options] DATAFILES and/or DIRS
        --verbose, --debug           turn on verbose / debug output (default: false)
    -o, --output PATH                output to file
        --seasons SEASONS            turn on processing only seasons (default: false)
```

Let's try to convert the "Euro" European Championship 2024
in the Football.TXT format (see [`euro/2024--germany/euro.txt`](https://github.com/openfootball/euro/blob/master/2024--germany/euro.txt)) to CSV:


```
$ fbtxt2csv euro/2024--germany/euro.txt -o euro2024.csv
```

resulting in:

``` csv
League,Date,Time,Team 1,Team 2,Score,HT,FT,ET,P,Round,Ground
Euro 2024,2024-06-14,21:00,Germany,Scotland,,3-0,5-1,,,"Group A, Matchday 1",München
Euro 2024,2024-06-15,15:00,Hungary,Switzerland,,0-2,1-3,,,"Group A, Matchday 1",Köln
Euro 2024,2024-06-19,18:00,Germany,Hungary,,1-0,2-0,,,"Group A, Matchday 2",Stuttgart
Euro 2024,2024-06-19,21:00,Scotland,Switzerland,,1-1,1-1,,,"Group A, Matchday 2",Köln
Euro 2024,2024-06-23,21:00,Switzerland,Germany,,1-0,1-1,,,"Group A, Matchday 3",Frankfurt
Euro 2024,2024-06-23,21:00,Scotland,Hungary,,0-0,0-1,,,"Group A, Matchday 3",Stuttgart
Euro 2024,2024-06-15,18:00,Spain,Croatia,,3-0,3-0,,,"Group B, Matchday 1",Berlin
Euro 2024,2024-06-15,21:00,Italy,Albania,,2-1,2-1,,,"Group B, Matchday 1",Dortmund
Euro 2024,2024-06-19,15:00,Croatia,Albania,,0-1,2-2,,,"Group B, Matchday 2",Hamburg
Euro 2024,2024-06-20,21:00,Spain,Italy,,0-0,1-0,,,"Group B, Matchday 2",Gelsenkirchen
Euro 2024,2024-06-24,21:00,Albania,Spain,,0-1,0-1,,,"Group B, Matchday 3",Düsseldorf
Euro 2024,2024-06-24,21:00,Croatia,Italy,,0-0,1-1,,,"Group B, Matchday 3",Leipzig
...
```

or pass in the directory and get all (match data) files rolled-into-one tabular .csv file.
Try:

```
$ fbtxt2csv euro -o euro.csv
```

resulting in:

``` csv
League,Date,Time,Team 1,Team 2,Score,HT,FT,ET,P,Round,Ground
Euro 1960,1960-07-06,20:00,France,Yugoslavia,4-5,,,,,Semi-finals,"Parc des Princes, Paris"
Euro 1960,1960-07-06,20:30,Czechoslovakia,Soviet Union,0-3,,,,,Semi-finals,"Stade Vélodrome, Marseille"
Euro 1960,1960-07-09,21:30,Czechoslovakia,France,2-0,,,,,Third place play-off,"Stade Vélodrome, Marseille"
Euro 1960,1960-07-10,20:30,Soviet Union,Yugoslavia,,,,2-1,,Final,"Parc des Princes, Paris"
Euro 1964,1964-06-17,20:00,Spain,Hungary,,,,2-1,,Semi-finals,"Santiago Bernabéu, Madrid"
Euro 1964,1964-06-17,22:30,Denmark,Soviet Union,0-3,,,,,Semi-finals,"Camp Nou, Barcelona"
Euro 1964,1964-06-20,20:00,Hungary,Denmark,,,,3-1,,Third place play-off,"Camp Nou, Barcelona"
Euro 1964,1964-06-21,18:30,Spain,Soviet Union,2-1,,,,,Final,"Santiago Bernabéu, Madrid"
Euro 1968,1968-06-05,18:00,Italy,Soviet Union,,,,0-0,,Semi-finals,"Stadio San Paolo, Naples"
Euro 1968,1968-06-05,21:15,Yugoslavia,England,1-0,,,,,Semi-finals,"Stadio Comunale, Florence"
Euro 1968,1968-06-08,15:00,England,Soviet Union,2-0,,,,,Third place play-off,"Stadio Olimpico, Rome"
Euro 1968,1968-06-08,21:15,Italy,Yugoslavia,,,,1-1,,Final,"Stadio Olimpico, Rome"
Euro 1968,1968-06-10,21:15,Italy,Yugoslavia,2-0,,,,,"Final, Replay","Stadio Olimpico, Rome"
Euro 1972,1972-06-14,20:00,West Germany,Belgium,2-1,,,,,Semi-finals,"Antwerpen, Bosuil"
Euro 1972,1972-06-14,20:00,Soviet Union,Hungary,1-0,,,,,Semi-finals,"Brussel, Astridpark"
Euro 1972,1972-06-17,20:00,Belgium,Hungary,2-1,,,,,Third place play-off,"Liège, Stade Sclessin"
Euro 1972,1972-06-18,16:00,West Germany,Soviet Union,3-0,,,,,Final,"Bruxelles, Stade Heysel"
...
```




## Build your own football.db (with sqlite & friends)

`football.db` quick starter datafile templates -
`worldcup.db`, `euro.db`, `england.db` etc.


### Usage  - Read / Load Match files with `football-to-sqlite` / `football-to-psql`

Run the `football-to-sqlite` tool against match files in the Football.TXT format like so:

```
$ football-to-sqlite england.db 2020-21/1-premierleague.txt
```

or pass in more than one match file (e.g. different leagues or more seasons):

```
$ football-to-sqlite england.db 2020-21/1-premierleague.txt \
                                2020-21/2-championship.txt  \
                                2020-21/3-league1.txt       \
                                2020-21/4-league2.txt       \
                                2020-21/5-nationalleague.txt

# -or-

$ football-to-sqlite premier.db 2020-21/1-premierleague.txt  \
                                2019-20/1-premierleague.txt  \
                                2018-19/1-premierleague.txt  \
                                2017-18/1-premierleague.txt  \
                                2016-17/1-premierleague.txt
```

Note: If the single-file SQLite database (and its tables, views & indices) do not (yet) exist,
they get auto-created on the first run.

[More »](https://github.com/sportdb/football.db/tree/master/football-to-sqlite)


### Usage - sportdb with quick starter datafile templates

Use the `sportdb new <name>` command to build yourself a copy. Example:

    $ sportdb new eng2024-25

Will run the following steps:

- Step 1:  Download [`eng2024-25.rb`](eng2024-25.rb) Datafile (from GitHub) to your working folder as `./Datafile`
- Step 2:  Run the `sportdb build` command
    - Step 2.a:  Download all datasets listed in the `Datafile` as zip archives (from GitHub) to `./tmp`
    - Step 2.b:  Create the "empty" database, that is, table structure, indexes, etc. (schema)
    - Step 2.c:  Read in all datasets from the zip archives in `./tmp` (no need to unpack)

That's it.

### Usage - Do-It-Yourself (DIY) - Download and Unpack Zip Archive or Git Clone

Download and unpack the zip archive with the datasets or if you have git installed use the `git clone` command to
get a local copy.

Try in your working folder (that is, `/england`):

```
$ sportdb build
$ sportdb --verbose build     # or for more (verbose) details incl. debug info
```

This will

- setup a new single-file SQLite database e.g. `./sport.db` and
- read in all datasets in plain text (`.txt`)

That's it.



## Appendix

### Q: What's `sportdb`?

`sportdb` is a command line tool that lets you read datasets (e.g. leagues, clubs, match schedules, etc.)
in plain text into your SQL database of choice (e.g. SQLite, PostgreSQL, etc.).
To get a list of all commands and options type:

```
$ sportdb help
```

Resulting in:

```
SYNOPSIS
    sportdb [global options] command [command options] [arguments...]

VERSION
    2.0

GLOBAL OPTIONS
    -d, --dbpath=PATH - Database path (default: .)
    -n, --dbname=NAME - Database name (default: sport.db)
    --verbose         - (Debug) Show debug messages
    --version         - Show version

COMMANDS
    new, n        - Build DB w/ quick starter Datafile templates
    build, b      - Build DB (download/create/read); use ./Datafile - zips get downloaded to ./tmp

MORE COMMANDS
    create        - Create DB schema
    download, dl  - Download datasets; use ./Datafile - zips get downloaded to ./tmp
    read, r       - Read datasets; use ./Datafile - zips required in ./tmp
    logs          - Show logs
    props         - Show props
    stats         - Show stats
    test          - (Debug) Test command suite
    help          - Shows a list of commands or help for one command
```


### `new` Command

```
NAME
    new - Build DB w/ quick starter Datafile templates
SYNOPSIS
    sportdb [global options] new NAME

EXAMPLES
    sportdb new eng2024-25
    sportdb new eng
```


### `build` Command

```
NAME
    build - Build DB (download/create/read); use ./Datafile - zips get downloaded to ./tmp

SYNOPSIS
    sportdb [global options] build

EXAMPLES
    sportdb build
```



## License

The datafiles are dedicated to the public domain.
Use as you please with no restrictions whatsoever.


## Questions? Comments?

Yes, you can. More than welcome.
See [Help & Support »](https://github.com/openfootball/help)

