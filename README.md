# README.md

# Scommersonii_genome

## **The haplotype-resolved and T2T genome assembly of Solanum commersonii**

### Assembly and annotation datasets

CM1.0/CM1.0_MCScanX.allele.tsv: allele table  
CM1.0/CM1.0_annotation.gff3.gz: Gene annotation file  
CM1.0/CM1.0_function.tsv.gz: Gene functional annotation file  
Releases/CM1.0_Hap1.assembly.fasta.gz: Solanum commersonii haplotype 1 genome sequence file  
Releases/CM1.0_Hap2.assembly.fasta.gz: Solanum commersonii haplotype 2 genome sequence file

### enrichment database

The KEGG/GO datasets in [https://figshare.com/articles/dataset/enrichment_database/26129590](https://figshare.com/articles/dataset/enrichment_database/26129590).

　　‍

KEGGdatabase\_ScomD.Rdata is diploid KEGG annotation and KEGGdatabase\_ScomH1.Rdata is Haplotype 1 KEGG annotation. org.Scommersonii.eg.db.tar.gz is diploid GOannotation and org.ScommersoniiHap1.eg.db.tar.gz is Haplotype 1 GO annotation.

　　‍

You can using these datasets in R:

```R
#for KEGG enrichment analysis
#genes is your target genelist
library(clusterProfiler)
load(file = '/your/path/to/KEGGdatabase_ScomH1.Rdata')
KEGGres <- enricher(genes,
                TERM2GENE = pathway2genes, 
                TERM2NAME = pathway2name,
                qvalueCutoff =1, pvalueCutoff  = 1)

#for GO enrichment analysis
install.packages('/your/path/to/org.ScommersoniiHap1.eg.db', repos=NULL, type="source")
GOres <- enrichGO(gene=genes,
                OrgDb=org.ScommersoniiHap1.eg.db,
                keyType="GID",
                ont="ALL",
                qvalueCutoff =1, pvalueCutoff  = 1)
```
