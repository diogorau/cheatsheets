# Pandas

## Constructing DataFrames
### Build a DataFrame by row
`df = pd.DataFrame([[1, 'a', 'alpha'], [2, 'b', 'beta']], columns = ['number', 'letter', 'greek'])`

### Copy a DataFrame
`df2 = df.copy(deep = True)`

### Load a DataFrame
`df = pd.read_csv('filename')`
`df = pd.read_excel('https://github.com/diogorau/foo.xlsx', sheet_name = 'Sheet 2')`
`df = pd.read_clipboard(sep = '\t')`
`df = pd.read_csv('dictionary', header=0, names=['word', 'count'], sep=' ')`

## Summarizing DataFrames

### Get DataFrame attributes: metadata and statistics
`df.shape`
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
#### The latter is supposed to be very fast
`for idx, row in df.iterrows():`
`for row in df.itertuples()`

### Query, database style
`df.query('Column > 100')`

### Get indices as a list
`df.index.tolist()`
### Get column names as a list, same as `df.columns.tolist()`
`list(df)`

### Get a subset of columns
`df[['column1', 'column2']]`

### Mapping and applying
#### Mapping works on series, but applying works on dataframes and series
#### Map decimals in a series to $ with two decimal points
`s.map(lambda x: f'${x:.2})'`
`df['column'].apply(lambda x: f(x))`

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

### Make a pivot table of, say populations by country
#### Besides sum, we could use mean, max, min, among others
`df.pivot_table(index = 'Country', values = 'Population', aggfunc = 'sum')`

### Merge in everything in a lookup table, like an Excel VLOOKUP
`pd.merge(df, df_lookup, how = 'left', on = 'column')`

### Encode labels
#### The first element is the label value, the second is the label name
`pd.factorize(df['column'])`

### Turn categories into numbers
`pd.get_dummies(df)`

### Cut into quantiles
#### Specify the number of quantiles. Get back the intervals.
`pd.qcut(df['column'], n)`

#### Cut into 5 bins or into designated bins
`pd.cut(df['column'], bins = 5)
`pd.cut(df['column'], bins = [0., 1.5, 3., 10., np.inf], labels = ['S','M','L','XL'])


### Transpose
`df.T`


## Save

### Save as CSV or Excel
`df.to_csv('file.csv')`
`df.to_excel('file.xlsx')`


## Plotting

### Display a histogram
`df.hist()`
