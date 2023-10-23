# Assignment6BiGDATA

# Part-2: Manipulating Data using Python DataFrames (DF)

## 1. Open your Data File

Open your Data File (gapminder.tsv – available in CougarView with Assignment) using a text-editor and have a quick skim over it. Note the columns (i.e., Data Attributes) and the Size (number of Records).

- TSV (Tab-Separated Values) is a simple widely used (especially in data exchange) text-based file format, similar to CSV (Comma-Separated Values). In TSV, Records are separated by newlines, and values are separated by tabs.
- To upload the tsv data file to Colab:
  - Create a Github folder, assign it a name, and mark it as ‘public’
  - Upload the tsv file to the github newly created folder
  - Clone the folder to your Colab notebook - as in Cell[18] in the next notebook snapshot
  
[Take Snapshot#1]

## 2. Assign your data to a Pandas DataFrame (DF)

```python
df = pd.read_csv("DataScience_Course/gapminder.tsv", sep='\t')
```

Hint: Press shift+enter as a shortcut to execute a cell.

## 3. Execute the following commands, and guess their utility/output:

```python
df.head(5)
type(df)
df.shape
df.columns
df.dtypes
```

[Take Snapshot#2] (last five commands/cells output)

### a. Qst#1:

Explain the output of the shape command?

## 4. Data Extraction / Sub-setting

You can select/extract specific Columns or a Subset of Columns and assign them to a separate DF. This is very useful in Data Preparation, especially when your data has plenty of attributes/columns and most of them are irrelevant to your Data Analytics task. In such a case, you select only needed columns and create new DFs. Alike in our data, we might need to analyze if there is any correlation between Life-Expectancy and the GDP:

- Extracting a single column:
  ```python
  df1 = df['country']
  ```
  Check df1 contents using head function.

- Sub-setting by Column: Extracting a set of columns
  ```python
  df2 = df[['country', 'lifeExp', 'gdpPercap']]
  ```
  Check df2 contents using head function.

- Sub-setting by Rows: Extracting a set of Rows (a.k.a., Slicing)
  ```python
  df_rows = df.loc[35:40]
  ```
  Check df_rows contents using head function.

[Take Snapshot#3] (last 2 (df_rows) commands)

## 5. "Aggregate Functions" - "Grouping By" (similar to the SQL 'group by' statement)

Refreshing – SQL Background:

We want to do the same here with our NoSQL! Tables/Data. Let’s say, we want to compute the average life-Expectancy per country:

```python
df.groupby("country")["lifeExp"].mean()
```

### b. Qst#2:

Explain the output of the following command:
```python
df.groupby("country")["gdpPercap"].mean().mean()
```

### c. Qst#3:

What would be the command for computing the average lifeExp per year (for all countries, i.e., worldwide). Your command should output like what follows:

[Take Snapshot#3]

Note the lifeExp increase.
