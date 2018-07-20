# xlsparser
Parse excel(xlsx/xls) to other format(dict, csv, json, ...).

## Install

    pip install xlsparser
    pip3 install xlsparser

## Usage

### CLI Usage

    $ xlsparser.py src.xlsx -csv
    [['asdf', 'bbb'], ['看', '我', '变']]

    $ xlsparser.py src.xlsx -json
    [['asdf', 'bbb'], ['看', '我', '变']]

### Module Usage

### parse
The `parse` function support the following file format:

    def parse(src):
        if src.endswith('.xls'):
            return parseXls(src)
        if src.endswith('.xlsx'):
            return parseXlsx(src)
        if src.endswith('.csv'):
            return parseCsv(src)

The `parse` will automatically parse any file to `rows` generator:

    >>> from xlsparser import parse, saveCsv
    >>> rows = parse('some.xlsx')
    >>> list(rows)
    [['asdf', 'bbb'], ['看', '我', '变']]

### Csv operation

    >>> from xlsparser import *

    >>> rows = [('asdf','bbb'), ('看','我','变')]
    >>> saveCsv(rows, 'test.csv')

    >>> list(parseCsv('test.csv'))
    [['asdf', 'bbb'], ['看', '我', '变']]

    toCsv(rows, 'to.csv')

## Required
1. python>=3.5
2. xlrd: required by xls
2. openpyxl>=2.5.4: required by xlsx
