# biblibrary : a command line tool for managing references

This is a simple command line tool for managing references (e.g. like a very primitive Mendeley) that builds up a bibtex file (at `~/.biblib.bib`). You can then search it or get ones with particular tags, and output the whole thing or a subset to tex file or pdf. Please bear in mind that this project is in its very early stages.

## Install
`pip install biblibrary`

## Usage
Type `biblib --help` for command line help. As an example you could add [this](https://www.nature.com/articles/s41558-018-0091-3) article by:
```
biblib add --title "Scenarios towards limiting global mean temperature increase below 1.5 °C" --year 2018 --journal Nature --author "Rogelj, J. Popp, A. Calvin, K.V. et al"
```
Which would give:
```
You have not entered: label, type
0 )  label
1 )  type
Which [0 to 1]?
```
So we will enter 0:
```
label: rogelj2018
type: article
Would you like to add anymore fields [bool]?y
0 )  tags
1 )  address
2 )  annotate
3 )  booktitle
4 )  chapter
5 )  crossref
6 )  edition
7 )  editor
8 )  howpublished
9 )  institution
10 )  key
11 )  month
12 )  note
13 )  number
14 )  organization
15 )  pages
16 )  publisher
17 )  school
18 )  series
19 )  volume
20 )  doi
Which [0 to 20]? 0
tags: climate change,climate,1.5degrees,warming,ssp
Are you sure [bool]?y
Would you like to add anymore fields [bool]?y
...
Which [0 to 20]? 20
doi: https://doi.org/10.1038/s41558-018-0091-3
Are you sure [bool]?y
Would you like to add anymore fields [bool]?n
You have entered:
    title: Scenarios towards limiting global mean temperature increase below 1.5 °C
    year: 2018
    journal: Nature
    author: Rogelj, J. et al
    note: sounds bad 
    type: article
    doi: https://doi.org/10.1038/s41558-018-0091-3
    tags: climate change,climate,1.5degrees,warming,ssp
    label: rogelj2018
Is this correct [bool]?y
```
Now we might want to see what's in out bibliography:
```
biblib show
@article{rogelj2018,
    author = "Rogelj, J. et al",
    title = "Scenarios towards limiting global mean temperature increase below 1.5 °C",
    year = "2018",
    journal = "Nature",
    doi = "https://doi.org/10.1038/s41558-018-0091-3",
    tags = "climate change,climate,1.5degrees,warming,ssp"
}
```
Or output it to a pdf (see examples folder):
```
biblib show --compile true --stdout false
```
Or just to a bibtex file, show it on screen, and only output ones with the tags "climate change,ssp" (or):
```
biblib show --tags "climate change,ssp" --bibtex true
...
```

## Thanks
Special thanks to [pybtex](https://pybtex.org/) so I didn't have to make a bibtex handler, and to [click](https://click.palletsprojects.com/en/8.0.x/) for hugely simplifying the command line tool aspect.