# SB-JSON-Exercise

Work the following requests:
 1) Find the 10 countries with most projects
 2) Find the top 10 major project themes (using column 'mjtheme_namecode')
 3) In 2. above you will notice that some entries have only the code and the name is missing. Create a dataframe with the missing names filled in.
 
 Use knowledge gained in the lessons in the course thus far and the commands provided below.
 
JSON examples and exercise

    get familiar with packages for dealing with JSON
    study examples with JSON strings and files
    work on exercise to be completed and submitted

    reference: http://pandas.pydata.org/pandas-docs/stable/io.html#io-json-reader
    data source: http://jsonstudio.com/resources/

import pandas as pd

imports for Python, Pandas

import json

from pandas.io.json import json_normalize

JSON example, with string

    demonstrates creation of normalized dataframes (tables) from nested json string
    source: http://pandas.pydata.org/pandas-docs/stable/io.html#normalization

# define json string

data = [{'state': 'Florida', 

         'shortname': 'FL',

         'info': {'governor': 'Rick Scott'},

         'counties': [{'name': 'Dade', 'population': 12345},

                      {'name': 'Broward', 'population': 40000},

                      {'name': 'Palm Beach', 'population': 60000}]},

        {'state': 'Ohio',

         'shortname': 'OH',

         'info': {'governor': 'John Kasich'},

         'counties': [{'name': 'Summit', 'population': 1234},

                      {'name': 'Cuyahoga', 'population': 1337}]}]

# use normalization to create tables from nested element

json_normalize(data, 'counties')

# further populate tables created from nested element

json_normalize(data, 'counties', ['state', 'shortname', ['info', 'governor']])

JSON example, with file

    demonstrates reading in a json file as a string and as a table
    uses small sample file containing data about projects funded by the World Bank
    data source: http://jsonstudio.com/resources/

# load json as string

json.load((open('data/world_bank_projects_less.json')))

# load as Pandas dataframe

sample_json_df = pd.read_json('data/world_bank_projects_less.json')

sample_json_df

JSON exercise

Using data in file 'data/world_bank_projects.json' and the techniques demonstrated above,

    Find the 10 countries with most projects
    Find the top 10 major project themes (using column 'mjtheme_namecode')
    In 2. above you will notice that some entries have only the code and the name is missing. Create a dataframe with the missing names filled in.

