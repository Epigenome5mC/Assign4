`install.packages("shiny")
install.packages("ggplot2")
library("ggplot2")
install.packages("plotly")
library("plotly") `



setwd("~/Desktop/Programming_2018/mygraph2/bin/")
getwd()
list.files()
mygenes <- read.csv('gene_dist_head.tsv', header= TRUE, sep = "\t")

summary(mygenes)
mygenes$feature
colnames(mygenes)
rownames(mygenes)
mygenes[,c(2,4)]
autosomes<-c("1","2","3","4","5","6","7","8","9","10",
             "11","12","13","14","15","16","17","18","19","20","21","22")
             
genes<- mygenes[ which(mygenes$chr %in% autosomes), ] 

genes$chr <- factor(genes$chr, levels = autosomes)

ggplot(data = genes) +  geom_bar(mapping = aes(x = chr, fill = feature), width = 1)

ggplot(data = genes) +
  geom_bar(mapping = aes(x = feature))

ggplot(data = genes) +
  geom_bar(mapping = aes(x = chr, fill = feature))

ggplot(data = genes) +
  geom_bar(mapping = aes(x = chr, fill = feature), width = 1) +
  coord_polar()

devtools::install_github('hadley/ggplot2')

#You will need to restart R at this point.

p <- ggplot(data = genes) +
  geom_bar(mapping = aes(x = chr, fill = feature), width = 1)

ggplotly(p) 



