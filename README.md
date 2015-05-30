# Pandas-TD

[![Build Status](https://travis-ci.org/treasure-data/pandas-td.svg?branch=master)](https://travis-ci.org/treasure-data/pandas-td)
[![Code Health](https://landscape.io/github/treasure-data/pandas-td/master/landscape.svg?style=flat)](https://landscape.io/github/treasure-data/pandas-td/master)
[![Coverage Status](https://coveralls.io/repos/treasure-data/pandas-td/badge.svg?branch=master)](https://coveralls.io/r/treasure-data/pandas-td?branch=master)
[![PyPI version](https://badge.fury.io/py/pandas-td.svg)](http://badge.fury.io/py/pandas-td)

## Install

You can install the releases from [PyPI](https://pypi.python.org/).

```sh
$ pip install pandas-td
```

## Examples

```python
import os
import pandas_td as td

# Initialize connection
td_conn = td.connect(apikey=os.environ['TD_API_KEY'], endpoint='https://api.treasuredata.com/')
presto = td_conn.query_engine(database='sample_datasets', type='presto')

# Read Treasure Data query into a DataFrame.
df = td.read_td('select * from www_access', presto)

# Read Treasure Data table, sampling 5 percent of data, into a DataFrame.
df = td.read_td_table('nasdaq', presto, sample=0.05, limit=10000)

# Write a DataFrame to a Treasure Data table.
td.to_td(df, 'my_db.test_table', td_conn, if_exists='replace', index=False)
```

## License

Apache Software License, Version 2.0
