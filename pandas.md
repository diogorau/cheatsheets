# Pandas

## Encode labels
### The first element is the label value, the second is the label name
pd.factorize(df['column'])

## Turn categories into numbers
pd.get_dummies(df)

## Cut into quantiles
### Specify the number of quantiles. Get back the intervals.
pd.qcut(df['column'], n)

## Turn text into dates
pd.to_datetime(df['column'])

## Transpose
df.T

## Drop duplicates
df.drop_duplicates()

## Clip outlying values
df['column'].clip(0,100)
### Now everything is in 0 to 100
