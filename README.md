# Duden [![Version](http://img.shields.io/pypi/v/duden.svg?style=flat)](https://pypi.python.org/pypi/duden/)

**duden** is a CLI-based program and python module, which can provide various information about given german word. The provided data are parsed from german dictionary [duden.de](https://duden.de).

![duden screenshot](screenshot.png)

## Installation
```console
pip3 install duden
```

## Usage

### CLI
```console
$ duden Löffel

Löffel, der
===========
Word type: Substantiv, maskulin
Commonness: 2/5
Separation: Löf|fel
Meaning overview:
 0.  a. [metallenes] [Ess]gerät, an dessen unterem Stielende eine schalenartige Vertiefung sitzt und das zur Aufnahme von Suppe, Flüssigkeiten, zur Zubereitung von Speisen o. Ä. verwendet wird
     b. (Medizin) Kürette

 1. (Jägersprache) Ohr von Hase und Kaninchen

Synonyms:
Ohr; [Ge]hörorgan; (salopp) Horcher, Horchlappen, Lauscher; (Jägersprache) Loser, Teller
```

<details>
<summary>Full CLI syntax (expand)</summary>

```console
$ duden --help
usage: duden [-h] [--title] [--name] [--article] [--part-of-speech]
             [--frequency] [--usage] [--word-separation]
             [--meaning-overview] [--synonyms] [--origin]
             [--compounds [COMPOUNDS]] [-g [GRAMMAR]] [--export]
             [--words-before] [--words-after] [-r RESULT] [--fuzzy]
             [--no-cache] [-V] [--phonetic] [--alternative-spellings]
             word

positional arguments:
  word

optional arguments:
  -h, --help            show this help message and exit
  --title               display word and article
  --name                display the word itself
  --article             display article
  --part-of-speech      display part of speech
  --frequency           display commonness (1 to 5)
  --usage               display context of use
  --word-separation     display proper separation (line separated)
  --meaning-overview    display meaning overview
  --synonyms            list synonyms (line separated)
  --origin              display origin
  --compounds [COMPOUNDS]
                        list common compounds
  -g [GRAMMAR], --grammar [GRAMMAR]
                        list grammar forms
  --export              export parsed word attributes in yaml format
  --words-before        list 5 words before this one
  --words-after         list 5 words after this one
  -r RESULT, --result RESULT
                        display n-th (starting from 1) result in case of multiple words matching the input
  --fuzzy               enable fuzzy word matching
  --no-cache            do not cache retrieved words
  -V, --version         print program version
  --phonetic            display pronunciation
  --alternative-spellings
                        display alternative spellings
```
</details>

### Module usage

```python
>>> import duden
>>> w = duden.get('Loeffel')
>>> w.name
'Löffel'
>>> w.word_separation
['Löf', 'fel']
>>> w.synonyms
'Ohr; [Ge]hörorgan; (salopp) Horcher, Horchlappen, Lauscher; (Jägersprache) Loser, Teller'
```
For more examples see [usage documentation](docs/usage.md).

## Development

Dependencies and packaging are managed by [Poetry](https://python-poetry.org/).

Install the virtual environment and enter it with
```console
$ poetry install
$ poetry shell
```

### Testing and code style

To execute data tests, run
```console
$ pytest
```

To run python style autoformaters (isort), run
```console
$ make autoformat
```

### Publishing

Before `poetry publish`, make sure to build locale files with `make localization`.

Poetry configuration for PyPI and Test PyPI credentials are well covered in [this SO answer](https://stackoverflow.com/a/72524326).

## Supported versions of Python

* Python 3.4+
