# Pandas

## Constructing DataFrames
### Build a DataFrame by row
`df = pd.DataFrame([[1, 'a', 'alpha'], [2, 'b', 'beta']], columns = ['number', 'letter', 'greek'])`

### Copy a DataFrame
`df2 = df.copy(deep = True)`

### Load a DataFrame
`df = pd.read_csv('filename')`


## Summarizing DataFrames

### Get DataFrame attributes: metadata and statistics
`df.info()`
`df.describe()`

## See what's in the DataFrame
`df.sample(frac = 0.1)`
`df.head(10)`
`df.tail(20)`

### Get data frame counts
`len(df)`
`df['column'].unique()` ### unique values
`df['column'].nunique()` ### number of uniques
`df.value_counts()`

### Get DataFrame memory usage
`df.memory_usage()`


## Querying DataFrames

### Get rows 5-7, even if index isn't a number
`df.iloc[5:7]`

### Get rows where column is foo or bar
`df[df['column'].isin(['foo', 'bar'])]`

### Get the 5 largest and smallest
`df.nlargest(5, 'column')`
`df.nsmallest(5, 'column')`

### Match not equal to 5
`df['column'].ne(5)`

### Get the index position of the min or max
`s.idxmin()`
`s.idxmax()`

### Iterate over rows
`for idx, row in df.iterrows():`
`for row in df.itertuples()` ### Supposed to be very fast!

### Query, database style
`df.query('Column > 100')`

### Get values
`df.index.tolist()` ### Indices as a list
`list(df)` ### Column names as alist, same as `df.columns.tolist()`

### Get a subset of columns
`df[['column1', 'column2']]`

### Mapping
#### Map decimals in a series to $ with two decimal points
`s.map(lambda x: f'${x:.2}'`


## Sorting and Grouping
### Sort by
`df.sort_values('column', ascending = False)`

### Pivot
`df.groupby('column').count()`



## Manipulating DataFrame data

### Turn text into dates
`pd.to_datetime(df['column'])`

### Drop duplicates
`df.drop_duplicates()`

### Clip outlying values between 0 and 100
`df['column'].clip(0,100)`

## Fill NA values with 0
`df.fillna(0)`


## Changing DataFrame structure

### Encode labels
#### The first element is the label value, the second is the label name
`pd.factorize(df['column'])`

### Turn categories into numbers
`pd.get_dummies(df)`

### Cut into quantiles
#### Specify the number of quantiles. Get back the intervals.
`pd.qcut(df['column'], n)`

### Transpose
`df.T`


## Save

### Save as CSV or Excel
`df.to_csv('file.csv')`
`df.to_excel('file.xlsx')`
