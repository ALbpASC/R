# R
## Merge multiple dataframes

# usage: 
merge_multiple_df(df_list, by, keep.common = TRUE, addNA = FALSE)

# Inputs

1) df_list: A list of dataframes to be merged

2) by: Character vector of column names to merge on. The key column in each dataframe should have the same name. If no columns are specified, the function will try to match the columns by name.

3) keep.common: Logical flag to control the merging of columns with the same name. If set to TRUE, columns with the same name will only be kept once. If set to FALSE, all columns will be kept separate, with an appendix indicating which dataframe they came from.
4) addNA: Logical flag to indicate whether missing values in the merged dataframes should be filled with NA. If set to TRUE, missing values in the merged dataframes will be filled with NA. If set to FALSE, missing values will not be filled.

# Output

Returns a single dataframe that is the result of merging the input dataframes. The columns will be merged based on the options specified by the by, keep.common, and addNA inputs.
