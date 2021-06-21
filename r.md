# Iteration
* [mapply](https://www.r-bloggers.com/2019/12/mapply-and-map-in-r/)
   * like sapply but allows you to iterate through multiple vectors
   * first use of mapply
      > `# function parameters represent vector elements; should be in same order` \
      > `# in the example below, I was able to iterate through log2FoldChange and padj vectors` \
      > `G26.DEG.FIL$change <- mapply(` \
      > `                             function(lfc,padj){` \
      > `                                                ifelse(` \
      > `                                                       lfc > 0 & padj < 0.05,` \
      > `                                                       "up_regulated",` \
      > `                                                       ifelse(` \
      > `                                                              lfc < 0 & padj < 0.05,` \
      > `                                                              "down_regulated",` \
      > `                                                              "no_major_difference"` \
      > `                                                              )` \   
      > `                                                       )` \   
      > `                                                },` \  
      > `                             G26.DEG.FIL$log2FoldChange,` \
      > `                             G26.DEG.FIL$padj` \
      > `                             )` 
# Data Wrangling w/ Dataframes
* [find common elements between multiple vectors](https://stackoverflow.com/questions/3695677/how-to-find-common-elements-from-multiple-vectors)
   > `CORE.GENES <- Reduce(`\
   > `                     intersect,`\
   > `                     list(`\
   > `                          G26.UP[,1],`\
   > `                          DAB1A.UP[,1],`\
   > `                          SP7.UP[,1],`\
   > `                          SP245.UP[,1]`\
   > `                          )`\   
   > `                     )`
# Data Wrangling w/ Dataframes
* column-wise
   * [divide columns by certain column](https://stackoverflow.com/questions/47821241/how-to-divide-a-number-of-columns-by-one-column-in-r)
   * [divide each cell by sum of row/column](https://stackoverflow.com/questions/48140258/dividing-each-cell-in-a-data-set-by-the-column-sum-in-r)
* combining dataframes
   * use merge to combine dataframes by rows
      * [use merge and reduce to combine multiple dataframes](https://stackoverflow.com/questions/14096814/merging-a-lot-of-data-frames)
         > `# merged using values from first columns`\
         > `CORE.LOGFC <- Reduce(`\
         > `                     function(x,y) merge(x,y,all=TRUE),`\
         > `                     list(`\
         > `                          G26.UP[,c(1,3)],`\
         > `                          DAB1A.UP[,c(1,3)],`\
         > `                          SP7.UP[,c(1,3)],`\
         > `                          SP245.UP[,c(1,3)]`\
         > `                          )`\
         > `                     )` 

# Code Readability
* Pipe (%>%)
   * [Pipes In R Tutorial](https://www.datacamp.com/community/tutorials/pipe-r-tutorial)
   * first use of R pipe
      > `# prevents the creation of unnecessary variables` \
      > `# this is so much cleaner and easier to read` \
      > `merge(` \
      > `      LAB.COUNT,` \
      > `      NOVOGENE.COUNT,` \
      > `      by = "gene_id"` \
      > `      )[-1] %>%` \
      > `cor(method = "spearman") %>%` \
      > `round(2) %>%` \
      > `write.table(` \
      > `            "exp07-correlation_matrix.tsv",` \
      > `            sep = "\t",` \
      > `            quote = F` \
      > `            )`   
