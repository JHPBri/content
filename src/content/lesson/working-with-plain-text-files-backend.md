---
slug: "working-with-plain-text-files-backend"
title: "Working with Plain Text Files"
subtitle: "Storing and retrieving information to files using backend languages"
cover: "https://ucarecdn.com/e6ca8daf-9f02-487b-8296-1f440a4e6e59/storage_background.jpg"
status: "draft"
authors: ["alesanchezr"]
textColor: "white"
date: "2018-05-11"
tags: ["marketing","query-string"]

---

## Files are the only way to `store` on a computer.

Your entire computer hard drive is comprised of files, is the most low level way to store information, your compute runs on a `file fystem` or `file directory` control that how data is stored and retrieved.

Using a backend language you can access the majority of the computer files, and that givis you almost endless power!

## Retrieving data from files

Lets say that you have the bitcoin prices from the last day in a `bitcoin_prices.csv` file with the following format:

<before-after width="400px"
    before="https://ucarecdn.com/97f74cd8-acdd-4ce9-aa26-bfd494e9b550/bitcoin_price_csv.png" 
    after="https://ucarecdn.com/709ff7ce-f7f6-4b16-a172-521fe1787733/bitcoing_prices_table.png" 
/>

[[info]]
| :tv: Five minute video explaining [what is a CSV file](https://www.youtube.com/watch?v=_blfh7uR05A)

Basically, every line in the CSV file represents one price, for example:
```python
Currency,Date,Closing Price (USD),24h Open (USD),24h High (USD),24h Low (USD)
BTC,2019-10-29,9455.7246926058,9228.0745024715,9551.7787262272,9125.7784571584
```

You can read the file with any backend programing language and interpret it based on the positions of the values:

```python{numberLines: true}
import csv, json

file = open("bitcoin_prices.csv", "r") 
csv_f = csv.reader(file)

prices = []
for row in csv_f:
  prices.append({
	  "ticker": row[0],
	  "price": row[2]
  })
```

<iframe height="400px" width="100%" src="https://repl.it/@4GeeksAcademy/Read-bitcoin-prices-python-file?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


## Saving data into files

Let's say you are running a script that has a variable called `todos` that contains a todo list:

```python
todos = ['make the bed', 'do the laundry', 'finish homework']
```

That variable is being stored in the RAM memory until you decide to save it to a text-file or database. The RAM memory is not reliable because your computer could loose power any moment (turned off).

You can save that variable into a `todos.csv` file with the following python code:

```python{numberLines: true}
todos = ['make the bed', 'do the laundry', 'finish homework']

todos_as_csv = ','.join(todos) # convert the list into a string
file = open('todos.csv', 'w+') # open the file for writing 'w', create if it doesn't exists
file.write(todos_as_csv) # write the content
file.close() # close the file
```

The code above will create or update a `todos.csv` with a content similar to this:

```csv
make the bed, do the laundry, finish homework
```

<iframe height="400px" width="100%" src="https://repl.it/@4GeeksAcademy/Writing-into-files-with-python?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

## Different file formats

| Format        | Explanation |
| ------        | ----------- |
| CSV           | Comma `,` separated values, one line for each row or different entity. |
| JSON          | Very similar to Javascript syntax, made specially for developers and the most used format when transmiting information over the internet (HTTP) |
| Yaml or YML   | The easies format to understand, developers love it because it is fast but its also very similar to a simpel text file, it allows comments and uses intentation instead of commas or braces for delimitation |
| XML           | Very popular in the 90's and still being used in a lot of legacy software |

### Converting from CSV to RAM memory

```py
file = open("bitcoin_prices.csv", "r") 
csv_f = csv.reader(file)
```

### Converting from JSON to RAM memory

### Converting from Yaml to RAM memory

### Converting from XML to RAM memory
