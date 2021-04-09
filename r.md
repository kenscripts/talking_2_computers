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
          > `            )` \   
