# Custom functions for R

## Merge (multiple) dataframes

# Function Signature: 
merge_df(df_list, by, keep.common = TRUE, addNA = FALSE)

# Inputs

1) df_list: A list of dataframes to be merged

2) by: Character vector of column names to merge on. The key column in each dataframe should have the same name. If no columns are specified, the function will try to match the columns by name.

3) keep.common: Logical flag to control the merging of columns with the same name. If set to TRUE, columns with the same name will only be kept once. If set to FALSE, all columns will be kept separate, with an appendix indicating which dataframe they came from.
4) addNA: Logical flag to indicate whether missing values in the merged dataframes should be filled with NA. If set to TRUE, missing values in the merged dataframes will be filled with NA. If set to FALSE, missing values will not be filled.

# Output

Returns a single dataframe that is the result of merging the input dataframes. The columns will be merged based on the options specified by the by, keep.common, and addNA inputs.

## Collapse phyloseq by taxonomy ranks

# Function signature

collapse_taxa(physeq, ranks = NULL)

## Usage

 1. Use all available ranks in the phyloseq object
physeq_taxa.list <- collapse_taxa(my_physeq)

The returned list might have elements like:
 - "physeq.kingdom", "physeq.phylum", "physeq.class", etc.
 - "physeq.asv" (the original object)

 2. Specify only certain ranks
desired_ranks <- c("Phylum", "Class", "Order", "Family", "Genus", "Species")
physeq_taxa.list <- collapse_taxa(my_physeq, ranks = desired_ranks)

 Check what's in the returned list
names(collapsed_subset)
 e.g. "physeq.phylum", "physeq.class", ..., "physeq.species", "physeq.asv"

## Output
 3. Inspect one of the collapsed objects
ntaxa(physeq_taxa.list[["physeq.genus"]])
 This shows the number of taxa after collapsing at the genus level.

 4. If needed, continue downstream analysis
 For example, subset_samples or prune_taxa on each collapsed object
