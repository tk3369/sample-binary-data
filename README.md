# Sample Binary Data

## Stock Prices File Format

This custom stock prices file format consists of the followings:

1. The header is just a 64-bit integer that represents the number of records in this file.
2. The rest of the file contains stock price records.  

Each record contains the followings:
- Bytes 0-7: integer, days since Epoch (0000-01-01)
- Bytes 8-15: floating point number, representing the stock price
- Bytes 16-23: integer, representing the trade volume 

## How the file was generated

The following code was used to create the binary data file.

```
julia> data = CSV.File("IBM.csv");

julia> open("IBM.dat", "w") do io
           write(io, length(data))
           for r in data
               write(io, Dates.date2epochdays(r.Date))
               write(io, r.Close)
               write(io, r.Volume)
           end
       end

shell> ls -l IBM.dat
-rw-r--r--  1 tomkwong  staff  6032 Dec  8 23:41 IBM.dat
```
