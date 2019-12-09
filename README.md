# Sample Binary Data

This repo contains a sample data file (IBM.dat) that contains 
historical stock prices.

The file format is as follows:

1. The header is just a 64-bit integer that represents the number of records in this file.
2. The rest of the file contains stock price records.  

Each record contains the followings:
- Bytes 0-7: integer, days since Epoch (0000-01-01)
- Bytes 8-15: floating point number, representing the stock price
- Bytes 16-23: integer, representing the trade volume 

