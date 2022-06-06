# Module-7-Challenge

For this project, I am using SQl and the Voila library to build a database and web application to analyza the performance of an ETF.

---

## Technologies

This project uses pandas programming language and utilizes Anaconda, Python, Git Bash, Jupyter Lab, and Github. This project also uses SQL and the Voila library.

---

## Installation Guide

These are the required libraries and dependencies:

import numpy as np

import pandas as pd

import hvplot.pandas

import sqlalchemy


You must also install the SQL and Voila packages in your conda dev environment using the code:

    pip install SQLAlchemy
    
    conda install -c conda-forge voila

---

## Usage

I created a temporary SQLite database and an engine to interact with the database:

    database_connection_string = 'sqlite:///etf.db'

    engine = sqlalchemy.create_engine(database_connection_string)


I brought in the information from the database to analyze:

    query = '''
    SELECT * FROM PYPL;
    '''

    pypl_dataframe = pd.read_sql_query(query, con=engine)
          
          
I used queries to get specific data:

    query = '''
    SELECT time, close
    FROM PYPL
    WHERE close > 200
    '''
and combine all the data to anaalyze further:

    query = '''
    SELECT GDOT.time as Time, GDOT.daily_returns as GDOT, GS.daily_returns as GS, PYPL.daily_returns as PYPL, SQ.daily_returns as SQ
    FROM GDOT
    INNER JOIN GS ON GDOT.time = GS.time
    INNER JOIN PYPL ON GDOT.time = PYPL.time 
    INNER JOIN SQ ON GDOT.time = SQ.time 
    '''

---

## Contributors

Allyssa Carmin

---

## License

SMU Fintech Course