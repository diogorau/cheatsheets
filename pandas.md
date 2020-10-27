# Pandas

## Encode labels
### The first element is the label value, the second is the label name
`pd.factorize(df['column'])`

## Turn categories into numbers
`pd.get_dummies(df)`

## Cut into quantiles
### Specify the number of quantiles. Get back the intervals.
`pd.qcut(df['column'], n)`

## Turn text into dates
`pd.to_datetime(df['column'])`

## Transpose
`df.T`

## Drop duplicates
`df.drop_duplicates()`

## Clip outlying values
`df['column'].clip(0,100)`
### Now everything is in 0 to 100

## Query
`df.query('Column > 100')`

## Get DataFrame memory usage
`df.memory_usage`

`df = pd.read_csv('filename')`

## Build a DataFrame by row
`df = pd.DataFrame([[1, 'a', 'alpha'], [2, 'b', 'beta']], columns = ['number', 'letter', 'greek'])`

## Copy a DataFrame
df2 = df.copy(deep = True)

## Save files
df.to_csv('file.csv')
df.to_excel('file.xlsx')

## Get data frame counts
`len(df)`
`df['column'].unique()` ### unique values
`df['column'].nunique()` ### number of uniques
`len['column'].value_counts()`

## Get DataFrame attributes
`df.info()` ### Metadata
`df.describe()` ### Statistics

## Get values
`df.index.tolist()` ### Indices as a list
`list(df)` ### Column names as alist, same as `df.columns.tolist()`

## Get a subset of columns
`df[['column1', 'column2']]`

## Get rows 5-7, even if index isn't a number
`df.iloc[5:7]`

## Get rows where column is foo or bar
`df[df['column'].isin(['foo', 'bar'])]`

## Sort by
`df.sort_values('column', ascending = False)`

## Pivot
`df.groupby('column').count()`

## Fill NA values with 0
`df.fillna(0)`

## See what's in the DataFrame
`df.sample(frac = 0.1)`
`df.head(10)`
`df.tail(20)`

## Iterate over rows
`for idx, row in df.iterrows():`
`for row in df.itertuples()` ### Supposed to be very fast!
