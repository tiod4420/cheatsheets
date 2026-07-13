# hledger

## Usual commands

```shell
# Balance sheet without opening / closing balances
hledger [bs|balancesheet] not:tag:clopen

# Show amount of cash per account
hledger [cf|cashflow]

# Show expenses per tag
hledger [is|incomestatement] --pivot=<TAG_NAME>
```

## Filtering

```shell
# Print for a given (loose) date period
hledger print date:<DATE>
# For instance
hledger print date:'last month'

# Filter per amount (acct: is default)
hledger print REGEX
hledger print acct:REGEX

# Filter per amount
hledger print amt:'>50'

# Filter per currency
hledger print cur:EUR

# Filter per description/payee/note
hledger print {desc,payee,note}:QUERY

# Negative filter
hledger print not:QUERY
```

## Opening / Closing account

```shell
hledger -f <CURRENT_YEAR>.ledger close --clopen -e <NEW_YEAR>
```

## CSV

```shell
# Print CSV file, using FILE.csv.rules as rules
hledger -f <FILE>.csv --rules <RULES>.rules print

# Print CSV file, using specified rules
hledger -f <FILE>.csv --rules <RULES>.rules print
```

## Lists

```shell
# Show account names
hledger accounts

# Show only used accounts, in tree style
hledger accounts --tree --used

# Show transaction descriptions
hledger descriptions
hledger payees
hledger notes

# Show tag names
hledger tags
```

## Stats

```shell
# Ledger stats
hledger stats
```
