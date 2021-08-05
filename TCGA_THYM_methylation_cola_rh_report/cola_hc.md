cola Report for Hierarchical Partitioning - 'TCGA_THYM_methylation'
==================

**Date**: 2021-07-22 16:22:51 CEST, **cola version**: 1.9.4

----------------------------------------------------------------

<style type='text/css'>

body, td, th {
   font-family: Arial,Helvetica,sans-serif;
   background-color: white;
   font-size: 13px;
  max-width: 800px;
  margin: auto;
  margin-left:210px;
  padding: 0px 10px 0px 10px;
  border-left: 1px solid #EEEEEE;
  line-height: 150%;
}

tt, code, pre {
   font-family: 'DejaVu Sans Mono', 'Droid Sans Mono', 'Lucida Console', Consolas, Monaco, 

monospace;
}

h1 {
   font-size:2.2em;
}

h2 {
   font-size:1.8em;
}

h3 {
   font-size:1.4em;
}

h4 {
   font-size:1.0em;
}

h5 {
   font-size:0.9em;
}

h6 {
   font-size:0.8em;
}

a {
  text-decoration: none;
  color: #0366d6;
}

a:hover {
  text-decoration: underline;
}

a:visited {
   color: #0366d6;
}

pre, img {
  max-width: 100%;
}
pre {
  overflow-x: auto;
}
pre code {
   display: block; padding: 0.5em;
}

code {
  font-size: 92%;
  border: 1px solid #ccc;
}

code[class] {
  background-color: #F8F8F8;
}

table, td, th {
  border: 1px solid #ccc;
}

blockquote {
   color:#666666;
   margin:0;
   padding-left: 1em;
   border-left: 0.5em #EEE solid;
}

hr {
   height: 0px;
   border-bottom: none;
   border-top-width: thin;
   border-top-style: dotted;
   border-top-color: #999999;
}

@media print {
   * {
      background: transparent !important;
      color: black !important;
      filter:none !important;
      -ms-filter: none !important;
   }

   body {
      font-size:12pt;
      max-width:100%;
   }

   a, a:visited {
      text-decoration: underline;
   }

   hr {
      visibility: hidden;
      page-break-before: always;
   }

   pre, blockquote {
      padding-right: 1em;
      page-break-inside: avoid;
   }

   tr, img {
      page-break-inside: avoid;
   }

   img {
      max-width: 100% !important;
   }

   @page :left {
      margin: 15mm 20mm 15mm 10mm;
   }

   @page :right {
      margin: 15mm 10mm 15mm 20mm;
   }

   p, h2, h3 {
      orphans: 3; widows: 3;
   }

   h2, h3 {
      page-break-after: avoid;
   }
}
</style>




## Summary



First the variable is renamed to `res_rh`.


```r
res_rh = rh
```



The partition hierarchy and all available functions which can be applied to `res_rh` object.


```r
res_rh
```

```
#> A 'HierarchicalPartition' object with 4 combinations of top-value methods and partitioning methods.
#>   On a matrix with 376018 rows and 126 columns.
#>   Performed in total 29400 partitions.
#>   There are 15 groups under the following parameters:
#>     - min_samples: 6
#>     - mean_silhouette_cutoff: 0.9
#>     - min_n_signatures: 1000 (signatures are selected based on:)
#>       - fdr_cutoff: 0.05
#>       - group_diff: 0.25
#> 
#> Hierarchy of the partition:
#>   0, 126 cols
#>   |-- 01, 69 cols, 3265 signatures
#>   |   |-- 011, 33 cols, 601 signatures (c)
#>   |   `-- 012, 36 cols, 8310 signatures
#>   |       |-- 0121, 11 cols (b)
#>   |       |-- 0122, 14 cols, 330 signatures (c)
#>   |       |-- 0123, 3 cols (b)
#>   |       `-- 0124, 8 cols (b)
#>   |-- 02, 19 cols, 4048 signatures
#>   |   |-- 021, 5 cols (b)
#>   |   |-- 022, 5 cols (b)
#>   |   |-- 023, 4 cols (b)
#>   |   `-- 024, 5 cols (b)
#>   |-- 03, 24 cols, 10559 signatures
#>   |   |-- 031, 8 cols (b)
#>   |   |-- 032, 8 cols (b)
#>   |   |-- 033, 5 cols (b)
#>   |   `-- 034, 3 cols (b)
#>   `-- 04, 14 cols, 7591 signatures
#>       |-- 041, 7 cols (b)
#>       `-- 042, 7 cols (b)
#> Stop reason:
#>   b) Subgroup had too few columns.
#>   c) There were too few signatures.
#> 
#> Following methods can be applied to this 'HierarchicalPartition' object:
#>  [1] "all_leaves"            "all_nodes"             "cola_report"           "collect_classes"      
#>  [5] "colnames"              "compare_signatures"    "dimension_reduction"   "functional_enrichment"
#>  [9] "get_anno_col"          "get_anno"              "get_children_nodes"    "get_classes"          
#> [13] "get_matrix"            "get_signatures"        "is_leaf_node"          "max_depth"            
#> [17] "merge_node"            "ncol"                  "node_info"             "node_level"           
#> [21] "nrow"                  "rownames"              "show"                  "split_node"           
#> [25] "suggest_best_k"        "test_to_known_factors" "top_rows_heatmap"      "top_rows_overlap"     
#> 
#> You can get result for a single node by e.g. object["01"]
```

The call of `hierarchical_partition()` was:


```
#> hierarchical_partition(data = mat, top_n = 1000, top_value_method = c("SD", "ATC"), 
#>     partition_method = c("kmeans", "skmeans"), subset = 500, group_diff = 0.25, min_n_signatures = 1000, 
#>     filter_fun = function(mat) {
#>         s = rowSds(mat)
#>         order(-s)[1:30000]
#>     }, max_k = 8, scale_rows = FALSE, cores = 4)
```

Dimension of the input matrix:


```r
mat = get_matrix(res_rh)
dim(mat)
```

```
#> [1] 376018    126
```

All the methods that were tried:


```r
res_rh@param$combination_method
```

```
#> [[1]]
#> [1] "SD"     "kmeans"
#> 
#> [[2]]
#> [1] "ATC"    "kmeans"
#> 
#> [[3]]
#> [1] "SD"      "skmeans"
#> 
#> [[4]]
#> [1] "ATC"     "skmeans"
```

### Density distribution

The density distribution for each sample is visualized as one column in the following heatmap.
The clustering is based on the distance which is the Kolmogorov-Smirnov statistic between two distributions.




```r
library(ComplexHeatmap)
densityHeatmap(mat, ylab = "value", cluster_columns = TRUE, show_column_names = FALSE,
    mc.cores = 1)
```

![plot of chunk density-heatmap](figure_cola/density-heatmap-1.png)



Some values about the hierarchy:


```r
all_nodes(res_rh)
```

```
#>  [1] "0"    "01"   "011"  "012"  "0121" "0122" "0123" "0124" "02"   "021"  "022"  "023"  "024" 
#> [14] "03"   "031"  "032"  "033"  "034"  "04"   "041"  "042"
```

```r
all_leaves(res_rh)
```

```
#>  [1] "011"  "0121" "0122" "0123" "0124" "021"  "022"  "023"  "024"  "031"  "032"  "033"  "034" 
#> [14] "041"  "042"
```

```r
node_info(res_rh)
```

```
#>      id best_method depth best_k n_columns n_signatures p_signatures is_leaf
#> 1     0  SD:skmeans     1      4       126        54876     0.145940   FALSE
#> 2    01   SD:kmeans     2      2        69         3265     0.008683   FALSE
#> 3   011 ATC:skmeans     3      4        33          601     0.001598    TRUE
#> 4   012  ATC:kmeans     3      4        36         8310     0.022100   FALSE
#> 5  0121 not applied     4     NA        11           NA           NA    TRUE
#> 6  0122 ATC:skmeans     4      3        14          330     0.000878    TRUE
#> 7  0123 not applied     4     NA         3           NA           NA    TRUE
#> 8  0124 not applied     4     NA         8           NA           NA    TRUE
#> 9    02   SD:kmeans     2      4        19         4048     0.010765   FALSE
#> 10  021 not applied     3     NA         5           NA           NA    TRUE
#> 11  022 not applied     3     NA         5           NA           NA    TRUE
#> 12  023 not applied     3     NA         4           NA           NA    TRUE
#> 13  024 not applied     3     NA         5           NA           NA    TRUE
#> 14   03  SD:skmeans     2      4        24        10559     0.028081   FALSE
#> 15  031 not applied     3     NA         8           NA           NA    TRUE
#> 16  032 not applied     3     NA         8           NA           NA    TRUE
#> 17  033 not applied     3     NA         5           NA           NA    TRUE
#> 18  034 not applied     3     NA         3           NA           NA    TRUE
#> 19   04 ATC:skmeans     2      2        14         7591     0.020188   FALSE
#> 20  041 not applied     3     NA         7           NA           NA    TRUE
#> 21  042 not applied     3     NA         7           NA           NA    TRUE
```

In the output from `node_info()`, there are the following columns:

- `id`: The node id.
- `best_method`: The best method selected.
- `depth`: Depth of the node in the hierarchy.
- `best_k`: Best number of groups of the partition on that node.
- `n_columns`: Number of columns in the submatrix.
- `n_signatures`: Number of signatures with the `best_k`.
- `p_signatures`: Proportion of hte signatures in total number of rows in the matrix.
- `is_leaf`: Whether the node is a leaf.

Labels of nodes are encoded in a special way. The number of digits
correspond to the depth of the node in the hierarchy and the value of the
digits correspond to the index of the subgroup in the current node, E.g. a label
of “012” means the node is the second subgroup of the partition which is the
first subgroup of the root node.

### Suggest the best k



Following table shows the best `k` (number of partitions) for each node in the
partition hierarchy. Clicking on the node name in the table goes to the
corresponding section for the partitioning on that node.

[The cola vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13)
explains the definition of the metrics used for determining the best
number of partitions.



```r
suggest_best_k(res_rh)
```


|Node                |Best method                                         |Is leaf   |Best k |1-PAC |Mean silhouette |Concordance | #samples|   |
|:-------------------|:---------------------------------------------------|:---------|:------|:-----|:---------------|:-----------|--------:|:--|
|[Node0](#Node0)     |SD:skmeans                                          |          |5      |0.99  |0.95            |0.96        |      126|** |
|[Node01](#Node01)   |SD:kmeans                                           |          |2      |1.00  |1.00            |1.00        |       69|** |
|Node011-leaf        |ATC:skmeans                                         |✓ (&#99;) |5      |0.92  |0.88            |0.94        |       33|*  |
|[Node012](#Node012) |ATC:kmeans                                          |          |7      |0.92  |0.94            |0.90        |       36|*  |
|Node0121-leaf       |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |       11|   |
|Node0122-leaf       |ATC:skmeans                                         |✓ (&#99;) |3      |1.00  |1.00            |1.00        |       14|** |
|Node0123-leaf       |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        3|   |
|Node0124-leaf       |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        8|   |
|[Node02](#Node02)   |SD:kmeans                                           |          |4      |0.91  |0.96            |0.95        |       19|*  |
|Node021-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        5|   |
|Node022-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        5|   |
|Node023-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        4|   |
|Node024-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        5|   |
|[Node03](#Node03)   |SD:skmeans                                          |          |4      |1.00  |1.00            |1.00        |       24|** |
|Node031-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        8|   |
|Node032-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        8|   |
|Node033-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        5|   |
|Node034-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        3|   |
|[Node04](#Node04)   |ATC:skmeans                                         |          |7      |0.90  |0.72            |0.97        |       14|*  |
|Node041-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        7|   |
|Node042-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        7|   |


Stop reason: b) Subgroup had too few columns. c) There were too few signatures. 

\*\*: 1-PAC > 0.95, \*: 1-PAC > 0.9


### Partition hierarchy

The nodes of the hierarchy can be merged by setting the `merge_node` parameters. Here we 
control the hierarchy with the `min_n_signatures` parameter. The value of `min_n_signatures` is
from `node_info()`.





<style type='text/css'>



.ui-helper-hidden {
	display: none;
}
.ui-helper-hidden-accessible {
	border: 0;
	clip: rect(0 0 0 0);
	height: 1px;
	margin: -1px;
	overflow: hidden;
	padding: 0;
	position: absolute;
	width: 1px;
}
.ui-helper-reset {
	margin: 0;
	padding: 0;
	border: 0;
	outline: 0;
	line-height: 1.3;
	text-decoration: none;
	font-size: 100%;
	list-style: none;
}
.ui-helper-clearfix:before,
.ui-helper-clearfix:after {
	content: "";
	display: table;
	border-collapse: collapse;
}
.ui-helper-clearfix:after {
	clear: both;
}
.ui-helper-zfix {
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	position: absolute;
	opacity: 0;
	filter:Alpha(Opacity=0); 
}

.ui-front {
	z-index: 100;
}



.ui-state-disabled {
	cursor: default !important;
	pointer-events: none;
}



.ui-icon {
	display: inline-block;
	vertical-align: middle;
	margin-top: -.25em;
	position: relative;
	text-indent: -99999px;
	overflow: hidden;
	background-repeat: no-repeat;
}

.ui-widget-icon-block {
	left: 50%;
	margin-left: -8px;
	display: block;
}




.ui-widget-overlay {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}
.ui-accordion .ui-accordion-header {
	display: block;
	cursor: pointer;
	position: relative;
	margin: 2px 0 0 0;
	padding: .5em .5em .5em .7em;
	font-size: 100%;
}
.ui-accordion .ui-accordion-content {
	padding: 1em 2.2em;
	border-top: 0;
	overflow: auto;
}
.ui-autocomplete {
	position: absolute;
	top: 0;
	left: 0;
	cursor: default;
}
.ui-menu {
	list-style: none;
	padding: 0;
	margin: 0;
	display: block;
	outline: 0;
}
.ui-menu .ui-menu {
	position: absolute;
}
.ui-menu .ui-menu-item {
	margin: 0;
	cursor: pointer;
	
	list-style-image: url("data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7");
}
.ui-menu .ui-menu-item-wrapper {
	position: relative;
	padding: 3px 1em 3px .4em;
}
.ui-menu .ui-menu-divider {
	margin: 5px 0;
	height: 0;
	font-size: 0;
	line-height: 0;
	border-width: 1px 0 0 0;
}
.ui-menu .ui-state-focus,
.ui-menu .ui-state-active {
	margin: -1px;
}


.ui-menu-icons {
	position: relative;
}
.ui-menu-icons .ui-menu-item-wrapper {
	padding-left: 2em;
}


.ui-menu .ui-icon {
	position: absolute;
	top: 0;
	bottom: 0;
	left: .2em;
	margin: auto 0;
}


.ui-menu .ui-menu-icon {
	left: auto;
	right: 0;
}
.ui-button {
	padding: .4em 1em;
	display: inline-block;
	position: relative;
	line-height: normal;
	margin-right: .1em;
	cursor: pointer;
	vertical-align: middle;
	text-align: center;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;

	
	overflow: visible;
}

.ui-button,
.ui-button:link,
.ui-button:visited,
.ui-button:hover,
.ui-button:active {
	text-decoration: none;
}


.ui-button-icon-only {
	width: 2em;
	box-sizing: border-box;
	text-indent: -9999px;
	white-space: nowrap;
}


input.ui-button.ui-button-icon-only {
	text-indent: 0;
}


.ui-button-icon-only .ui-icon {
	position: absolute;
	top: 50%;
	left: 50%;
	margin-top: -8px;
	margin-left: -8px;
}

.ui-button.ui-icon-notext .ui-icon {
	padding: 0;
	width: 2.1em;
	height: 2.1em;
	text-indent: -9999px;
	white-space: nowrap;

}

input.ui-button.ui-icon-notext .ui-icon {
	width: auto;
	height: auto;
	text-indent: 0;
	white-space: normal;
	padding: .4em 1em;
}



input.ui-button::-moz-focus-inner,
button.ui-button::-moz-focus-inner {
	border: 0;
	padding: 0;
}
.ui-controlgroup {
	vertical-align: middle;
	display: inline-block;
}
.ui-controlgroup > .ui-controlgroup-item {
	float: left;
	margin-left: 0;
	margin-right: 0;
}
.ui-controlgroup > .ui-controlgroup-item:focus,
.ui-controlgroup > .ui-controlgroup-item.ui-visual-focus {
	z-index: 9999;
}
.ui-controlgroup-vertical > .ui-controlgroup-item {
	display: block;
	float: none;
	width: 100%;
	margin-top: 0;
	margin-bottom: 0;
	text-align: left;
}
.ui-controlgroup-vertical .ui-controlgroup-item {
	box-sizing: border-box;
}
.ui-controlgroup .ui-controlgroup-label {
	padding: .4em 1em;
}
.ui-controlgroup .ui-controlgroup-label span {
	font-size: 80%;
}
.ui-controlgroup-horizontal .ui-controlgroup-label + .ui-controlgroup-item {
	border-left: none;
}
.ui-controlgroup-vertical .ui-controlgroup-label + .ui-controlgroup-item {
	border-top: none;
}
.ui-controlgroup-horizontal .ui-controlgroup-label.ui-widget-content {
	border-right: none;
}
.ui-controlgroup-vertical .ui-controlgroup-label.ui-widget-content {
	border-bottom: none;
}


.ui-controlgroup-vertical .ui-spinner-input {

	
	width: 75%;
	width: calc( 100% - 2.4em );
}
.ui-controlgroup-vertical .ui-spinner .ui-spinner-up {
	border-top-style: solid;
}

.ui-checkboxradio-label .ui-icon-background {
	box-shadow: inset 1px 1px 1px #ccc;
	border-radius: .12em;
	border: none;
}
.ui-checkboxradio-radio-label .ui-icon-background {
	width: 16px;
	height: 16px;
	border-radius: 1em;
	overflow: visible;
	border: none;
}
.ui-checkboxradio-radio-label.ui-checkboxradio-checked .ui-icon,
.ui-checkboxradio-radio-label.ui-checkboxradio-checked:hover .ui-icon {
	background-image: none;
	width: 8px;
	height: 8px;
	border-width: 4px;
	border-style: solid;
}
.ui-checkboxradio-disabled {
	pointer-events: none;
}
.ui-datepicker {
	width: 17em;
	padding: .2em .2em 0;
	display: none;
}
.ui-datepicker .ui-datepicker-header {
	position: relative;
	padding: .2em 0;
}
.ui-datepicker .ui-datepicker-prev,
.ui-datepicker .ui-datepicker-next {
	position: absolute;
	top: 2px;
	width: 1.8em;
	height: 1.8em;
}
.ui-datepicker .ui-datepicker-prev-hover,
.ui-datepicker .ui-datepicker-next-hover {
	top: 1px;
}
.ui-datepicker .ui-datepicker-prev {
	left: 2px;
}
.ui-datepicker .ui-datepicker-next {
	right: 2px;
}
.ui-datepicker .ui-datepicker-prev-hover {
	left: 1px;
}
.ui-datepicker .ui-datepicker-next-hover {
	right: 1px;
}
.ui-datepicker .ui-datepicker-prev span,
.ui-datepicker .ui-datepicker-next span {
	display: block;
	position: absolute;
	left: 50%;
	margin-left: -8px;
	top: 50%;
	margin-top: -8px;
}
.ui-datepicker .ui-datepicker-title {
	margin: 0 2.3em;
	line-height: 1.8em;
	text-align: center;
}
.ui-datepicker .ui-datepicker-title select {
	font-size: 1em;
	margin: 1px 0;
}
.ui-datepicker select.ui-datepicker-month,
.ui-datepicker select.ui-datepicker-year {
	width: 45%;
}
.ui-datepicker table {
	width: 100%;
	font-size: .9em;
	border-collapse: collapse;
	margin: 0 0 .4em;
}
.ui-datepicker th {
	padding: .7em .3em;
	text-align: center;
	font-weight: bold;
	border: 0;
}
.ui-datepicker td {
	border: 0;
	padding: 1px;
}
.ui-datepicker td span,
.ui-datepicker td a {
	display: block;
	padding: .2em;
	text-align: right;
	text-decoration: none;
}
.ui-datepicker .ui-datepicker-buttonpane {
	background-image: none;
	margin: .7em 0 0 0;
	padding: 0 .2em;
	border-left: 0;
	border-right: 0;
	border-bottom: 0;
}
.ui-datepicker .ui-datepicker-buttonpane button {
	float: right;
	margin: .5em .2em .4em;
	cursor: pointer;
	padding: .2em .6em .3em .6em;
	width: auto;
	overflow: visible;
}
.ui-datepicker .ui-datepicker-buttonpane button.ui-datepicker-current {
	float: left;
}


.ui-datepicker.ui-datepicker-multi {
	width: auto;
}
.ui-datepicker-multi .ui-datepicker-group {
	float: left;
}
.ui-datepicker-multi .ui-datepicker-group table {
	width: 95%;
	margin: 0 auto .4em;
}
.ui-datepicker-multi-2 .ui-datepicker-group {
	width: 50%;
}
.ui-datepicker-multi-3 .ui-datepicker-group {
	width: 33.3%;
}
.ui-datepicker-multi-4 .ui-datepicker-group {
	width: 25%;
}
.ui-datepicker-multi .ui-datepicker-group-last .ui-datepicker-header,
.ui-datepicker-multi .ui-datepicker-group-middle .ui-datepicker-header {
	border-left-width: 0;
}
.ui-datepicker-multi .ui-datepicker-buttonpane {
	clear: left;
}
.ui-datepicker-row-break {
	clear: both;
	width: 100%;
	font-size: 0;
}


.ui-datepicker-rtl {
	direction: rtl;
}
.ui-datepicker-rtl .ui-datepicker-prev {
	right: 2px;
	left: auto;
}
.ui-datepicker-rtl .ui-datepicker-next {
	left: 2px;
	right: auto;
}
.ui-datepicker-rtl .ui-datepicker-prev:hover {
	right: 1px;
	left: auto;
}
.ui-datepicker-rtl .ui-datepicker-next:hover {
	left: 1px;
	right: auto;
}
.ui-datepicker-rtl .ui-datepicker-buttonpane {
	clear: right;
}
.ui-datepicker-rtl .ui-datepicker-buttonpane button {
	float: left;
}
.ui-datepicker-rtl .ui-datepicker-buttonpane button.ui-datepicker-current,
.ui-datepicker-rtl .ui-datepicker-group {
	float: right;
}
.ui-datepicker-rtl .ui-datepicker-group-last .ui-datepicker-header,
.ui-datepicker-rtl .ui-datepicker-group-middle .ui-datepicker-header {
	border-right-width: 0;
	border-left-width: 1px;
}


.ui-datepicker .ui-icon {
	display: block;
	text-indent: -99999px;
	overflow: hidden;
	background-repeat: no-repeat;
	left: .5em;
	top: .3em;
}
.ui-dialog {
	position: absolute;
	top: 0;
	left: 0;
	padding: .2em;
	outline: 0;
}
.ui-dialog .ui-dialog-titlebar {
	padding: .4em 1em;
	position: relative;
}
.ui-dialog .ui-dialog-title {
	float: left;
	margin: .1em 0;
	white-space: nowrap;
	width: 90%;
	overflow: hidden;
	text-overflow: ellipsis;
}
.ui-dialog .ui-dialog-titlebar-close {
	position: absolute;
	right: .3em;
	top: 50%;
	width: 20px;
	margin: -10px 0 0 0;
	padding: 1px;
	height: 20px;
}
.ui-dialog .ui-dialog-content {
	position: relative;
	border: 0;
	padding: .5em 1em;
	background: none;
	overflow: auto;
}
.ui-dialog .ui-dialog-buttonpane {
	text-align: left;
	border-width: 1px 0 0 0;
	background-image: none;
	margin-top: .5em;
	padding: .3em 1em .5em .4em;
}
.ui-dialog .ui-dialog-buttonpane .ui-dialog-buttonset {
	float: right;
}
.ui-dialog .ui-dialog-buttonpane button {
	margin: .5em .4em .5em 0;
	cursor: pointer;
}
.ui-dialog .ui-resizable-n {
	height: 2px;
	top: 0;
}
.ui-dialog .ui-resizable-e {
	width: 2px;
	right: 0;
}
.ui-dialog .ui-resizable-s {
	height: 2px;
	bottom: 0;
}
.ui-dialog .ui-resizable-w {
	width: 2px;
	left: 0;
}
.ui-dialog .ui-resizable-se,
.ui-dialog .ui-resizable-sw,
.ui-dialog .ui-resizable-ne,
.ui-dialog .ui-resizable-nw {
	width: 7px;
	height: 7px;
}
.ui-dialog .ui-resizable-se {
	right: 0;
	bottom: 0;
}
.ui-dialog .ui-resizable-sw {
	left: 0;
	bottom: 0;
}
.ui-dialog .ui-resizable-ne {
	right: 0;
	top: 0;
}
.ui-dialog .ui-resizable-nw {
	left: 0;
	top: 0;
}
.ui-draggable .ui-dialog-titlebar {
	cursor: move;
}
.ui-draggable-handle {
	-ms-touch-action: none;
	touch-action: none;
}
.ui-resizable {
	position: relative;
}
.ui-resizable-handle {
	position: absolute;
	font-size: 0.1px;
	display: block;
	-ms-touch-action: none;
	touch-action: none;
}
.ui-resizable-disabled .ui-resizable-handle,
.ui-resizable-autohide .ui-resizable-handle {
	display: none;
}
.ui-resizable-n {
	cursor: n-resize;
	height: 7px;
	width: 100%;
	top: -5px;
	left: 0;
}
.ui-resizable-s {
	cursor: s-resize;
	height: 7px;
	width: 100%;
	bottom: -5px;
	left: 0;
}
.ui-resizable-e {
	cursor: e-resize;
	width: 7px;
	right: -5px;
	top: 0;
	height: 100%;
}
.ui-resizable-w {
	cursor: w-resize;
	width: 7px;
	left: -5px;
	top: 0;
	height: 100%;
}
.ui-resizable-se {
	cursor: se-resize;
	width: 12px;
	height: 12px;
	right: 1px;
	bottom: 1px;
}
.ui-resizable-sw {
	cursor: sw-resize;
	width: 9px;
	height: 9px;
	left: -5px;
	bottom: -5px;
}
.ui-resizable-nw {
	cursor: nw-resize;
	width: 9px;
	height: 9px;
	left: -5px;
	top: -5px;
}
.ui-resizable-ne {
	cursor: ne-resize;
	width: 9px;
	height: 9px;
	right: -5px;
	top: -5px;
}
.ui-progressbar {
	height: 2em;
	text-align: left;
	overflow: hidden;
}
.ui-progressbar .ui-progressbar-value {
	margin: -1px;
	height: 100%;
}
.ui-progressbar .ui-progressbar-overlay {
	background: url("data:image/gif;base64,R0lGODlhKAAoAIABAAAAAP///yH/C05FVFNDQVBFMi4wAwEAAAAh+QQJAQABACwAAAAAKAAoAAACkYwNqXrdC52DS06a7MFZI+4FHBCKoDeWKXqymPqGqxvJrXZbMx7Ttc+w9XgU2FB3lOyQRWET2IFGiU9m1frDVpxZZc6bfHwv4c1YXP6k1Vdy292Fb6UkuvFtXpvWSzA+HycXJHUXiGYIiMg2R6W459gnWGfHNdjIqDWVqemH2ekpObkpOlppWUqZiqr6edqqWQAAIfkECQEAAQAsAAAAACgAKAAAApSMgZnGfaqcg1E2uuzDmmHUBR8Qil95hiPKqWn3aqtLsS18y7G1SzNeowWBENtQd+T1JktP05nzPTdJZlR6vUxNWWjV+vUWhWNkWFwxl9VpZRedYcflIOLafaa28XdsH/ynlcc1uPVDZxQIR0K25+cICCmoqCe5mGhZOfeYSUh5yJcJyrkZWWpaR8doJ2o4NYq62lAAACH5BAkBAAEALAAAAAAoACgAAAKVDI4Yy22ZnINRNqosw0Bv7i1gyHUkFj7oSaWlu3ovC8GxNso5fluz3qLVhBVeT/Lz7ZTHyxL5dDalQWPVOsQWtRnuwXaFTj9jVVh8pma9JjZ4zYSj5ZOyma7uuolffh+IR5aW97cHuBUXKGKXlKjn+DiHWMcYJah4N0lYCMlJOXipGRr5qdgoSTrqWSq6WFl2ypoaUAAAIfkECQEAAQAsAAAAACgAKAAAApaEb6HLgd/iO7FNWtcFWe+ufODGjRfoiJ2akShbueb0wtI50zm02pbvwfWEMWBQ1zKGlLIhskiEPm9R6vRXxV4ZzWT2yHOGpWMyorblKlNp8HmHEb/lCXjcW7bmtXP8Xt229OVWR1fod2eWqNfHuMjXCPkIGNileOiImVmCOEmoSfn3yXlJWmoHGhqp6ilYuWYpmTqKUgAAIfkECQEAAQAsAAAAACgAKAAAApiEH6kb58biQ3FNWtMFWW3eNVcojuFGfqnZqSebuS06w5V80/X02pKe8zFwP6EFWOT1lDFk8rGERh1TTNOocQ61Hm4Xm2VexUHpzjymViHrFbiELsefVrn6XKfnt2Q9G/+Xdie499XHd2g4h7ioOGhXGJboGAnXSBnoBwKYyfioubZJ2Hn0RuRZaflZOil56Zp6iioKSXpUAAAh+QQJAQABACwAAAAAKAAoAAACkoQRqRvnxuI7kU1a1UU5bd5tnSeOZXhmn5lWK3qNTWvRdQxP8qvaC+/yaYQzXO7BMvaUEmJRd3TsiMAgswmNYrSgZdYrTX6tSHGZO73ezuAw2uxuQ+BbeZfMxsexY35+/Qe4J1inV0g4x3WHuMhIl2jXOKT2Q+VU5fgoSUI52VfZyfkJGkha6jmY+aaYdirq+lQAACH5BAkBAAEALAAAAAAoACgAAAKWBIKpYe0L3YNKToqswUlvznigd4wiR4KhZrKt9Upqip61i9E3vMvxRdHlbEFiEXfk9YARYxOZZD6VQ2pUunBmtRXo1Lf8hMVVcNl8JafV38aM2/Fu5V16Bn63r6xt97j09+MXSFi4BniGFae3hzbH9+hYBzkpuUh5aZmHuanZOZgIuvbGiNeomCnaxxap2upaCZsq+1kAACH5BAkBAAEALAAAAAAoACgAAAKXjI8By5zf4kOxTVrXNVlv1X0d8IGZGKLnNpYtm8Lr9cqVeuOSvfOW79D9aDHizNhDJidFZhNydEahOaDH6nomtJjp1tutKoNWkvA6JqfRVLHU/QUfau9l2x7G54d1fl995xcIGAdXqMfBNadoYrhH+Mg2KBlpVpbluCiXmMnZ2Sh4GBqJ+ckIOqqJ6LmKSllZmsoq6wpQAAAh+QQJAQABACwAAAAAKAAoAAAClYx/oLvoxuJDkU1a1YUZbJ59nSd2ZXhWqbRa2/gF8Gu2DY3iqs7yrq+xBYEkYvFSM8aSSObE+ZgRl1BHFZNr7pRCavZ5BW2142hY3AN/zWtsmf12p9XxxFl2lpLn1rseztfXZjdIWIf2s5dItwjYKBgo9yg5pHgzJXTEeGlZuenpyPmpGQoKOWkYmSpaSnqKileI2FAAACH5BAkBAAEALAAAAAAoACgAAAKVjB+gu+jG4kORTVrVhRlsnn2dJ3ZleFaptFrb+CXmO9OozeL5VfP99HvAWhpiUdcwkpBH3825AwYdU8xTqlLGhtCosArKMpvfa1mMRae9VvWZfeB2XfPkeLmm18lUcBj+p5dnN8jXZ3YIGEhYuOUn45aoCDkp16hl5IjYJvjWKcnoGQpqyPlpOhr3aElaqrq56Bq7VAAAOw==");
	height: 100%;
	filter: alpha(opacity=25); 
	opacity: 0.25;
}
.ui-progressbar-indeterminate .ui-progressbar-value {
	background-image: none;
}
.ui-selectable {
	-ms-touch-action: none;
	touch-action: none;
}
.ui-selectable-helper {
	position: absolute;
	z-index: 100;
	border: 1px dotted black;
}
.ui-selectmenu-menu {
	padding: 0;
	margin: 0;
	position: absolute;
	top: 0;
	left: 0;
	display: none;
}
.ui-selectmenu-menu .ui-menu {
	overflow: auto;
	overflow-x: hidden;
	padding-bottom: 1px;
}
.ui-selectmenu-menu .ui-menu .ui-selectmenu-optgroup {
	font-size: 1em;
	font-weight: bold;
	line-height: 1.5;
	padding: 2px 0.4em;
	margin: 0.5em 0 0 0;
	height: auto;
	border: 0;
}
.ui-selectmenu-open {
	display: block;
}
.ui-selectmenu-text {
	display: block;
	margin-right: 20px;
	overflow: hidden;
	text-overflow: ellipsis;
}
.ui-selectmenu-button.ui-button {
	text-align: left;
	white-space: nowrap;
	width: 14em;
}
.ui-selectmenu-icon.ui-icon {
	float: right;
	margin-top: 0;
}
.ui-slider {
	position: relative;
	text-align: left;
}
.ui-slider .ui-slider-handle {
	position: absolute;
	z-index: 2;
	width: 1.2em;
	height: 1.2em;
	cursor: default;
	-ms-touch-action: none;
	touch-action: none;
}
.ui-slider .ui-slider-range {
	position: absolute;
	z-index: 1;
	font-size: .7em;
	display: block;
	border: 0;
	background-position: 0 0;
}


.ui-slider.ui-state-disabled .ui-slider-handle,
.ui-slider.ui-state-disabled .ui-slider-range {
	filter: inherit;
}

.ui-slider-horizontal {
	height: .8em;
}
.ui-slider-horizontal .ui-slider-handle {
	top: -.3em;
	margin-left: -.6em;
}
.ui-slider-horizontal .ui-slider-range {
	top: 0;
	height: 100%;
}
.ui-slider-horizontal .ui-slider-range-min {
	left: 0;
}
.ui-slider-horizontal .ui-slider-range-max {
	right: 0;
}

.ui-slider-vertical {
	width: .8em;
	height: 100px;
}
.ui-slider-vertical .ui-slider-handle {
	left: -.3em;
	margin-left: 0;
	margin-bottom: -.6em;
}
.ui-slider-vertical .ui-slider-range {
	left: 0;
	width: 100%;
}
.ui-slider-vertical .ui-slider-range-min {
	bottom: 0;
}
.ui-slider-vertical .ui-slider-range-max {
	top: 0;
}
.ui-sortable-handle {
	-ms-touch-action: none;
	touch-action: none;
}
.ui-spinner {
	position: relative;
	display: inline-block;
	overflow: hidden;
	padding: 0;
	vertical-align: middle;
}
.ui-spinner-input {
	border: none;
	background: none;
	color: inherit;
	padding: .222em 0;
	margin: .2em 0;
	vertical-align: middle;
	margin-left: .4em;
	margin-right: 2em;
}
.ui-spinner-button {
	width: 1.6em;
	height: 50%;
	font-size: .5em;
	padding: 0;
	margin: 0;
	text-align: center;
	position: absolute;
	cursor: default;
	display: block;
	overflow: hidden;
	right: 0;
}

.ui-spinner a.ui-spinner-button {
	border-top-style: none;
	border-bottom-style: none;
	border-right-style: none;
}
.ui-spinner-up {
	top: 0;
}
.ui-spinner-down {
	bottom: 0;
}
.ui-tabs {
	position: relative;
	padding: .2em;
}
.ui-tabs .ui-tabs-nav {
	margin: 0;
	padding: .2em .2em 0;
}
.ui-tabs .ui-tabs-nav li {
	list-style: none;
	float: left;
	position: relative;
	top: 0;
	margin: 1px .2em 0 0;
	border-bottom-width: 0;
	padding: 0;
	white-space: nowrap;
}
.ui-tabs .ui-tabs-nav .ui-tabs-anchor {
	float: left;
	padding: .5em 1em;
	text-decoration: none;
}
.ui-tabs .ui-tabs-nav li.ui-tabs-active {
	margin-bottom: -1px;
	padding-bottom: 1px;
}
.ui-tabs .ui-tabs-nav li.ui-tabs-active .ui-tabs-anchor,
.ui-tabs .ui-tabs-nav li.ui-state-disabled .ui-tabs-anchor,
.ui-tabs .ui-tabs-nav li.ui-tabs-loading .ui-tabs-anchor {
	cursor: text;
}
.ui-tabs-collapsible .ui-tabs-nav li.ui-tabs-active .ui-tabs-anchor {
	cursor: pointer;
}
.ui-tabs .ui-tabs-panel {
	display: block;
	border-width: 0;
	padding: 1em 1.4em;
	background: none;
}
.ui-tooltip {
	padding: 8px;
	position: absolute;
	z-index: 9999;
	max-width: 300px;
}
body .ui-tooltip {
	border-width: 2px;
}

.ui-widget {
	font-family: Arial,Helvetica,sans-serif;
	font-size: 1em;
}
.ui-widget .ui-widget {
	font-size: 1em;
}
.ui-widget input,
.ui-widget select,
.ui-widget textarea,
.ui-widget button {
	font-family: Arial,Helvetica,sans-serif;
	font-size: 1em;
}
.ui-widget.ui-widget-content {
	border: 1px solid #c5c5c5;
}
.ui-widget-content {
	border: 1px solid #dddddd;
	background: #ffffff;
	color: #333333;
}
.ui-widget-content a {
	color: #333333;
}
.ui-widget-header {
	border: 1px solid #dddddd;
	background: #e9e9e9;
	color: #333333;
	font-weight: bold;
}
.ui-widget-header a {
	color: #333333;
}


.ui-state-default,
.ui-widget-content .ui-state-default,
.ui-widget-header .ui-state-default,
.ui-button,


html .ui-button.ui-state-disabled:hover,
html .ui-button.ui-state-disabled:active {
	border: 1px solid #c5c5c5;
	background: #f6f6f6;
	font-weight: normal;
	color: #454545;
}
.ui-state-default a,
.ui-state-default a:link,
.ui-state-default a:visited,
a.ui-button,
a:link.ui-button,
a:visited.ui-button,
.ui-button {
	color: #454545;
	text-decoration: none;
}
.ui-state-hover,
.ui-widget-content .ui-state-hover,
.ui-widget-header .ui-state-hover,
.ui-state-focus,
.ui-widget-content .ui-state-focus,
.ui-widget-header .ui-state-focus,
.ui-button:hover,
.ui-button:focus {
	border: 1px solid #cccccc;
	background: #ededed;
	font-weight: normal;
	color: #2b2b2b;
}
.ui-state-hover a,
.ui-state-hover a:hover,
.ui-state-hover a:link,
.ui-state-hover a:visited,
.ui-state-focus a,
.ui-state-focus a:hover,
.ui-state-focus a:link,
.ui-state-focus a:visited,
a.ui-button:hover,
a.ui-button:focus {
	color: #2b2b2b;
	text-decoration: none;
}

.ui-visual-focus {
	box-shadow: 0 0 3px 1px rgb(94, 158, 214);
}
.ui-state-active,
.ui-widget-content .ui-state-active,
.ui-widget-header .ui-state-active,
a.ui-button:active,
.ui-button:active,
.ui-button.ui-state-active:hover {
	border: 1px solid #003eff;
	background: #007fff;
	font-weight: normal;
	color: #ffffff;
}
.ui-icon-background,
.ui-state-active .ui-icon-background {
	border: #003eff;
	background-color: #ffffff;
}
.ui-state-active a,
.ui-state-active a:link,
.ui-state-active a:visited {
	color: #ffffff;
	text-decoration: none;
}


.ui-state-highlight,
.ui-widget-content .ui-state-highlight,
.ui-widget-header .ui-state-highlight {
	border: 1px solid #dad55e;
	background: #fffa90;
	color: #777620;
}
.ui-state-checked {
	border: 1px solid #dad55e;
	background: #fffa90;
}
.ui-state-highlight a,
.ui-widget-content .ui-state-highlight a,
.ui-widget-header .ui-state-highlight a {
	color: #777620;
}
.ui-state-error,
.ui-widget-content .ui-state-error,
.ui-widget-header .ui-state-error {
	border: 1px solid #f1a899;
	background: #fddfdf;
	color: #5f3f3f;
}
.ui-state-error a,
.ui-widget-content .ui-state-error a,
.ui-widget-header .ui-state-error a {
	color: #5f3f3f;
}
.ui-state-error-text,
.ui-widget-content .ui-state-error-text,
.ui-widget-header .ui-state-error-text {
	color: #5f3f3f;
}
.ui-priority-primary,
.ui-widget-content .ui-priority-primary,
.ui-widget-header .ui-priority-primary {
	font-weight: bold;
}
.ui-priority-secondary,
.ui-widget-content .ui-priority-secondary,
.ui-widget-header .ui-priority-secondary {
	opacity: .7;
	filter:Alpha(Opacity=70); 
	font-weight: normal;
}
.ui-state-disabled,
.ui-widget-content .ui-state-disabled,
.ui-widget-header .ui-state-disabled {
	opacity: .35;
	filter:Alpha(Opacity=35); 
	background-image: none;
}
.ui-state-disabled .ui-icon {
	filter:Alpha(Opacity=35); 
}




.ui-icon {
	width: 16px;
	height: 16px;
}
.ui-icon,
.ui-widget-content .ui-icon {
	background-image: url("images/ui-icons_444444_256x240.png");
}
.ui-widget-header .ui-icon {
	background-image: url("images/ui-icons_444444_256x240.png");
}
.ui-state-hover .ui-icon,
.ui-state-focus .ui-icon,
.ui-button:hover .ui-icon,
.ui-button:focus .ui-icon {
	background-image: url("images/ui-icons_555555_256x240.png");
}
.ui-state-active .ui-icon,
.ui-button:active .ui-icon {
	background-image: url("images/ui-icons_ffffff_256x240.png");
}
.ui-state-highlight .ui-icon,
.ui-button .ui-state-highlight.ui-icon {
	background-image: url("images/ui-icons_777620_256x240.png");
}
.ui-state-error .ui-icon,
.ui-state-error-text .ui-icon {
	background-image: url("images/ui-icons_cc0000_256x240.png");
}
.ui-button .ui-icon {
	background-image: url("images/ui-icons_777777_256x240.png");
}


.ui-icon-blank { background-position: 16px 16px; }
.ui-icon-caret-1-n { background-position: 0 0; }
.ui-icon-caret-1-ne { background-position: -16px 0; }
.ui-icon-caret-1-e { background-position: -32px 0; }
.ui-icon-caret-1-se { background-position: -48px 0; }
.ui-icon-caret-1-s { background-position: -65px 0; }
.ui-icon-caret-1-sw { background-position: -80px 0; }
.ui-icon-caret-1-w { background-position: -96px 0; }
.ui-icon-caret-1-nw { background-position: -112px 0; }
.ui-icon-caret-2-n-s { background-position: -128px 0; }
.ui-icon-caret-2-e-w { background-position: -144px 0; }
.ui-icon-triangle-1-n { background-position: 0 -16px; }
.ui-icon-triangle-1-ne { background-position: -16px -16px; }
.ui-icon-triangle-1-e { background-position: -32px -16px; }
.ui-icon-triangle-1-se { background-position: -48px -16px; }
.ui-icon-triangle-1-s { background-position: -65px -16px; }
.ui-icon-triangle-1-sw { background-position: -80px -16px; }
.ui-icon-triangle-1-w { background-position: -96px -16px; }
.ui-icon-triangle-1-nw { background-position: -112px -16px; }
.ui-icon-triangle-2-n-s { background-position: -128px -16px; }
.ui-icon-triangle-2-e-w { background-position: -144px -16px; }
.ui-icon-arrow-1-n { background-position: 0 -32px; }
.ui-icon-arrow-1-ne { background-position: -16px -32px; }
.ui-icon-arrow-1-e { background-position: -32px -32px; }
.ui-icon-arrow-1-se { background-position: -48px -32px; }
.ui-icon-arrow-1-s { background-position: -65px -32px; }
.ui-icon-arrow-1-sw { background-position: -80px -32px; }
.ui-icon-arrow-1-w { background-position: -96px -32px; }
.ui-icon-arrow-1-nw { background-position: -112px -32px; }
.ui-icon-arrow-2-n-s { background-position: -128px -32px; }
.ui-icon-arrow-2-ne-sw { background-position: -144px -32px; }
.ui-icon-arrow-2-e-w { background-position: -160px -32px; }
.ui-icon-arrow-2-se-nw { background-position: -176px -32px; }
.ui-icon-arrowstop-1-n { background-position: -192px -32px; }
.ui-icon-arrowstop-1-e { background-position: -208px -32px; }
.ui-icon-arrowstop-1-s { background-position: -224px -32px; }
.ui-icon-arrowstop-1-w { background-position: -240px -32px; }
.ui-icon-arrowthick-1-n { background-position: 1px -48px; }
.ui-icon-arrowthick-1-ne { background-position: -16px -48px; }
.ui-icon-arrowthick-1-e { background-position: -32px -48px; }
.ui-icon-arrowthick-1-se { background-position: -48px -48px; }
.ui-icon-arrowthick-1-s { background-position: -64px -48px; }
.ui-icon-arrowthick-1-sw { background-position: -80px -48px; }
.ui-icon-arrowthick-1-w { background-position: -96px -48px; }
.ui-icon-arrowthick-1-nw { background-position: -112px -48px; }
.ui-icon-arrowthick-2-n-s { background-position: -128px -48px; }
.ui-icon-arrowthick-2-ne-sw { background-position: -144px -48px; }
.ui-icon-arrowthick-2-e-w { background-position: -160px -48px; }
.ui-icon-arrowthick-2-se-nw { background-position: -176px -48px; }
.ui-icon-arrowthickstop-1-n { background-position: -192px -48px; }
.ui-icon-arrowthickstop-1-e { background-position: -208px -48px; }
.ui-icon-arrowthickstop-1-s { background-position: -224px -48px; }
.ui-icon-arrowthickstop-1-w { background-position: -240px -48px; }
.ui-icon-arrowreturnthick-1-w { background-position: 0 -64px; }
.ui-icon-arrowreturnthick-1-n { background-position: -16px -64px; }
.ui-icon-arrowreturnthick-1-e { background-position: -32px -64px; }
.ui-icon-arrowreturnthick-1-s { background-position: -48px -64px; }
.ui-icon-arrowreturn-1-w { background-position: -64px -64px; }
.ui-icon-arrowreturn-1-n { background-position: -80px -64px; }
.ui-icon-arrowreturn-1-e { background-position: -96px -64px; }
.ui-icon-arrowreturn-1-s { background-position: -112px -64px; }
.ui-icon-arrowrefresh-1-w { background-position: -128px -64px; }
.ui-icon-arrowrefresh-1-n { background-position: -144px -64px; }
.ui-icon-arrowrefresh-1-e { background-position: -160px -64px; }
.ui-icon-arrowrefresh-1-s { background-position: -176px -64px; }
.ui-icon-arrow-4 { background-position: 0 -80px; }
.ui-icon-arrow-4-diag { background-position: -16px -80px; }
.ui-icon-extlink { background-position: -32px -80px; }
.ui-icon-newwin { background-position: -48px -80px; }
.ui-icon-refresh { background-position: -64px -80px; }
.ui-icon-shuffle { background-position: -80px -80px; }
.ui-icon-transfer-e-w { background-position: -96px -80px; }
.ui-icon-transferthick-e-w { background-position: -112px -80px; }
.ui-icon-folder-collapsed { background-position: 0 -96px; }
.ui-icon-folder-open { background-position: -16px -96px; }
.ui-icon-document { background-position: -32px -96px; }
.ui-icon-document-b { background-position: -48px -96px; }
.ui-icon-note { background-position: -64px -96px; }
.ui-icon-mail-closed { background-position: -80px -96px; }
.ui-icon-mail-open { background-position: -96px -96px; }
.ui-icon-suitcase { background-position: -112px -96px; }
.ui-icon-comment { background-position: -128px -96px; }
.ui-icon-person { background-position: -144px -96px; }
.ui-icon-print { background-position: -160px -96px; }
.ui-icon-trash { background-position: -176px -96px; }
.ui-icon-locked { background-position: -192px -96px; }
.ui-icon-unlocked { background-position: -208px -96px; }
.ui-icon-bookmark { background-position: -224px -96px; }
.ui-icon-tag { background-position: -240px -96px; }
.ui-icon-home { background-position: 0 -112px; }
.ui-icon-flag { background-position: -16px -112px; }
.ui-icon-calendar { background-position: -32px -112px; }
.ui-icon-cart { background-position: -48px -112px; }
.ui-icon-pencil { background-position: -64px -112px; }
.ui-icon-clock { background-position: -80px -112px; }
.ui-icon-disk { background-position: -96px -112px; }
.ui-icon-calculator { background-position: -112px -112px; }
.ui-icon-zoomin { background-position: -128px -112px; }
.ui-icon-zoomout { background-position: -144px -112px; }
.ui-icon-search { background-position: -160px -112px; }
.ui-icon-wrench { background-position: -176px -112px; }
.ui-icon-gear { background-position: -192px -112px; }
.ui-icon-heart { background-position: -208px -112px; }
.ui-icon-star { background-position: -224px -112px; }
.ui-icon-link { background-position: -240px -112px; }
.ui-icon-cancel { background-position: 0 -128px; }
.ui-icon-plus { background-position: -16px -128px; }
.ui-icon-plusthick { background-position: -32px -128px; }
.ui-icon-minus { background-position: -48px -128px; }
.ui-icon-minusthick { background-position: -64px -128px; }
.ui-icon-close { background-position: -80px -128px; }
.ui-icon-closethick { background-position: -96px -128px; }
.ui-icon-key { background-position: -112px -128px; }
.ui-icon-lightbulb { background-position: -128px -128px; }
.ui-icon-scissors { background-position: -144px -128px; }
.ui-icon-clipboard { background-position: -160px -128px; }
.ui-icon-copy { background-position: -176px -128px; }
.ui-icon-contact { background-position: -192px -128px; }
.ui-icon-image { background-position: -208px -128px; }
.ui-icon-video { background-position: -224px -128px; }
.ui-icon-script { background-position: -240px -128px; }
.ui-icon-alert { background-position: 0 -144px; }
.ui-icon-info { background-position: -16px -144px; }
.ui-icon-notice { background-position: -32px -144px; }
.ui-icon-help { background-position: -48px -144px; }
.ui-icon-check { background-position: -64px -144px; }
.ui-icon-bullet { background-position: -80px -144px; }
.ui-icon-radio-on { background-position: -96px -144px; }
.ui-icon-radio-off { background-position: -112px -144px; }
.ui-icon-pin-w { background-position: -128px -144px; }
.ui-icon-pin-s { background-position: -144px -144px; }
.ui-icon-play { background-position: 0 -160px; }
.ui-icon-pause { background-position: -16px -160px; }
.ui-icon-seek-next { background-position: -32px -160px; }
.ui-icon-seek-prev { background-position: -48px -160px; }
.ui-icon-seek-end { background-position: -64px -160px; }
.ui-icon-seek-start { background-position: -80px -160px; }

.ui-icon-seek-first { background-position: -80px -160px; }
.ui-icon-stop { background-position: -96px -160px; }
.ui-icon-eject { background-position: -112px -160px; }
.ui-icon-volume-off { background-position: -128px -160px; }
.ui-icon-volume-on { background-position: -144px -160px; }
.ui-icon-power { background-position: 0 -176px; }
.ui-icon-signal-diag { background-position: -16px -176px; }
.ui-icon-signal { background-position: -32px -176px; }
.ui-icon-battery-0 { background-position: -48px -176px; }
.ui-icon-battery-1 { background-position: -64px -176px; }
.ui-icon-battery-2 { background-position: -80px -176px; }
.ui-icon-battery-3 { background-position: -96px -176px; }
.ui-icon-circle-plus { background-position: 0 -192px; }
.ui-icon-circle-minus { background-position: -16px -192px; }
.ui-icon-circle-close { background-position: -32px -192px; }
.ui-icon-circle-triangle-e { background-position: -48px -192px; }
.ui-icon-circle-triangle-s { background-position: -64px -192px; }
.ui-icon-circle-triangle-w { background-position: -80px -192px; }
.ui-icon-circle-triangle-n { background-position: -96px -192px; }
.ui-icon-circle-arrow-e { background-position: -112px -192px; }
.ui-icon-circle-arrow-s { background-position: -128px -192px; }
.ui-icon-circle-arrow-w { background-position: -144px -192px; }
.ui-icon-circle-arrow-n { background-position: -160px -192px; }
.ui-icon-circle-zoomin { background-position: -176px -192px; }
.ui-icon-circle-zoomout { background-position: -192px -192px; }
.ui-icon-circle-check { background-position: -208px -192px; }
.ui-icon-circlesmall-plus { background-position: 0 -208px; }
.ui-icon-circlesmall-minus { background-position: -16px -208px; }
.ui-icon-circlesmall-close { background-position: -32px -208px; }
.ui-icon-squaresmall-plus { background-position: -48px -208px; }
.ui-icon-squaresmall-minus { background-position: -64px -208px; }
.ui-icon-squaresmall-close { background-position: -80px -208px; }
.ui-icon-grip-dotted-vertical { background-position: 0 -224px; }
.ui-icon-grip-dotted-horizontal { background-position: -16px -224px; }
.ui-icon-grip-solid-vertical { background-position: -32px -224px; }
.ui-icon-grip-solid-horizontal { background-position: -48px -224px; }
.ui-icon-gripsmall-diagonal-se { background-position: -64px -224px; }
.ui-icon-grip-diagonal-se { background-position: -80px -224px; }





.ui-corner-all,
.ui-corner-top,
.ui-corner-left,
.ui-corner-tl {
	border-top-left-radius: 3px;
}
.ui-corner-all,
.ui-corner-top,
.ui-corner-right,
.ui-corner-tr {
	border-top-right-radius: 3px;
}
.ui-corner-all,
.ui-corner-bottom,
.ui-corner-left,
.ui-corner-bl {
	border-bottom-left-radius: 3px;
}
.ui-corner-all,
.ui-corner-bottom,
.ui-corner-right,
.ui-corner-br {
	border-bottom-right-radius: 3px;
}


.ui-widget-overlay {
	background: #aaaaaa;
	opacity: .3;
	filter: Alpha(Opacity=30); 
}
.ui-widget-shadow {
	-webkit-box-shadow: 0px 0px 5px #666666;
	box-shadow: 0px 0px 5px #666666;
} 
</style>
<script src='js/jquery-1.12.4.js'></script>
<script src='js/jquery-ui.js'></script>

<script>
$( function() {
	$( '#tabs-collect-classes-from-hierarchical-partition' ).tabs();
} );
</script>
<div id='tabs-collect-classes-from-hierarchical-partition'>
<ul>
<li><a href='#tab-collect-classes-from-hierarchical-partition-1'>n_signatures ≥ 3265</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-2'>n_signatures ≥ 4048</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-3'>n_signatures ≥ 7591</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-4'>n_signatures ≥ 8310</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-5'>n_signatures ≥ 10559</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-6'>n_signatures ≥ 54876</a></li>
</ul>
<div id='tab-collect-classes-from-hierarchical-partition-1'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3265))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-1-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-1"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-2'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 4048))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-2-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-2"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-3'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 7591))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-3-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-3"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-4'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 8310))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-4-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-4"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-5'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 10559))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-5-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-5"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-6'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 54876))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-6-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-6"/></p>

</div>
</div>

Following shows the table of the partitions (You need to click the **show/hide
code output** link to see it).


<script>
$( function() {
	$( '#tabs-get-classes-from-hierarchical-partition' ).tabs();
} );
</script>
<div id='tabs-get-classes-from-hierarchical-partition'>
<ul>
<li><a href='#tab-get-classes-from-hierarchical-partition-1'>n_signatures ≥ 3265</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-2'>n_signatures ≥ 4048</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-3'>n_signatures ≥ 7591</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-4'>n_signatures ≥ 8310</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-5'>n_signatures ≥ 10559</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-6'>n_signatures ≥ 54876</a></li>
</ul>

<div id='tab-get-classes-from-hierarchical-partition-1'>
<p><a id='tab-get-classes-from-hierarchical-partition-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3265))
</code></pre>

<pre><code>#&gt; TCGA.3S.A8YW.01 TCGA.ZB.A96K.01 TCGA.XU.A930.01 TCGA.ZB.A965.01 TCGA.4V.A9QN.01 TCGA.ZB.A96G.01 
#&gt;           &quot;041&quot;           &quot;032&quot;           &quot;031&quot;           &quot;022&quot;           &quot;042&quot;           &quot;011&quot; 
#&gt; TCGA.XM.A8R8.01 TCGA.XU.AAXX.01 TCGA.ZT.A8OM.01 TCGA.3S.AAYX.01 TCGA.ZB.A96M.01 TCGA.XU.A936.01 
#&gt;          &quot;0123&quot;          &quot;0124&quot;          &quot;0122&quot;          &quot;0121&quot;           &quot;033&quot;           &quot;041&quot; 
#&gt; TCGA.5U.AB0F.01 TCGA.X7.A8DJ.01 TCGA.ZB.A96D.01 TCGA.ZB.A96Q.01 TCGA.X7.A8DG.01 TCGA.X7.A8D9.01 
#&gt;          &quot;0122&quot;           &quot;011&quot;          &quot;0122&quot;           &quot;032&quot;           &quot;011&quot;           &quot;033&quot; 
#&gt; TCGA.5V.A9RR.01 TCGA.4V.A9QI.01 TCGA.ZB.A96C.01 TCGA.4V.A9QX.01 TCGA.XU.A931.01 TCGA.ZB.A961.01 
#&gt;           &quot;032&quot;           &quot;011&quot;           &quot;024&quot;          &quot;0122&quot;           &quot;042&quot;           &quot;031&quot; 
#&gt; TCGA.4X.A9FB.01 TCGA.YT.A95E.01 TCGA.X7.A8D7.01 TCGA.4V.A9QQ.01 TCGA.ZB.A969.01 TCGA.X7.A8M4.01 
#&gt;           &quot;011&quot;           &quot;011&quot;          &quot;0121&quot;          &quot;0124&quot;           &quot;023&quot;           &quot;011&quot; 
#&gt; TCGA.XM.A8RC.01 TCGA.4V.A9QJ.01 TCGA.XM.AAZ2.01 TCGA.X7.A8M1.01 TCGA.XM.A8RG.01 TCGA.4X.A9FD.01 
#&gt;           &quot;031&quot;           &quot;011&quot;           &quot;024&quot;           &quot;032&quot;           &quot;021&quot;           &quot;034&quot; 
#&gt; TCGA.X7.A8D6.01 TCGA.ZC.AAAF.01 TCGA.3G.AB0Q.01 TCGA.4X.A9FA.01 TCGA.5K.AAAP.01 TCGA.XM.A8RF.01 
#&gt;          &quot;0121&quot;          &quot;0122&quot;           &quot;024&quot;           &quot;024&quot;           &quot;032&quot;           &quot;023&quot; 
#&gt; TCGA.4X.A9FC.01 TCGA.3T.AA9L.01 TCGA.XU.A92W.01 TCGA.X7.A8DI.01 TCGA.ZL.A9V6.01 TCGA.XU.AAXY.01 
#&gt;          &quot;0124&quot;          &quot;0121&quot;           &quot;011&quot;          &quot;0124&quot;           &quot;021&quot;           &quot;011&quot; 
#&gt; TCGA.4V.A9QU.01 TCGA.X7.A8DF.01 TCGA.XU.A932.01 TCGA.XU.A92Z.01 TCGA.3G.AB0O.01 TCGA.XU.A92X.01 
#&gt;          &quot;0122&quot;           &quot;011&quot;           &quot;011&quot;           &quot;042&quot;           &quot;011&quot;           &quot;031&quot; 
#&gt; TCGA.XU.A92O.01 TCGA.5G.A9ZZ.01 TCGA.X7.A8M7.01 TCGA.XM.A8R9.01 TCGA.XM.AAZ1.01 TCGA.X7.A8DE.01 
#&gt;           &quot;021&quot;           &quot;034&quot;           &quot;011&quot;          &quot;0123&quot;           &quot;011&quot;          &quot;0122&quot; 
#&gt; TCGA.X7.A8D7.11 TCGA.ZB.A962.01 TCGA.YT.A95D.01 TCGA.X7.A8M8.01 TCGA.X7.A8D6.11 TCGA.4V.A9QT.01 
#&gt;          &quot;0121&quot;           &quot;022&quot;           &quot;024&quot;           &quot;011&quot;          &quot;0123&quot;          &quot;0121&quot; 
#&gt; TCGA.3G.AB14.01 TCGA.5U.AB0D.01 TCGA.YT.A95F.01 TCGA.XM.A8RL.01 TCGA.4V.A9QR.01 TCGA.XM.A8RI.01 
#&gt;           &quot;031&quot;           &quot;041&quot;           &quot;033&quot;           &quot;011&quot;           &quot;034&quot;           &quot;031&quot; 
#&gt; TCGA.XM.A8RE.01 TCGA.XM.A8RH.01 TCGA.ZC.AAAH.01 TCGA.XH.A853.01 TCGA.X7.A8DD.01 TCGA.4V.A9QL.01 
#&gt;          &quot;0121&quot;          &quot;0124&quot;           &quot;011&quot;           &quot;011&quot;          &quot;0124&quot;           &quot;033&quot; 
#&gt; TCGA.ZB.A96A.01 TCGA.XU.AAY0.01 TCGA.XM.A8RB.01 TCGA.ZB.A96R.01 TCGA.ZB.A96V.01 TCGA.XM.A8RD.01 
#&gt;           &quot;011&quot;          &quot;0122&quot;          &quot;0121&quot;           &quot;011&quot;           &quot;041&quot;          &quot;0122&quot; 
#&gt; TCGA.X7.A8M0.01 TCGA.ZB.A96I.01 TCGA.ZB.A96F.01 TCGA.X7.A8DC.01 TCGA.X7.A8M5.01 TCGA.ZB.A966.01 
#&gt;           &quot;033&quot;           &quot;042&quot;           &quot;031&quot;           &quot;011&quot;           &quot;042&quot;           &quot;041&quot; 
#&gt; TCGA.XU.A92V.01 TCGA.YT.A95H.01 TCGA.ZC.AAAA.01 TCGA.XU.A92R.01 TCGA.YT.A95G.01 TCGA.XU.A933.01 
#&gt;           &quot;042&quot;           &quot;011&quot;           &quot;011&quot;          &quot;0122&quot;          &quot;0122&quot;           &quot;041&quot; 
#&gt; TCGA.XU.A92U.01 TCGA.3Q.A9WF.01 TCGA.XU.AAXV.01 TCGA.X7.A8D8.01 TCGA.ZB.A96L.01 TCGA.XU.AAXW.01 
#&gt;           &quot;011&quot;           &quot;011&quot;          &quot;0122&quot;           &quot;032&quot;           &quot;023&quot;          &quot;0124&quot; 
#&gt; TCGA.4V.A9QW.01 TCGA.XU.AAXZ.01 TCGA.X7.A8DB.01 TCGA.ZB.A96O.01 TCGA.ZB.A96H.01 TCGA.4V.A9QM.01 
#&gt;           &quot;011&quot;           &quot;011&quot;          &quot;0121&quot;          &quot;0121&quot;           &quot;021&quot;           &quot;032&quot; 
#&gt; TCGA.XU.AAY1.01 TCGA.4V.A9QS.01 TCGA.XU.A92T.01 TCGA.X7.A8M6.01 TCGA.3G.AB0T.01 TCGA.ZC.AAA7.01 
#&gt;          &quot;0124&quot;          &quot;0122&quot;           &quot;022&quot;           &quot;011&quot;           &quot;011&quot;           &quot;041&quot; 
#&gt; TCGA.4X.A9F9.01 TCGA.XU.A92Y.01 TCGA.ZB.A96B.01 TCGA.3G.AB19.01 TCGA.XM.AAZ3.01 TCGA.X7.A8M3.01 
#&gt;          &quot;0121&quot;          &quot;0122&quot;           &quot;011&quot;           &quot;023&quot;           &quot;021&quot;           &quot;042&quot; 
#&gt; TCGA.ZB.A964.01 TCGA.5U.AB0E.01 TCGA.XU.A92Q.01 TCGA.ZB.A96P.01 TCGA.ZB.A96E.01 TCGA.ZB.A963.01 
#&gt;           &quot;022&quot;           &quot;031&quot;           &quot;022&quot;           &quot;011&quot;           &quot;032&quot;           &quot;011&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-1-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-1-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-2'>
<p><a id='tab-get-classes-from-hierarchical-partition-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 4048))
</code></pre>

<pre><code>#&gt; TCGA.3S.A8YW.01 TCGA.ZB.A96K.01 TCGA.XU.A930.01 TCGA.ZB.A965.01 TCGA.4V.A9QN.01 TCGA.ZB.A96G.01 
#&gt;           &quot;041&quot;           &quot;032&quot;           &quot;031&quot;           &quot;022&quot;           &quot;042&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8R8.01 TCGA.XU.AAXX.01 TCGA.ZT.A8OM.01 TCGA.3S.AAYX.01 TCGA.ZB.A96M.01 TCGA.XU.A936.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot;           &quot;041&quot; 
#&gt; TCGA.5U.AB0F.01 TCGA.X7.A8DJ.01 TCGA.ZB.A96D.01 TCGA.ZB.A96Q.01 TCGA.X7.A8DG.01 TCGA.X7.A8D9.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.5V.A9RR.01 TCGA.4V.A9QI.01 TCGA.ZB.A96C.01 TCGA.4V.A9QX.01 TCGA.XU.A931.01 TCGA.ZB.A961.01 
#&gt;           &quot;032&quot;            &quot;01&quot;           &quot;024&quot;            &quot;01&quot;           &quot;042&quot;           &quot;031&quot; 
#&gt; TCGA.4X.A9FB.01 TCGA.YT.A95E.01 TCGA.X7.A8D7.01 TCGA.4V.A9QQ.01 TCGA.ZB.A969.01 TCGA.X7.A8M4.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;023&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8RC.01 TCGA.4V.A9QJ.01 TCGA.XM.AAZ2.01 TCGA.X7.A8M1.01 TCGA.XM.A8RG.01 TCGA.4X.A9FD.01 
#&gt;           &quot;031&quot;            &quot;01&quot;           &quot;024&quot;           &quot;032&quot;           &quot;021&quot;           &quot;034&quot; 
#&gt; TCGA.X7.A8D6.01 TCGA.ZC.AAAF.01 TCGA.3G.AB0Q.01 TCGA.4X.A9FA.01 TCGA.5K.AAAP.01 TCGA.XM.A8RF.01 
#&gt;            &quot;01&quot;            &quot;01&quot;           &quot;024&quot;           &quot;024&quot;           &quot;032&quot;           &quot;023&quot; 
#&gt; TCGA.4X.A9FC.01 TCGA.3T.AA9L.01 TCGA.XU.A92W.01 TCGA.X7.A8DI.01 TCGA.ZL.A9V6.01 TCGA.XU.AAXY.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;021&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QU.01 TCGA.X7.A8DF.01 TCGA.XU.A932.01 TCGA.XU.A92Z.01 TCGA.3G.AB0O.01 TCGA.XU.A92X.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;042&quot;            &quot;01&quot;           &quot;031&quot; 
#&gt; TCGA.XU.A92O.01 TCGA.5G.A9ZZ.01 TCGA.X7.A8M7.01 TCGA.XM.A8R9.01 TCGA.XM.AAZ1.01 TCGA.X7.A8DE.01 
#&gt;           &quot;021&quot;           &quot;034&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8D7.11 TCGA.ZB.A962.01 TCGA.YT.A95D.01 TCGA.X7.A8M8.01 TCGA.X7.A8D6.11 TCGA.4V.A9QT.01 
#&gt;            &quot;01&quot;           &quot;022&quot;           &quot;024&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.3G.AB14.01 TCGA.5U.AB0D.01 TCGA.YT.A95F.01 TCGA.XM.A8RL.01 TCGA.4V.A9QR.01 TCGA.XM.A8RI.01 
#&gt;           &quot;031&quot;           &quot;041&quot;           &quot;033&quot;            &quot;01&quot;           &quot;034&quot;           &quot;031&quot; 
#&gt; TCGA.XM.A8RE.01 TCGA.XM.A8RH.01 TCGA.ZC.AAAH.01 TCGA.XH.A853.01 TCGA.X7.A8DD.01 TCGA.4V.A9QL.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.ZB.A96A.01 TCGA.XU.AAY0.01 TCGA.XM.A8RB.01 TCGA.ZB.A96R.01 TCGA.ZB.A96V.01 TCGA.XM.A8RD.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;041&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8M0.01 TCGA.ZB.A96I.01 TCGA.ZB.A96F.01 TCGA.X7.A8DC.01 TCGA.X7.A8M5.01 TCGA.ZB.A966.01 
#&gt;           &quot;033&quot;           &quot;042&quot;           &quot;031&quot;            &quot;01&quot;           &quot;042&quot;           &quot;041&quot; 
#&gt; TCGA.XU.A92V.01 TCGA.YT.A95H.01 TCGA.ZC.AAAA.01 TCGA.XU.A92R.01 TCGA.YT.A95G.01 TCGA.XU.A933.01 
#&gt;           &quot;042&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;041&quot; 
#&gt; TCGA.XU.A92U.01 TCGA.3Q.A9WF.01 TCGA.XU.AAXV.01 TCGA.X7.A8D8.01 TCGA.ZB.A96L.01 TCGA.XU.AAXW.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;           &quot;023&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QW.01 TCGA.XU.AAXZ.01 TCGA.X7.A8DB.01 TCGA.ZB.A96O.01 TCGA.ZB.A96H.01 TCGA.4V.A9QM.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;021&quot;           &quot;032&quot; 
#&gt; TCGA.XU.AAY1.01 TCGA.4V.A9QS.01 TCGA.XU.A92T.01 TCGA.X7.A8M6.01 TCGA.3G.AB0T.01 TCGA.ZC.AAA7.01 
#&gt;            &quot;01&quot;            &quot;01&quot;           &quot;022&quot;            &quot;01&quot;            &quot;01&quot;           &quot;041&quot; 
#&gt; TCGA.4X.A9F9.01 TCGA.XU.A92Y.01 TCGA.ZB.A96B.01 TCGA.3G.AB19.01 TCGA.XM.AAZ3.01 TCGA.X7.A8M3.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;023&quot;           &quot;021&quot;           &quot;042&quot; 
#&gt; TCGA.ZB.A964.01 TCGA.5U.AB0E.01 TCGA.XU.A92Q.01 TCGA.ZB.A96P.01 TCGA.ZB.A96E.01 TCGA.ZB.A963.01 
#&gt;           &quot;022&quot;           &quot;031&quot;           &quot;022&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-2-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-2-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-3'>
<p><a id='tab-get-classes-from-hierarchical-partition-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 7591))
</code></pre>

<pre><code>#&gt; TCGA.3S.A8YW.01 TCGA.ZB.A96K.01 TCGA.XU.A930.01 TCGA.ZB.A965.01 TCGA.4V.A9QN.01 TCGA.ZB.A96G.01 
#&gt;           &quot;041&quot;           &quot;032&quot;           &quot;031&quot;            &quot;02&quot;           &quot;042&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8R8.01 TCGA.XU.AAXX.01 TCGA.ZT.A8OM.01 TCGA.3S.AAYX.01 TCGA.ZB.A96M.01 TCGA.XU.A936.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot;           &quot;041&quot; 
#&gt; TCGA.5U.AB0F.01 TCGA.X7.A8DJ.01 TCGA.ZB.A96D.01 TCGA.ZB.A96Q.01 TCGA.X7.A8DG.01 TCGA.X7.A8D9.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.5V.A9RR.01 TCGA.4V.A9QI.01 TCGA.ZB.A96C.01 TCGA.4V.A9QX.01 TCGA.XU.A931.01 TCGA.ZB.A961.01 
#&gt;           &quot;032&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;           &quot;042&quot;           &quot;031&quot; 
#&gt; TCGA.4X.A9FB.01 TCGA.YT.A95E.01 TCGA.X7.A8D7.01 TCGA.4V.A9QQ.01 TCGA.ZB.A969.01 TCGA.X7.A8M4.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8RC.01 TCGA.4V.A9QJ.01 TCGA.XM.AAZ2.01 TCGA.X7.A8M1.01 TCGA.XM.A8RG.01 TCGA.4X.A9FD.01 
#&gt;           &quot;031&quot;            &quot;01&quot;            &quot;02&quot;           &quot;032&quot;            &quot;02&quot;           &quot;034&quot; 
#&gt; TCGA.X7.A8D6.01 TCGA.ZC.AAAF.01 TCGA.3G.AB0Q.01 TCGA.4X.A9FA.01 TCGA.5K.AAAP.01 TCGA.XM.A8RF.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;           &quot;032&quot;            &quot;02&quot; 
#&gt; TCGA.4X.A9FC.01 TCGA.3T.AA9L.01 TCGA.XU.A92W.01 TCGA.X7.A8DI.01 TCGA.ZL.A9V6.01 TCGA.XU.AAXY.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QU.01 TCGA.X7.A8DF.01 TCGA.XU.A932.01 TCGA.XU.A92Z.01 TCGA.3G.AB0O.01 TCGA.XU.A92X.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;042&quot;            &quot;01&quot;           &quot;031&quot; 
#&gt; TCGA.XU.A92O.01 TCGA.5G.A9ZZ.01 TCGA.X7.A8M7.01 TCGA.XM.A8R9.01 TCGA.XM.AAZ1.01 TCGA.X7.A8DE.01 
#&gt;            &quot;02&quot;           &quot;034&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8D7.11 TCGA.ZB.A962.01 TCGA.YT.A95D.01 TCGA.X7.A8M8.01 TCGA.X7.A8D6.11 TCGA.4V.A9QT.01 
#&gt;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.3G.AB14.01 TCGA.5U.AB0D.01 TCGA.YT.A95F.01 TCGA.XM.A8RL.01 TCGA.4V.A9QR.01 TCGA.XM.A8RI.01 
#&gt;           &quot;031&quot;           &quot;041&quot;           &quot;033&quot;            &quot;01&quot;           &quot;034&quot;           &quot;031&quot; 
#&gt; TCGA.XM.A8RE.01 TCGA.XM.A8RH.01 TCGA.ZC.AAAH.01 TCGA.XH.A853.01 TCGA.X7.A8DD.01 TCGA.4V.A9QL.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.ZB.A96A.01 TCGA.XU.AAY0.01 TCGA.XM.A8RB.01 TCGA.ZB.A96R.01 TCGA.ZB.A96V.01 TCGA.XM.A8RD.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;041&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8M0.01 TCGA.ZB.A96I.01 TCGA.ZB.A96F.01 TCGA.X7.A8DC.01 TCGA.X7.A8M5.01 TCGA.ZB.A966.01 
#&gt;           &quot;033&quot;           &quot;042&quot;           &quot;031&quot;            &quot;01&quot;           &quot;042&quot;           &quot;041&quot; 
#&gt; TCGA.XU.A92V.01 TCGA.YT.A95H.01 TCGA.ZC.AAAA.01 TCGA.XU.A92R.01 TCGA.YT.A95G.01 TCGA.XU.A933.01 
#&gt;           &quot;042&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;041&quot; 
#&gt; TCGA.XU.A92U.01 TCGA.3Q.A9WF.01 TCGA.XU.AAXV.01 TCGA.X7.A8D8.01 TCGA.ZB.A96L.01 TCGA.XU.AAXW.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QW.01 TCGA.XU.AAXZ.01 TCGA.X7.A8DB.01 TCGA.ZB.A96O.01 TCGA.ZB.A96H.01 TCGA.4V.A9QM.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;           &quot;032&quot; 
#&gt; TCGA.XU.AAY1.01 TCGA.4V.A9QS.01 TCGA.XU.A92T.01 TCGA.X7.A8M6.01 TCGA.3G.AB0T.01 TCGA.ZC.AAA7.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;           &quot;041&quot; 
#&gt; TCGA.4X.A9F9.01 TCGA.XU.A92Y.01 TCGA.ZB.A96B.01 TCGA.3G.AB19.01 TCGA.XM.AAZ3.01 TCGA.X7.A8M3.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;           &quot;042&quot; 
#&gt; TCGA.ZB.A964.01 TCGA.5U.AB0E.01 TCGA.XU.A92Q.01 TCGA.ZB.A96P.01 TCGA.ZB.A96E.01 TCGA.ZB.A963.01 
#&gt;            &quot;02&quot;           &quot;031&quot;            &quot;02&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-3-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-3-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-4'>
<p><a id='tab-get-classes-from-hierarchical-partition-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 8310))
</code></pre>

<pre><code>#&gt; TCGA.3S.A8YW.01 TCGA.ZB.A96K.01 TCGA.XU.A930.01 TCGA.ZB.A965.01 TCGA.4V.A9QN.01 TCGA.ZB.A96G.01 
#&gt;            &quot;04&quot;           &quot;032&quot;           &quot;031&quot;            &quot;02&quot;            &quot;04&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8R8.01 TCGA.XU.AAXX.01 TCGA.ZT.A8OM.01 TCGA.3S.AAYX.01 TCGA.ZB.A96M.01 TCGA.XU.A936.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot;            &quot;04&quot; 
#&gt; TCGA.5U.AB0F.01 TCGA.X7.A8DJ.01 TCGA.ZB.A96D.01 TCGA.ZB.A96Q.01 TCGA.X7.A8DG.01 TCGA.X7.A8D9.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.5V.A9RR.01 TCGA.4V.A9QI.01 TCGA.ZB.A96C.01 TCGA.4V.A9QX.01 TCGA.XU.A931.01 TCGA.ZB.A961.01 
#&gt;           &quot;032&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;04&quot;           &quot;031&quot; 
#&gt; TCGA.4X.A9FB.01 TCGA.YT.A95E.01 TCGA.X7.A8D7.01 TCGA.4V.A9QQ.01 TCGA.ZB.A969.01 TCGA.X7.A8M4.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8RC.01 TCGA.4V.A9QJ.01 TCGA.XM.AAZ2.01 TCGA.X7.A8M1.01 TCGA.XM.A8RG.01 TCGA.4X.A9FD.01 
#&gt;           &quot;031&quot;            &quot;01&quot;            &quot;02&quot;           &quot;032&quot;            &quot;02&quot;           &quot;034&quot; 
#&gt; TCGA.X7.A8D6.01 TCGA.ZC.AAAF.01 TCGA.3G.AB0Q.01 TCGA.4X.A9FA.01 TCGA.5K.AAAP.01 TCGA.XM.A8RF.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;           &quot;032&quot;            &quot;02&quot; 
#&gt; TCGA.4X.A9FC.01 TCGA.3T.AA9L.01 TCGA.XU.A92W.01 TCGA.X7.A8DI.01 TCGA.ZL.A9V6.01 TCGA.XU.AAXY.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QU.01 TCGA.X7.A8DF.01 TCGA.XU.A932.01 TCGA.XU.A92Z.01 TCGA.3G.AB0O.01 TCGA.XU.A92X.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot;            &quot;01&quot;           &quot;031&quot; 
#&gt; TCGA.XU.A92O.01 TCGA.5G.A9ZZ.01 TCGA.X7.A8M7.01 TCGA.XM.A8R9.01 TCGA.XM.AAZ1.01 TCGA.X7.A8DE.01 
#&gt;            &quot;02&quot;           &quot;034&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8D7.11 TCGA.ZB.A962.01 TCGA.YT.A95D.01 TCGA.X7.A8M8.01 TCGA.X7.A8D6.11 TCGA.4V.A9QT.01 
#&gt;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.3G.AB14.01 TCGA.5U.AB0D.01 TCGA.YT.A95F.01 TCGA.XM.A8RL.01 TCGA.4V.A9QR.01 TCGA.XM.A8RI.01 
#&gt;           &quot;031&quot;            &quot;04&quot;           &quot;033&quot;            &quot;01&quot;           &quot;034&quot;           &quot;031&quot; 
#&gt; TCGA.XM.A8RE.01 TCGA.XM.A8RH.01 TCGA.ZC.AAAH.01 TCGA.XH.A853.01 TCGA.X7.A8DD.01 TCGA.4V.A9QL.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.ZB.A96A.01 TCGA.XU.AAY0.01 TCGA.XM.A8RB.01 TCGA.ZB.A96R.01 TCGA.ZB.A96V.01 TCGA.XM.A8RD.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8M0.01 TCGA.ZB.A96I.01 TCGA.ZB.A96F.01 TCGA.X7.A8DC.01 TCGA.X7.A8M5.01 TCGA.ZB.A966.01 
#&gt;           &quot;033&quot;            &quot;04&quot;           &quot;031&quot;            &quot;01&quot;            &quot;04&quot;            &quot;04&quot; 
#&gt; TCGA.XU.A92V.01 TCGA.YT.A95H.01 TCGA.ZC.AAAA.01 TCGA.XU.A92R.01 TCGA.YT.A95G.01 TCGA.XU.A933.01 
#&gt;            &quot;04&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot; 
#&gt; TCGA.XU.A92U.01 TCGA.3Q.A9WF.01 TCGA.XU.AAXV.01 TCGA.X7.A8D8.01 TCGA.ZB.A96L.01 TCGA.XU.AAXW.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QW.01 TCGA.XU.AAXZ.01 TCGA.X7.A8DB.01 TCGA.ZB.A96O.01 TCGA.ZB.A96H.01 TCGA.4V.A9QM.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;           &quot;032&quot; 
#&gt; TCGA.XU.AAY1.01 TCGA.4V.A9QS.01 TCGA.XU.A92T.01 TCGA.X7.A8M6.01 TCGA.3G.AB0T.01 TCGA.ZC.AAA7.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot; 
#&gt; TCGA.4X.A9F9.01 TCGA.XU.A92Y.01 TCGA.ZB.A96B.01 TCGA.3G.AB19.01 TCGA.XM.AAZ3.01 TCGA.X7.A8M3.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;04&quot; 
#&gt; TCGA.ZB.A964.01 TCGA.5U.AB0E.01 TCGA.XU.A92Q.01 TCGA.ZB.A96P.01 TCGA.ZB.A96E.01 TCGA.ZB.A963.01 
#&gt;            &quot;02&quot;           &quot;031&quot;            &quot;02&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-4-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-4-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-5'>
<p><a id='tab-get-classes-from-hierarchical-partition-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 10559))
</code></pre>

<pre><code>#&gt; TCGA.3S.A8YW.01 TCGA.ZB.A96K.01 TCGA.XU.A930.01 TCGA.ZB.A965.01 TCGA.4V.A9QN.01 TCGA.ZB.A96G.01 
#&gt;            &quot;04&quot;           &quot;032&quot;           &quot;031&quot;            &quot;02&quot;            &quot;04&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8R8.01 TCGA.XU.AAXX.01 TCGA.ZT.A8OM.01 TCGA.3S.AAYX.01 TCGA.ZB.A96M.01 TCGA.XU.A936.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot;            &quot;04&quot; 
#&gt; TCGA.5U.AB0F.01 TCGA.X7.A8DJ.01 TCGA.ZB.A96D.01 TCGA.ZB.A96Q.01 TCGA.X7.A8DG.01 TCGA.X7.A8D9.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.5V.A9RR.01 TCGA.4V.A9QI.01 TCGA.ZB.A96C.01 TCGA.4V.A9QX.01 TCGA.XU.A931.01 TCGA.ZB.A961.01 
#&gt;           &quot;032&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;04&quot;           &quot;031&quot; 
#&gt; TCGA.4X.A9FB.01 TCGA.YT.A95E.01 TCGA.X7.A8D7.01 TCGA.4V.A9QQ.01 TCGA.ZB.A969.01 TCGA.X7.A8M4.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8RC.01 TCGA.4V.A9QJ.01 TCGA.XM.AAZ2.01 TCGA.X7.A8M1.01 TCGA.XM.A8RG.01 TCGA.4X.A9FD.01 
#&gt;           &quot;031&quot;            &quot;01&quot;            &quot;02&quot;           &quot;032&quot;            &quot;02&quot;           &quot;034&quot; 
#&gt; TCGA.X7.A8D6.01 TCGA.ZC.AAAF.01 TCGA.3G.AB0Q.01 TCGA.4X.A9FA.01 TCGA.5K.AAAP.01 TCGA.XM.A8RF.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;           &quot;032&quot;            &quot;02&quot; 
#&gt; TCGA.4X.A9FC.01 TCGA.3T.AA9L.01 TCGA.XU.A92W.01 TCGA.X7.A8DI.01 TCGA.ZL.A9V6.01 TCGA.XU.AAXY.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QU.01 TCGA.X7.A8DF.01 TCGA.XU.A932.01 TCGA.XU.A92Z.01 TCGA.3G.AB0O.01 TCGA.XU.A92X.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot;            &quot;01&quot;           &quot;031&quot; 
#&gt; TCGA.XU.A92O.01 TCGA.5G.A9ZZ.01 TCGA.X7.A8M7.01 TCGA.XM.A8R9.01 TCGA.XM.AAZ1.01 TCGA.X7.A8DE.01 
#&gt;            &quot;02&quot;           &quot;034&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8D7.11 TCGA.ZB.A962.01 TCGA.YT.A95D.01 TCGA.X7.A8M8.01 TCGA.X7.A8D6.11 TCGA.4V.A9QT.01 
#&gt;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.3G.AB14.01 TCGA.5U.AB0D.01 TCGA.YT.A95F.01 TCGA.XM.A8RL.01 TCGA.4V.A9QR.01 TCGA.XM.A8RI.01 
#&gt;           &quot;031&quot;            &quot;04&quot;           &quot;033&quot;            &quot;01&quot;           &quot;034&quot;           &quot;031&quot; 
#&gt; TCGA.XM.A8RE.01 TCGA.XM.A8RH.01 TCGA.ZC.AAAH.01 TCGA.XH.A853.01 TCGA.X7.A8DD.01 TCGA.4V.A9QL.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;033&quot; 
#&gt; TCGA.ZB.A96A.01 TCGA.XU.AAY0.01 TCGA.XM.A8RB.01 TCGA.ZB.A96R.01 TCGA.ZB.A96V.01 TCGA.XM.A8RD.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8M0.01 TCGA.ZB.A96I.01 TCGA.ZB.A96F.01 TCGA.X7.A8DC.01 TCGA.X7.A8M5.01 TCGA.ZB.A966.01 
#&gt;           &quot;033&quot;            &quot;04&quot;           &quot;031&quot;            &quot;01&quot;            &quot;04&quot;            &quot;04&quot; 
#&gt; TCGA.XU.A92V.01 TCGA.YT.A95H.01 TCGA.ZC.AAAA.01 TCGA.XU.A92R.01 TCGA.YT.A95G.01 TCGA.XU.A933.01 
#&gt;            &quot;04&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot; 
#&gt; TCGA.XU.A92U.01 TCGA.3Q.A9WF.01 TCGA.XU.AAXV.01 TCGA.X7.A8D8.01 TCGA.ZB.A96L.01 TCGA.XU.AAXW.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;           &quot;032&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QW.01 TCGA.XU.AAXZ.01 TCGA.X7.A8DB.01 TCGA.ZB.A96O.01 TCGA.ZB.A96H.01 TCGA.4V.A9QM.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;           &quot;032&quot; 
#&gt; TCGA.XU.AAY1.01 TCGA.4V.A9QS.01 TCGA.XU.A92T.01 TCGA.X7.A8M6.01 TCGA.3G.AB0T.01 TCGA.ZC.AAA7.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot; 
#&gt; TCGA.4X.A9F9.01 TCGA.XU.A92Y.01 TCGA.ZB.A96B.01 TCGA.3G.AB19.01 TCGA.XM.AAZ3.01 TCGA.X7.A8M3.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;04&quot; 
#&gt; TCGA.ZB.A964.01 TCGA.5U.AB0E.01 TCGA.XU.A92Q.01 TCGA.ZB.A96P.01 TCGA.ZB.A96E.01 TCGA.ZB.A963.01 
#&gt;            &quot;02&quot;           &quot;031&quot;            &quot;02&quot;            &quot;01&quot;           &quot;032&quot;            &quot;01&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-5-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-5-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-6'>
<p><a id='tab-get-classes-from-hierarchical-partition-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 54876))
</code></pre>

<pre><code>#&gt; TCGA.3S.A8YW.01 TCGA.ZB.A96K.01 TCGA.XU.A930.01 TCGA.ZB.A965.01 TCGA.4V.A9QN.01 TCGA.ZB.A96G.01 
#&gt;            &quot;04&quot;            &quot;03&quot;            &quot;03&quot;            &quot;02&quot;            &quot;04&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8R8.01 TCGA.XU.AAXX.01 TCGA.ZT.A8OM.01 TCGA.3S.AAYX.01 TCGA.ZB.A96M.01 TCGA.XU.A936.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;04&quot; 
#&gt; TCGA.5U.AB0F.01 TCGA.X7.A8DJ.01 TCGA.ZB.A96D.01 TCGA.ZB.A96Q.01 TCGA.X7.A8DG.01 TCGA.X7.A8D9.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot; 
#&gt; TCGA.5V.A9RR.01 TCGA.4V.A9QI.01 TCGA.ZB.A96C.01 TCGA.4V.A9QX.01 TCGA.XU.A931.01 TCGA.ZB.A961.01 
#&gt;            &quot;03&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;04&quot;            &quot;03&quot; 
#&gt; TCGA.4X.A9FB.01 TCGA.YT.A95E.01 TCGA.X7.A8D7.01 TCGA.4V.A9QQ.01 TCGA.ZB.A969.01 TCGA.X7.A8M4.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.XM.A8RC.01 TCGA.4V.A9QJ.01 TCGA.XM.AAZ2.01 TCGA.X7.A8M1.01 TCGA.XM.A8RG.01 TCGA.4X.A9FD.01 
#&gt;            &quot;03&quot;            &quot;01&quot;            &quot;02&quot;            &quot;03&quot;            &quot;02&quot;            &quot;03&quot; 
#&gt; TCGA.X7.A8D6.01 TCGA.ZC.AAAF.01 TCGA.3G.AB0Q.01 TCGA.4X.A9FA.01 TCGA.5K.AAAP.01 TCGA.XM.A8RF.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;03&quot;            &quot;02&quot; 
#&gt; TCGA.4X.A9FC.01 TCGA.3T.AA9L.01 TCGA.XU.A92W.01 TCGA.X7.A8DI.01 TCGA.ZL.A9V6.01 TCGA.XU.AAXY.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QU.01 TCGA.X7.A8DF.01 TCGA.XU.A932.01 TCGA.XU.A92Z.01 TCGA.3G.AB0O.01 TCGA.XU.A92X.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot;            &quot;01&quot;            &quot;03&quot; 
#&gt; TCGA.XU.A92O.01 TCGA.5G.A9ZZ.01 TCGA.X7.A8M7.01 TCGA.XM.A8R9.01 TCGA.XM.AAZ1.01 TCGA.X7.A8DE.01 
#&gt;            &quot;02&quot;            &quot;03&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8D7.11 TCGA.ZB.A962.01 TCGA.YT.A95D.01 TCGA.X7.A8M8.01 TCGA.X7.A8D6.11 TCGA.4V.A9QT.01 
#&gt;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.3G.AB14.01 TCGA.5U.AB0D.01 TCGA.YT.A95F.01 TCGA.XM.A8RL.01 TCGA.4V.A9QR.01 TCGA.XM.A8RI.01 
#&gt;            &quot;03&quot;            &quot;04&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.XM.A8RE.01 TCGA.XM.A8RH.01 TCGA.ZC.AAAH.01 TCGA.XH.A853.01 TCGA.X7.A8DD.01 TCGA.4V.A9QL.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot; 
#&gt; TCGA.ZB.A96A.01 TCGA.XU.AAY0.01 TCGA.XM.A8RB.01 TCGA.ZB.A96R.01 TCGA.ZB.A96V.01 TCGA.XM.A8RD.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot;            &quot;01&quot; 
#&gt; TCGA.X7.A8M0.01 TCGA.ZB.A96I.01 TCGA.ZB.A96F.01 TCGA.X7.A8DC.01 TCGA.X7.A8M5.01 TCGA.ZB.A966.01 
#&gt;            &quot;03&quot;            &quot;04&quot;            &quot;03&quot;            &quot;01&quot;            &quot;04&quot;            &quot;04&quot; 
#&gt; TCGA.XU.A92V.01 TCGA.YT.A95H.01 TCGA.ZC.AAAA.01 TCGA.XU.A92R.01 TCGA.YT.A95G.01 TCGA.XU.A933.01 
#&gt;            &quot;04&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot; 
#&gt; TCGA.XU.A92U.01 TCGA.3Q.A9WF.01 TCGA.XU.AAXV.01 TCGA.X7.A8D8.01 TCGA.ZB.A96L.01 TCGA.XU.AAXW.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;02&quot;            &quot;01&quot; 
#&gt; TCGA.4V.A9QW.01 TCGA.XU.AAXZ.01 TCGA.X7.A8DB.01 TCGA.ZB.A96O.01 TCGA.ZB.A96H.01 TCGA.4V.A9QM.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;03&quot; 
#&gt; TCGA.XU.AAY1.01 TCGA.4V.A9QS.01 TCGA.XU.A92T.01 TCGA.X7.A8M6.01 TCGA.3G.AB0T.01 TCGA.ZC.AAA7.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;04&quot; 
#&gt; TCGA.4X.A9F9.01 TCGA.XU.A92Y.01 TCGA.ZB.A96B.01 TCGA.3G.AB19.01 TCGA.XM.AAZ3.01 TCGA.X7.A8M3.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;04&quot; 
#&gt; TCGA.ZB.A964.01 TCGA.5U.AB0E.01 TCGA.XU.A92Q.01 TCGA.ZB.A96P.01 TCGA.ZB.A96E.01 TCGA.ZB.A963.01 
#&gt;            &quot;02&quot;            &quot;03&quot;            &quot;02&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-6-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-6-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>



### Top rows heatmap

Heatmaps of the top rows:





```r
top_rows_heatmap(res_rh)
```

![plot of chunk top-rows-heatmap](figure_cola/top-rows-heatmap-1.png)

```
#> Error in h(simpleError(msg, call)) : 
#>   error in evaluating the argument 'object' in selecting a method for function 'draw': no applicable method for 'height' applied to an object of class "list"
```

Top rows on each node:


```r
top_rows_overlap(res_rh, method = "upset")
```

![plot of chunk top-rows-overlap](figure_cola/top-rows-overlap-1.png)


### UMAP plot

UMAP plot which shows how samples are separated.




<script>
$( function() {
	$( '#tabs-dimension-reduction-by-depth' ).tabs();
} );
</script>
<div id='tabs-dimension-reduction-by-depth'>
<ul>
<li><a href='#tab-dimension-reduction-by-depth-1'>n_signatures ≥ 3265</a></li>
<li><a href='#tab-dimension-reduction-by-depth-2'>n_signatures ≥ 4048</a></li>
<li><a href='#tab-dimension-reduction-by-depth-3'>n_signatures ≥ 7591</a></li>
<li><a href='#tab-dimension-reduction-by-depth-4'>n_signatures ≥ 8310</a></li>
<li><a href='#tab-dimension-reduction-by-depth-5'>n_signatures ≥ 10559</a></li>
<li><a href='#tab-dimension-reduction-by-depth-6'>n_signatures ≥ 54876</a></li>
</ul>
<div id='tab-dimension-reduction-by-depth-1'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3265),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3265),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-1-1.png" title="plot of chunk tab-dimension-reduction-by-depth-1" alt="plot of chunk tab-dimension-reduction-by-depth-1" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-2'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 4048),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 4048),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-2-1.png" title="plot of chunk tab-dimension-reduction-by-depth-2" alt="plot of chunk tab-dimension-reduction-by-depth-2" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-3'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 7591),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 7591),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-3-1.png" title="plot of chunk tab-dimension-reduction-by-depth-3" alt="plot of chunk tab-dimension-reduction-by-depth-3" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-4'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 8310),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 8310),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-4-1.png" title="plot of chunk tab-dimension-reduction-by-depth-4" alt="plot of chunk tab-dimension-reduction-by-depth-4" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-5'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 10559),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 10559),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-5-1.png" title="plot of chunk tab-dimension-reduction-by-depth-5" alt="plot of chunk tab-dimension-reduction-by-depth-5" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-6'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 54876),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 54876),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-6-1.png" title="plot of chunk tab-dimension-reduction-by-depth-6" alt="plot of chunk tab-dimension-reduction-by-depth-6" width="100%" /></p>

</div>
</div>




### Signature heatmap

Signatures on the heatmap are the union of all signatures found on every node
on the hierarchy. The number of k-means on rows are automatically selected by the function.




<script>
$( function() {
	$( '#tabs-get-signatures-from-hierarchical-partition' ).tabs();
} );
</script>
<div id='tabs-get-signatures-from-hierarchical-partition'>
<ul>
<li><a href='#tab-get-signatures-from-hierarchical-partition-1'>n_signatures ≥ 3265</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-2'>n_signatures ≥ 4048</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-3'>n_signatures ≥ 7591</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-4'>n_signatures ≥ 8310</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-5'>n_signatures ≥ 10559</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-6'>n_signatures ≥ 54876</a></li>
</ul>
<div id='tab-get-signatures-from-hierarchical-partition-1'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 3265))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-1-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-1"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-2'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 4048))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-2-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-2"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-3'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 7591))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-3-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-3"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-4'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 8310))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-4-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-4"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-5'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 10559))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-5-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-5"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-6'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 54876))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-6-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-6"/></p>

</div>
</div>




Compare signatures from different nodes:


```r
compare_signatures(res_rh, verbose = FALSE)
```

![plot of chunk unnamed-chunk-24](figure_cola/unnamed-chunk-24-1.png)

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs. Note it only works on every node and the final signatures
are the union of all signatures of all nodes.


```r
# code only for demonstration
# e.g. to show the top 500 most significant rows on each node.
tb = get_signature(res_rh, top_signatures = 500)
```


## Results for each node


---------------------------------------------------




### Node0


Child nodes: 
                [Node01](#Node01)
        ,
                [Node02](#Node02)
        ,
                [Node03](#Node03)
        ,
                [Node04](#Node04)
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["0"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 126 columns.
#>   Top rows (1000) are extracted by 'SD' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 5.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-0-collect-plots](figure_cola/node-0-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-0-select-partition-number](figure_cola/node-0-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           0.988       0.996         0.3939 0.610   0.610
#> 3 3 1.000           0.956       0.982         0.4981 0.745   0.600
#> 4 4 1.000           0.984       0.994         0.0789 0.934   0.844
#> 5 5 0.987           0.950       0.962         0.0448 0.949   0.865
#> 6 6 0.797           0.926       0.876         0.1453 0.847   0.557
#> 7 7 0.732           0.807       0.850         0.0407 0.984   0.920
#> 8 8 0.708           0.727       0.806         0.0219 0.985   0.919
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 5
#> attr(,"optional")
#> [1] 2 3 4
```

There is also optional best $k$ = 2 3 4 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-0-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-0-get-classes'>
<ul>
<li><a href='#tab-node-0-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-0-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-0-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-0-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-0-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-0-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-0-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-0-get-classes-1'>
<p><a id='tab-node-0-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2
#&gt; TCGA.3S.A8YW.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A96K.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A930.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A965.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4V.A9QN.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A96G.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8R8.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.AAXX.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZT.A8OM.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.3S.AAYX.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96M.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A936.01     1   1.000    -0.0018 0.50 0.50
#&gt; TCGA.5U.AB0F.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DJ.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96D.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96Q.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DG.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8D9.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.5V.A9RR.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4V.A9QI.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96C.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4V.A9QX.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A931.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A961.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4X.A9FB.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.YT.A95E.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8D7.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QQ.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A969.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.X7.A8M4.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RC.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QJ.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.AAZ2.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.X7.A8M1.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RG.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4X.A9FD.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8D6.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZC.AAAF.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.3G.AB0Q.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4X.A9FA.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.5K.AAAP.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RF.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4X.A9FC.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.3T.AA9L.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92W.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DI.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZL.A9V6.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.XU.AAXY.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QU.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DF.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A932.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92Z.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.3G.AB0O.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92X.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92O.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.5G.A9ZZ.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8M7.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8R9.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.AAZ1.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DE.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8D7.11     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A962.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.YT.A95D.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.X7.A8M8.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8D6.11     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QT.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.3G.AB14.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.5U.AB0D.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.YT.A95F.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RL.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QR.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RI.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RE.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RH.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZC.AAAH.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XH.A853.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DD.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QL.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96A.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.AAY0.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RB.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96R.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96V.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XM.A8RD.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8M0.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96I.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A96F.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DC.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8M5.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A966.01     2   0.141     0.9794 0.02 0.98
#&gt; TCGA.XU.A92V.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.YT.A95H.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZC.AAAA.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92R.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.YT.A95G.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A933.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.XU.A92U.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.3Q.A9WF.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.AAXV.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8D8.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A96L.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.XU.AAXW.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QW.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.AAXZ.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.X7.A8DB.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96O.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96H.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4V.A9QM.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.AAY1.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.4V.A9QS.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92T.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.X7.A8M6.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.3G.AB0T.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZC.AAA7.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.4X.A9F9.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92Y.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96B.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.3G.AB19.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.XM.AAZ3.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.X7.A8M3.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A964.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.5U.AB0E.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.XU.A92Q.01     2   0.000     0.9994 0.00 1.00
#&gt; TCGA.ZB.A96P.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A96E.01     1   0.000     0.9945 1.00 0.00
#&gt; TCGA.ZB.A963.01     1   0.000     0.9945 1.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-1-a').parent().next().next().hide();
$('#tab-node-0-get-classes-1-a').click(function(){
  $('#tab-node-0-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-2'>
<p><a id='tab-node-0-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.3S.A8YW.01     2  0.1529      0.925 0.00 0.96 0.04
#&gt; TCGA.ZB.A96K.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XU.A930.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.ZB.A965.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.4V.A9QN.01     3  0.6192      0.291 0.00 0.42 0.58
#&gt; TCGA.ZB.A96G.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XM.A8R8.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.AAXX.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZT.A8OM.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.3S.AAYX.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96M.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XU.A936.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.5U.AB0F.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8DJ.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96D.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96Q.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8DG.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8D9.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.5V.A9RR.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.4V.A9QI.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96C.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.4V.A9QX.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A931.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.ZB.A961.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.4X.A9FB.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.YT.A95E.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8D7.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.4V.A9QQ.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A969.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XM.A8RC.01     1  0.2537      0.913 0.92 0.00 0.08
#&gt; TCGA.4V.A9QJ.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XM.AAZ2.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.X7.A8M1.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XM.A8RG.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.4X.A9FD.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.X7.A8D6.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.3G.AB0Q.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.4X.A9FA.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.5K.AAAP.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XM.A8RF.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.4X.A9FC.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.3T.AA9L.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A92W.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8DI.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZL.A9V6.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.XU.AAXY.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.4V.A9QU.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8DF.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A932.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A92Z.01     3  0.5560      0.579 0.00 0.30 0.70
#&gt; TCGA.3G.AB0O.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A92X.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XU.A92O.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.5G.A9ZZ.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.X7.A8M7.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XM.A8R9.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XM.AAZ1.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8DE.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8D7.11     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A962.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.YT.A95D.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.X7.A8M8.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8D6.11     1  0.0892      0.978 0.98 0.00 0.02
#&gt; TCGA.4V.A9QT.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.3G.AB14.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.5U.AB0D.01     2  0.5706      0.499 0.00 0.68 0.32
#&gt; TCGA.YT.A95F.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XM.A8RL.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.4V.A9QR.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XM.A8RI.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XM.A8RE.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XM.A8RH.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZC.AAAH.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XH.A853.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8DD.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.4V.A9QL.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.ZB.A96A.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.AAY0.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XM.A8RB.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96R.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96V.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XM.A8RD.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8M0.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.ZB.A96I.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.ZB.A96F.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.X7.A8DC.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8M5.01     3  0.5948      0.453 0.00 0.36 0.64
#&gt; TCGA.ZB.A966.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XU.A92V.01     2  0.6126      0.292 0.00 0.60 0.40
#&gt; TCGA.YT.A95H.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZC.AAAA.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A92R.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.YT.A95G.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A933.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.XU.A92U.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.3Q.A9WF.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.AAXV.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8D8.01     3  0.4291      0.769 0.00 0.18 0.82
#&gt; TCGA.ZB.A96L.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.XU.AAXW.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.4V.A9QW.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.AAXZ.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.X7.A8DB.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96O.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96H.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.4V.A9QM.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XU.AAY1.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.4V.A9QS.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A92T.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.X7.A8M6.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.3G.AB0T.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZC.AAA7.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.4X.A9F9.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.XU.A92Y.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96B.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.3G.AB19.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.XM.AAZ3.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.X7.A8M3.01     3  0.2959      0.862 0.00 0.10 0.90
#&gt; TCGA.ZB.A964.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.5U.AB0E.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.XU.A92Q.01     2  0.0000      0.962 0.00 1.00 0.00
#&gt; TCGA.ZB.A96P.01     1  0.0000      0.999 1.00 0.00 0.00
#&gt; TCGA.ZB.A96E.01     3  0.0000      0.953 0.00 0.00 1.00
#&gt; TCGA.ZB.A963.01     1  0.0000      0.999 1.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-2-a').parent().next().next().hide();
$('#tab-node-0-get-classes-2-a').click(function(){
  $('#tab-node-0-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-3'>
<p><a id='tab-node-0-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2   p3   p4
#&gt; TCGA.3S.A8YW.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.ZB.A96K.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XU.A930.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.ZB.A965.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4V.A9QN.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.ZB.A96G.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XM.A8R8.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.AAXX.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZT.A8OM.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.3S.AAYX.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96M.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XU.A936.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.5U.AB0F.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8DJ.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96D.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96Q.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.X7.A8DG.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8D9.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.5V.A9RR.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.4V.A9QI.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96C.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4V.A9QX.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A931.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.ZB.A961.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.4X.A9FB.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.YT.A95E.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8D7.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.4V.A9QQ.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A969.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XM.A8RC.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.4V.A9QJ.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XM.AAZ2.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.X7.A8M1.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XM.A8RG.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4X.A9FD.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.X7.A8D6.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.3G.AB0Q.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4X.A9FA.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.5K.AAAP.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XM.A8RF.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4X.A9FC.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.3T.AA9L.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A92W.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8DI.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZL.A9V6.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.XU.AAXY.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.4V.A9QU.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8DF.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A932.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A92Z.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.3G.AB0O.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A92X.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XU.A92O.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.5G.A9ZZ.01     3  0.4713      0.440 0.00  0 0.64 0.36
#&gt; TCGA.X7.A8M7.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XM.A8R9.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XM.AAZ1.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8DE.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8D7.11     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A962.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.YT.A95D.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.X7.A8M8.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8D6.11     1  0.4790      0.383 0.62  0 0.38 0.00
#&gt; TCGA.4V.A9QT.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.3G.AB14.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.5U.AB0D.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.YT.A95F.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XM.A8RL.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.4V.A9QR.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XM.A8RI.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XM.A8RE.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XM.A8RH.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZC.AAAH.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XH.A853.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8DD.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.4V.A9QL.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.ZB.A96A.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.AAY0.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XM.A8RB.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96R.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96V.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.XM.A8RD.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8M0.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.ZB.A96I.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.ZB.A96F.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.X7.A8DC.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8M5.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.ZB.A966.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.XU.A92V.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.YT.A95H.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZC.AAAA.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A92R.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.YT.A95G.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A933.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.XU.A92U.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.3Q.A9WF.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.AAXV.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8D8.01     3  0.0707      0.965 0.00  0 0.98 0.02
#&gt; TCGA.ZB.A96L.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.XU.AAXW.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.4V.A9QW.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.AAXZ.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8DB.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96O.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96H.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4V.A9QM.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XU.AAY1.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.4V.A9QS.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A92T.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.X7.A8M6.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.3G.AB0T.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZC.AAA7.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.4X.A9F9.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.XU.A92Y.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96B.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.3G.AB19.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.XM.AAZ3.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.X7.A8M3.01     4  0.0000      1.000 0.00  0 0.00 1.00
#&gt; TCGA.ZB.A964.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.5U.AB0E.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.ZB.A96P.01     1  0.0000      0.994 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96E.01     3  0.0000      0.983 0.00  0 1.00 0.00
#&gt; TCGA.ZB.A963.01     1  0.0000      0.994 1.00  0 0.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-3-a').parent().next().next().hide();
$('#tab-node-0-get-classes-3-a').click(function(){
  $('#tab-node-0-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-4'>
<p><a id='tab-node-0-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.3S.A8YW.01     4  0.0000      0.969 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.ZB.A96K.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.XU.A930.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A965.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QN.01     4  0.1043      0.967 0.00 0.00 0.00 0.96 0.04
#&gt; TCGA.ZB.A96G.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XM.A8R8.01     3  0.4287      0.204 0.46 0.00 0.54 0.00 0.00
#&gt; TCGA.XU.AAXX.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZT.A8OM.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.3S.AAYX.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96M.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.XU.A936.01     4  0.0000      0.969 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.5U.AB0F.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DJ.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.ZB.A96D.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96Q.01     1  0.5050      0.602 0.70 0.00 0.12 0.00 0.18
#&gt; TCGA.X7.A8DG.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8D9.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.5V.A9RR.01     5  0.1732      0.940 0.00 0.00 0.08 0.00 0.92
#&gt; TCGA.4V.A9QI.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.ZB.A96C.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QX.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A931.01     4  0.1043      0.967 0.00 0.00 0.00 0.96 0.04
#&gt; TCGA.ZB.A961.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.4X.A9FB.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.YT.A95E.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8D7.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QQ.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A969.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XM.A8RC.01     3  0.0609      0.889 0.00 0.00 0.98 0.00 0.02
#&gt; TCGA.4V.A9QJ.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XM.AAZ2.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M1.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.XM.A8RG.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FD.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8D6.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.3G.AB0Q.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FA.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.5K.AAAP.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.XM.A8RF.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FC.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.3T.AA9L.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92W.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8DI.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZL.A9V6.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAXY.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.4V.A9QU.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DF.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.A932.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.A92Z.01     4  0.1410      0.958 0.00 0.00 0.00 0.94 0.06
#&gt; TCGA.3G.AB0O.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.A92X.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     2  0.0609      0.983 0.00 0.98 0.00 0.00 0.02
#&gt; TCGA.5G.A9ZZ.01     3  0.1410      0.858 0.00 0.00 0.94 0.06 0.00
#&gt; TCGA.X7.A8M7.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XM.A8R9.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.AAZ1.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8DE.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D7.11     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A962.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95D.01     2  0.0609      0.983 0.00 0.98 0.00 0.00 0.02
#&gt; TCGA.X7.A8M8.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8D6.11     3  0.1410      0.839 0.06 0.00 0.94 0.00 0.00
#&gt; TCGA.4V.A9QT.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.3G.AB14.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.5U.AB0D.01     4  0.0000      0.969 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.YT.A95F.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.XM.A8RL.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.4V.A9QR.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8RI.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8RE.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RH.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZC.AAAH.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XH.A853.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8DD.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QL.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.ZB.A96A.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.AAY0.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RB.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96R.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.ZB.A96V.01     4  0.2516      0.827 0.00 0.00 0.14 0.86 0.00
#&gt; TCGA.XM.A8RD.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M0.01     3  0.1732      0.827 0.00 0.00 0.92 0.00 0.08
#&gt; TCGA.ZB.A96I.01     4  0.1043      0.967 0.00 0.00 0.00 0.96 0.04
#&gt; TCGA.ZB.A96F.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8DC.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8M5.01     4  0.1410      0.958 0.00 0.00 0.00 0.94 0.06
#&gt; TCGA.ZB.A966.01     4  0.0000      0.969 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XU.A92V.01     5  0.2929      0.703 0.00 0.00 0.00 0.18 0.82
#&gt; TCGA.YT.A95H.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.ZC.AAAA.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.A92R.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95G.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A933.01     4  0.0000      0.969 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XU.A92U.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.3Q.A9WF.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.AAXV.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D8.01     5  0.1732      0.940 0.00 0.00 0.08 0.00 0.92
#&gt; TCGA.ZB.A96L.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAXW.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QW.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.AAXZ.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.X7.A8DB.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96O.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96H.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QM.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.XU.AAY1.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QS.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92T.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M6.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.3G.AB0T.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.ZC.AAA7.01     4  0.0000      0.969 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.4X.A9F9.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Y.01     1  0.0000      0.966 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96B.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.3G.AB19.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.AAZ3.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M3.01     4  0.1043      0.967 0.00 0.00 0.00 0.96 0.04
#&gt; TCGA.ZB.A964.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0E.01     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.0000      0.998 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96P.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.ZB.A96E.01     5  0.2280      0.967 0.00 0.00 0.12 0.00 0.88
#&gt; TCGA.ZB.A963.01     1  0.1410      0.966 0.94 0.00 0.00 0.00 0.06
</code></pre>

<script>
$('#tab-node-0-get-classes-4-a').parent().next().next().hide();
$('#tab-node-0-get-classes-4-a').click(function(){
  $('#tab-node-0-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-5'>
<p><a id='tab-node-0-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.3S.A8YW.01     4  0.0547      0.913 0.00 0.00 0.00 0.98 0.00 0.02
#&gt; TCGA.ZB.A96K.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.XU.A930.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A965.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QN.01     4  0.2631      0.894 0.00 0.00 0.00 0.82 0.00 0.18
#&gt; TCGA.ZB.A96G.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8R8.01     6  0.4723      0.743 0.18 0.00 0.14 0.00 0.00 0.68
#&gt; TCGA.XU.AAXX.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZT.A8OM.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.3S.AAYX.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZB.A96M.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.XU.A936.01     4  0.1267      0.903 0.00 0.00 0.00 0.94 0.00 0.06
#&gt; TCGA.5U.AB0F.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.X7.A8DJ.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.ZB.A96D.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.ZB.A96Q.01     1  0.5331      0.442 0.62 0.00 0.02 0.00 0.26 0.10
#&gt; TCGA.X7.A8DG.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D9.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.5V.A9RR.01     5  0.0547      0.946 0.00 0.00 0.00 0.00 0.98 0.02
#&gt; TCGA.4V.A9QI.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96C.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QX.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.XU.A931.01     4  0.2631      0.894 0.00 0.00 0.00 0.82 0.00 0.18
#&gt; TCGA.ZB.A961.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FB.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95E.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.X7.A8D7.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.4V.A9QQ.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZB.A969.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.XM.A8RC.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QJ.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.XM.AAZ2.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M1.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.XM.A8RG.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FD.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D6.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZC.AAAF.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.3G.AB0Q.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FA.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5K.AAAP.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.XM.A8RF.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FC.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.3T.AA9L.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.XU.A92W.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DI.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.ZL.A9V6.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAXY.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QU.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.X7.A8DF.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.XU.A932.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Z.01     4  0.1814      0.910 0.00 0.00 0.00 0.90 0.00 0.10
#&gt; TCGA.3G.AB0O.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92X.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     2  0.1480      0.950 0.00 0.94 0.00 0.00 0.02 0.04
#&gt; TCGA.5G.A9ZZ.01     3  0.1807      0.913 0.00 0.00 0.92 0.02 0.00 0.06
#&gt; TCGA.X7.A8M7.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8R9.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.XM.AAZ1.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.X7.A8DE.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.X7.A8D7.11     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZB.A962.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95D.01     2  0.1480      0.950 0.00 0.94 0.00 0.00 0.02 0.04
#&gt; TCGA.X7.A8M8.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D6.11     3  0.1556      0.880 0.00 0.00 0.92 0.00 0.00 0.08
#&gt; TCGA.4V.A9QT.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.3G.AB14.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0D.01     4  0.0547      0.913 0.00 0.00 0.00 0.98 0.00 0.02
#&gt; TCGA.YT.A95F.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.XM.A8RL.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QR.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RI.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RE.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.XM.A8RH.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZC.AAAH.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XH.A853.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DD.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.4V.A9QL.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.ZB.A96A.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.XU.AAY0.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.XM.A8RB.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZB.A96R.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96V.01     4  0.1807      0.894 0.00 0.00 0.02 0.92 0.00 0.06
#&gt; TCGA.XM.A8RD.01     6  0.3499      0.921 0.32 0.00 0.00 0.00 0.00 0.68
#&gt; TCGA.X7.A8M0.01     3  0.3829      0.733 0.00 0.00 0.76 0.00 0.18 0.06
#&gt; TCGA.ZB.A96I.01     4  0.2631      0.894 0.00 0.00 0.00 0.82 0.00 0.18
#&gt; TCGA.ZB.A96F.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DC.01     1  0.0937      0.921 0.96 0.00 0.00 0.00 0.00 0.04
#&gt; TCGA.X7.A8M5.01     4  0.3523      0.865 0.00 0.00 0.00 0.78 0.04 0.18
#&gt; TCGA.ZB.A966.01     4  0.1267      0.903 0.00 0.00 0.00 0.94 0.00 0.06
#&gt; TCGA.XU.A92V.01     5  0.4094      0.706 0.00 0.00 0.00 0.08 0.74 0.18
#&gt; TCGA.YT.A95H.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.ZC.AAAA.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.XU.A92R.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.YT.A95G.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.XU.A933.01     4  0.0547      0.913 0.00 0.00 0.00 0.98 0.00 0.02
#&gt; TCGA.XU.A92U.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.3Q.A9WF.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAXV.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.X7.A8D8.01     5  0.0937      0.934 0.00 0.00 0.00 0.00 0.96 0.04
#&gt; TCGA.ZB.A96L.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAXW.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.4V.A9QW.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.XU.AAXZ.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.X7.A8DB.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZB.A96O.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.ZB.A96H.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QM.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.XU.AAY1.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.4V.A9QS.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.XU.A92T.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M6.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.3G.AB0T.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.ZC.AAA7.01     4  0.1267      0.903 0.00 0.00 0.00 0.94 0.00 0.06
#&gt; TCGA.4X.A9F9.01     6  0.3756      0.911 0.40 0.00 0.00 0.00 0.00 0.60
#&gt; TCGA.XU.A92Y.01     6  0.3409      0.922 0.30 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.ZB.A96B.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.3G.AB19.01     2  0.0547      0.980 0.00 0.98 0.00 0.00 0.00 0.02
#&gt; TCGA.XM.AAZ3.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M3.01     4  0.2631      0.894 0.00 0.00 0.00 0.82 0.00 0.18
#&gt; TCGA.ZB.A964.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0E.01     3  0.0000      0.967 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.0000      0.993 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96P.01     1  0.0000      0.927 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96E.01     5  0.0547      0.969 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.ZB.A963.01     1  0.1556      0.911 0.92 0.00 0.00 0.00 0.00 0.08
</code></pre>

<script>
$('#tab-node-0-get-classes-5-a').parent().next().next().hide();
$('#tab-node-0-get-classes-5-a').click(function(){
  $('#tab-node-0-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-6'>
<p><a id='tab-node-0-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.3S.A8YW.01     4  0.4451     0.4181 0.00 0.00 0.00 0.64 0.00 0.10 0.26
#&gt; TCGA.ZB.A96K.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.XU.A930.01     3  0.0504     0.9020 0.00 0.00 0.98 0.02 0.00 0.00 0.00
#&gt; TCGA.ZB.A965.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QN.01     7  0.3294     0.6215 0.00 0.00 0.00 0.34 0.00 0.00 0.66
#&gt; TCGA.ZB.A96G.01     1  0.0000     0.9063 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8R8.01     6  0.4507     0.7158 0.08 0.00 0.04 0.06 0.00 0.76 0.06
#&gt; TCGA.XU.AAXX.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.ZT.A8OM.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.3S.AAYX.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.ZB.A96M.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.XU.A936.01     4  0.0863     0.6984 0.00 0.00 0.04 0.96 0.00 0.00 0.00
#&gt; TCGA.5U.AB0F.01     6  0.3199     0.8125 0.14 0.00 0.00 0.00 0.00 0.80 0.06
#&gt; TCGA.X7.A8DJ.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.ZB.A96D.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.ZB.A96Q.01     5  0.5686     0.4162 0.18 0.00 0.02 0.00 0.62 0.12 0.06
#&gt; TCGA.X7.A8DG.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.X7.A8D9.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.5V.A9RR.01     5  0.2912     0.7008 0.00 0.00 0.00 0.00 0.82 0.04 0.14
#&gt; TCGA.4V.A9QI.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.ZB.A96C.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QX.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.XU.A931.01     7  0.3294     0.6215 0.00 0.00 0.00 0.34 0.00 0.00 0.66
#&gt; TCGA.ZB.A961.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FB.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.YT.A95E.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.X7.A8D7.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.4V.A9QQ.01     6  0.4070     0.7892 0.30 0.00 0.00 0.02 0.00 0.66 0.02
#&gt; TCGA.ZB.A969.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.XM.A8RC.01     3  0.0863     0.8715 0.04 0.00 0.96 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QJ.01     1  0.1928     0.8952 0.90 0.00 0.00 0.00 0.00 0.08 0.02
#&gt; TCGA.XM.AAZ2.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M1.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.XM.A8RG.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FD.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D6.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.ZC.AAAF.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.3G.AB0Q.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FA.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5K.AAAP.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.XM.A8RF.01     2  0.0504     0.9467 0.00 0.98 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.4X.A9FC.01     6  0.2081     0.8207 0.14 0.00 0.00 0.00 0.00 0.86 0.00
#&gt; TCGA.3T.AA9L.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.XU.A92W.01     1  0.0000     0.9063 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DI.01     6  0.2081     0.8207 0.14 0.00 0.00 0.00 0.00 0.86 0.00
#&gt; TCGA.ZL.A9V6.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAXY.01     1  0.0000     0.9063 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QU.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.X7.A8DF.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.XU.A932.01     1  0.0000     0.9063 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Z.01     7  0.5429     0.1605 0.00 0.00 0.00 0.40 0.02 0.12 0.46
#&gt; TCGA.3G.AB0O.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.XU.A92X.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     2  0.3991     0.7033 0.00 0.72 0.00 0.00 0.02 0.04 0.22
#&gt; TCGA.5G.A9ZZ.01     3  0.3294     0.5244 0.00 0.00 0.66 0.34 0.00 0.00 0.00
#&gt; TCGA.X7.A8M7.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.XM.A8R9.01     6  0.3199     0.8125 0.14 0.00 0.00 0.00 0.00 0.80 0.06
#&gt; TCGA.XM.AAZ1.01     1  0.2278     0.8843 0.88 0.00 0.00 0.00 0.00 0.08 0.04
#&gt; TCGA.X7.A8DE.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.X7.A8D7.11     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.ZB.A962.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95D.01     2  0.3991     0.7033 0.00 0.72 0.00 0.00 0.02 0.04 0.22
#&gt; TCGA.X7.A8M8.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.X7.A8D6.11     3  0.4191     0.4606 0.00 0.00 0.64 0.00 0.00 0.30 0.06
#&gt; TCGA.4V.A9QT.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.3G.AB14.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0D.01     4  0.4451     0.4181 0.00 0.00 0.00 0.64 0.00 0.10 0.26
#&gt; TCGA.YT.A95F.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.XM.A8RL.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.4V.A9QR.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RI.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RE.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.XM.A8RH.01     6  0.4269     0.7710 0.36 0.00 0.00 0.02 0.00 0.60 0.02
#&gt; TCGA.ZC.AAAH.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.XH.A853.01     1  0.1006     0.9063 0.96 0.00 0.00 0.00 0.00 0.02 0.02
#&gt; TCGA.X7.A8DD.01     6  0.4269     0.7710 0.36 0.00 0.00 0.02 0.00 0.60 0.02
#&gt; TCGA.4V.A9QL.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.ZB.A96A.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.XU.AAY0.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.XM.A8RB.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.ZB.A96R.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.ZB.A96V.01     4  0.0863     0.6984 0.00 0.00 0.04 0.96 0.00 0.00 0.00
#&gt; TCGA.XM.A8RD.01     6  0.3052     0.8151 0.20 0.00 0.00 0.00 0.00 0.78 0.02
#&gt; TCGA.X7.A8M0.01     5  0.5638     0.0221 0.00 0.00 0.32 0.32 0.36 0.00 0.00
#&gt; TCGA.ZB.A96I.01     7  0.3294     0.6215 0.00 0.00 0.00 0.34 0.00 0.00 0.66
#&gt; TCGA.ZB.A96F.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DC.01     1  0.1664     0.9009 0.92 0.00 0.00 0.00 0.00 0.06 0.02
#&gt; TCGA.X7.A8M5.01     7  0.4574     0.4631 0.00 0.00 0.00 0.12 0.10 0.06 0.72
#&gt; TCGA.ZB.A966.01     4  0.0863     0.6984 0.00 0.00 0.04 0.96 0.00 0.00 0.00
#&gt; TCGA.XU.A92V.01     7  0.4108     0.3391 0.00 0.00 0.00 0.00 0.28 0.06 0.66
#&gt; TCGA.YT.A95H.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.ZC.AAAA.01     1  0.2016     0.8945 0.90 0.00 0.00 0.00 0.00 0.06 0.04
#&gt; TCGA.XU.A92R.01     6  0.2912     0.8146 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.YT.A95G.01     6  0.3199     0.8125 0.14 0.00 0.00 0.00 0.00 0.80 0.06
#&gt; TCGA.XU.A933.01     4  0.4451     0.4181 0.00 0.00 0.00 0.64 0.00 0.10 0.26
#&gt; TCGA.XU.A92U.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.3Q.A9WF.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.XU.AAXV.01     6  0.3086     0.8204 0.16 0.00 0.00 0.00 0.00 0.80 0.04
#&gt; TCGA.X7.A8D8.01     5  0.3519     0.6133 0.00 0.00 0.00 0.00 0.74 0.04 0.22
#&gt; TCGA.ZB.A96L.01     2  0.0863     0.9340 0.00 0.96 0.00 0.00 0.00 0.00 0.04
#&gt; TCGA.XU.AAXW.01     6  0.4269     0.7710 0.36 0.00 0.00 0.02 0.00 0.60 0.02
#&gt; TCGA.4V.A9QW.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
#&gt; TCGA.XU.AAXZ.01     1  0.2016     0.8945 0.90 0.00 0.00 0.00 0.00 0.06 0.04
#&gt; TCGA.X7.A8DB.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.ZB.A96O.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.ZB.A96H.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QM.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.XU.AAY1.01     6  0.2081     0.8207 0.14 0.00 0.00 0.00 0.00 0.86 0.00
#&gt; TCGA.4V.A9QS.01     6  0.3086     0.8204 0.16 0.00 0.00 0.00 0.00 0.80 0.04
#&gt; TCGA.XU.A92T.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M6.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.3G.AB0T.01     1  0.2016     0.8945 0.90 0.00 0.00 0.00 0.00 0.06 0.04
#&gt; TCGA.ZC.AAA7.01     4  0.0863     0.6984 0.00 0.00 0.04 0.96 0.00 0.00 0.00
#&gt; TCGA.4X.A9F9.01     6  0.4317     0.7594 0.38 0.00 0.00 0.02 0.00 0.58 0.02
#&gt; TCGA.XU.A92Y.01     6  0.2912     0.8175 0.14 0.00 0.00 0.00 0.00 0.82 0.04
#&gt; TCGA.ZB.A96B.01     1  0.0504     0.9065 0.98 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.3G.AB19.01     2  0.2422     0.8180 0.00 0.82 0.00 0.00 0.00 0.00 0.18
#&gt; TCGA.XM.AAZ3.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M3.01     7  0.3294     0.6215 0.00 0.00 0.00 0.34 0.00 0.00 0.66
#&gt; TCGA.ZB.A964.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0E.01     3  0.0000     0.9161 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.0000     0.9577 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96P.01     1  0.1006     0.8956 0.96 0.00 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.ZB.A96E.01     5  0.0504     0.8583 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.ZB.A963.01     1  0.2163     0.8858 0.88 0.00 0.00 0.00 0.00 0.10 0.02
</code></pre>

<script>
$('#tab-node-0-get-classes-6-a').parent().next().next().hide();
$('#tab-node-0-get-classes-6-a').click(function(){
  $('#tab-node-0-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-7'>
<p><a id='tab-node-0-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7   p8
#&gt; TCGA.3S.A8YW.01     7  0.5802    0.46244 0.10 0.00 0.00 0.32 0.00 0.00 0.46 0.12
#&gt; TCGA.ZB.A96K.01     5  0.0941    0.88894 0.00 0.00 0.02 0.00 0.96 0.00 0.00 0.02
#&gt; TCGA.XU.A930.01     3  0.1091    0.85101 0.00 0.00 0.94 0.06 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A965.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QN.01     7  0.0471    0.65686 0.00 0.00 0.00 0.02 0.00 0.00 0.98 0.00
#&gt; TCGA.ZB.A96G.01     1  0.3270    0.80722 0.80 0.00 0.00 0.06 0.00 0.12 0.00 0.02
#&gt; TCGA.XM.A8R8.01     6  0.4031    0.52063 0.02 0.00 0.00 0.16 0.00 0.72 0.00 0.10
#&gt; TCGA.XU.AAXX.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.ZT.A8OM.01     6  0.0471    0.70638 0.00 0.00 0.00 0.00 0.00 0.98 0.00 0.02
#&gt; TCGA.3S.AAYX.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.ZB.A96M.01     5  0.0471    0.88680 0.00 0.00 0.02 0.00 0.98 0.00 0.00 0.00
#&gt; TCGA.XU.A936.01     4  0.1804    0.69499 0.00 0.00 0.02 0.90 0.00 0.00 0.08 0.00
#&gt; TCGA.5U.AB0F.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.X7.A8DJ.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.ZB.A96D.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.ZB.A96Q.01     5  0.5988    0.39026 0.04 0.00 0.02 0.08 0.60 0.14 0.00 0.12
#&gt; TCGA.X7.A8DG.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.X7.A8D9.01     5  0.0471    0.88680 0.00 0.00 0.02 0.00 0.98 0.00 0.00 0.00
#&gt; TCGA.5V.A9RR.01     5  0.3237    0.24683 0.00 0.00 0.00 0.00 0.60 0.00 0.00 0.40
#&gt; TCGA.4V.A9QI.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.ZB.A96C.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QX.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.XU.A931.01     7  0.1275    0.64586 0.00 0.00 0.00 0.04 0.00 0.00 0.94 0.02
#&gt; TCGA.ZB.A961.01     3  0.0471    0.89145 0.00 0.00 0.98 0.02 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FB.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.YT.A95E.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.X7.A8D7.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.4V.A9QQ.01     6  0.4672    0.67037 0.28 0.00 0.00 0.00 0.02 0.60 0.00 0.10
#&gt; TCGA.ZB.A969.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.XM.A8RC.01     3  0.1091    0.84832 0.00 0.00 0.94 0.06 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QJ.01     1  0.4293    0.78196 0.68 0.00 0.00 0.10 0.00 0.20 0.00 0.02
#&gt; TCGA.XM.AAZ2.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M1.01     5  0.0941    0.88894 0.00 0.00 0.02 0.00 0.96 0.00 0.00 0.02
#&gt; TCGA.XM.A8RG.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FD.01     3  0.0000    0.90619 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D6.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.ZC.AAAF.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.3G.AB0Q.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FA.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5K.AAAP.01     5  0.0941    0.88894 0.00 0.00 0.02 0.00 0.96 0.00 0.00 0.02
#&gt; TCGA.XM.A8RF.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FC.01     6  0.1557    0.71030 0.00 0.00 0.00 0.00 0.02 0.92 0.00 0.06
#&gt; TCGA.3T.AA9L.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.XU.A92W.01     1  0.2224    0.80416 0.86 0.00 0.00 0.02 0.00 0.12 0.00 0.00
#&gt; TCGA.X7.A8DI.01     6  0.1557    0.71030 0.00 0.00 0.00 0.00 0.02 0.92 0.00 0.06
#&gt; TCGA.ZL.A9V6.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAXY.01     1  0.2224    0.80416 0.86 0.00 0.00 0.02 0.00 0.12 0.00 0.00
#&gt; TCGA.4V.A9QU.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.X7.A8DF.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.XU.A932.01     1  0.2224    0.80416 0.86 0.00 0.00 0.02 0.00 0.12 0.00 0.00
#&gt; TCGA.XU.A92Z.01     7  0.4999    0.38438 0.02 0.00 0.00 0.12 0.00 0.00 0.52 0.34
#&gt; TCGA.3G.AB0O.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.XU.A92X.01     3  0.0000    0.90619 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     8  0.3318    0.27475 0.00 0.46 0.00 0.00 0.00 0.00 0.00 0.54
#&gt; TCGA.5G.A9ZZ.01     4  0.3658    0.29992 0.00 0.00 0.40 0.58 0.00 0.00 0.00 0.02
#&gt; TCGA.X7.A8M7.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.XM.A8R9.01     6  0.1804    0.68806 0.00 0.00 0.00 0.02 0.00 0.90 0.00 0.08
#&gt; TCGA.XM.AAZ1.01     1  0.4841    0.76240 0.64 0.00 0.00 0.10 0.00 0.20 0.00 0.06
#&gt; TCGA.X7.A8DE.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.X7.A8D7.11     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.ZB.A962.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95D.01     8  0.3318    0.27475 0.00 0.46 0.00 0.00 0.00 0.00 0.00 0.54
#&gt; TCGA.X7.A8M8.01     1  0.1765    0.79829 0.88 0.00 0.00 0.00 0.00 0.12 0.00 0.00
#&gt; TCGA.X7.A8D6.11     3  0.4940    0.19854 0.00 0.00 0.48 0.02 0.00 0.40 0.00 0.10
#&gt; TCGA.4V.A9QT.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.3G.AB14.01     3  0.0000    0.90619 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0D.01     7  0.5802    0.46244 0.10 0.00 0.00 0.32 0.00 0.00 0.46 0.12
#&gt; TCGA.YT.A95F.01     5  0.0471    0.88680 0.00 0.00 0.02 0.00 0.98 0.00 0.00 0.00
#&gt; TCGA.XM.A8RL.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.4V.A9QR.01     3  0.0000    0.90619 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RI.01     3  0.0000    0.90619 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RE.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.XM.A8RH.01     6  0.4740    0.66395 0.30 0.00 0.00 0.00 0.02 0.58 0.00 0.10
#&gt; TCGA.ZC.AAAH.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.XH.A853.01     1  0.3270    0.80722 0.80 0.00 0.00 0.06 0.00 0.12 0.00 0.02
#&gt; TCGA.X7.A8DD.01     6  0.4740    0.66395 0.30 0.00 0.00 0.00 0.02 0.58 0.00 0.10
#&gt; TCGA.4V.A9QL.01     5  0.0471    0.88680 0.00 0.00 0.02 0.00 0.98 0.00 0.00 0.00
#&gt; TCGA.ZB.A96A.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.XU.AAY0.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.XM.A8RB.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.ZB.A96R.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.ZB.A96V.01     4  0.1804    0.69499 0.00 0.00 0.02 0.90 0.00 0.00 0.08 0.00
#&gt; TCGA.XM.A8RD.01     6  0.3102    0.71503 0.08 0.00 0.00 0.00 0.02 0.82 0.00 0.08
#&gt; TCGA.X7.A8M0.01     4  0.5306    0.26464 0.00 0.00 0.12 0.48 0.36 0.00 0.00 0.04
#&gt; TCGA.ZB.A96I.01     7  0.2071    0.61808 0.00 0.00 0.04 0.04 0.00 0.00 0.90 0.02
#&gt; TCGA.ZB.A96F.01     3  0.0000    0.90619 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DC.01     1  0.4865    0.77089 0.64 0.00 0.00 0.08 0.00 0.20 0.00 0.08
#&gt; TCGA.X7.A8M5.01     8  0.3658    0.08263 0.00 0.00 0.00 0.00 0.02 0.00 0.40 0.58
#&gt; TCGA.ZB.A966.01     4  0.1804    0.69499 0.00 0.00 0.02 0.90 0.00 0.00 0.08 0.00
#&gt; TCGA.XU.A92V.01     8  0.4482    0.28278 0.00 0.00 0.00 0.00 0.14 0.00 0.26 0.60
#&gt; TCGA.YT.A95H.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.ZC.AAAA.01     1  0.4841    0.76240 0.64 0.00 0.00 0.10 0.00 0.20 0.00 0.06
#&gt; TCGA.XU.A92R.01     6  0.0808    0.69266 0.00 0.00 0.00 0.00 0.00 0.96 0.00 0.04
#&gt; TCGA.YT.A95G.01     6  0.2591    0.69640 0.04 0.00 0.00 0.02 0.00 0.86 0.00 0.08
#&gt; TCGA.XU.A933.01     7  0.5938    0.44862 0.12 0.00 0.00 0.32 0.00 0.00 0.44 0.12
#&gt; TCGA.XU.A92U.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.3Q.A9WF.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.XU.AAXV.01     6  0.2348    0.71058 0.04 0.00 0.00 0.02 0.00 0.88 0.00 0.06
#&gt; TCGA.X7.A8D8.01     8  0.3299   -0.00968 0.00 0.00 0.00 0.00 0.44 0.00 0.00 0.56
#&gt; TCGA.ZB.A96L.01     2  0.1341    0.88476 0.00 0.92 0.00 0.00 0.00 0.00 0.00 0.08
#&gt; TCGA.XU.AAXW.01     6  0.4740    0.66382 0.30 0.00 0.00 0.00 0.02 0.58 0.00 0.10
#&gt; TCGA.4V.A9QW.01     1  0.5280    0.71545 0.54 0.00 0.00 0.08 0.00 0.30 0.00 0.08
#&gt; TCGA.XU.AAXZ.01     1  0.4276    0.78597 0.70 0.00 0.00 0.08 0.00 0.18 0.00 0.04
#&gt; TCGA.X7.A8DB.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.ZB.A96O.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.ZB.A96H.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QM.01     5  0.0941    0.88894 0.00 0.00 0.02 0.00 0.96 0.00 0.00 0.02
#&gt; TCGA.XU.AAY1.01     6  0.1275    0.71010 0.00 0.00 0.00 0.00 0.02 0.94 0.00 0.04
#&gt; TCGA.4V.A9QS.01     6  0.2071    0.70769 0.04 0.00 0.00 0.02 0.00 0.90 0.00 0.04
#&gt; TCGA.XU.A92T.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M6.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.3G.AB0T.01     1  0.4650    0.76662 0.66 0.00 0.00 0.08 0.00 0.20 0.00 0.06
#&gt; TCGA.ZC.AAA7.01     4  0.2265    0.67645 0.00 0.00 0.02 0.88 0.00 0.00 0.08 0.02
#&gt; TCGA.4X.A9F9.01     6  0.4798    0.65227 0.32 0.00 0.00 0.00 0.02 0.56 0.00 0.10
#&gt; TCGA.XU.A92Y.01     6  0.2591    0.69640 0.04 0.00 0.00 0.02 0.00 0.86 0.00 0.08
#&gt; TCGA.ZB.A96B.01     1  0.3002    0.80750 0.82 0.00 0.00 0.04 0.00 0.12 0.00 0.02
#&gt; TCGA.3G.AB19.01     2  0.2406    0.68709 0.00 0.80 0.00 0.00 0.00 0.00 0.00 0.20
#&gt; TCGA.XM.AAZ3.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M3.01     7  0.0471    0.65686 0.00 0.00 0.00 0.02 0.00 0.00 0.98 0.00
#&gt; TCGA.ZB.A964.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0E.01     3  0.0000    0.90619 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.0000    0.97789 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96P.01     1  0.2224    0.79070 0.86 0.00 0.00 0.00 0.00 0.12 0.00 0.02
#&gt; TCGA.ZB.A96E.01     5  0.0941    0.88894 0.00 0.00 0.02 0.00 0.96 0.00 0.00 0.02
#&gt; TCGA.ZB.A963.01     1  0.5332    0.68876 0.52 0.00 0.00 0.08 0.00 0.32 0.00 0.08
</code></pre>

<script>
$('#tab-node-0-get-classes-7-a').parent().next().next().hide();
$('#tab-node-0-get-classes-7-a').click(function(){
  $('#tab-node-0-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-0-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-0-consensus-heatmap'>
<ul>
<li><a href='#tab-node-0-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-0-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-0-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-0-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-0-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-0-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-0-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-0-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-0-membership-heatmap'>
<ul>
<li><a href='#tab-node-0-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-0-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-0-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-0-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-0-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-0-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-0-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-1-1.png" alt="plot of chunk tab-node-0-membership-heatmap-1"/></p>

</div>
<div id='tab-node-0-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-2-1.png" alt="plot of chunk tab-node-0-membership-heatmap-2"/></p>

</div>
<div id='tab-node-0-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-3-1.png" alt="plot of chunk tab-node-0-membership-heatmap-3"/></p>

</div>
<div id='tab-node-0-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-4-1.png" alt="plot of chunk tab-node-0-membership-heatmap-4"/></p>

</div>
<div id='tab-node-0-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-5-1.png" alt="plot of chunk tab-node-0-membership-heatmap-5"/></p>

</div>
<div id='tab-node-0-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-6-1.png" alt="plot of chunk tab-node-0-membership-heatmap-6"/></p>

</div>
<div id='tab-node-0-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-7-1.png" alt="plot of chunk tab-node-0-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-0-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-0-get-signatures'>
<ul>
<li><a href='#tab-node-0-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-0-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-0-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-0-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-0-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-0-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-0-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-1-1.png" alt="plot of chunk tab-node-0-get-signatures-1"/></p>

</div>
<div id='tab-node-0-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-2-1.png" alt="plot of chunk tab-node-0-get-signatures-2"/></p>

</div>
<div id='tab-node-0-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-3-1.png" alt="plot of chunk tab-node-0-get-signatures-3"/></p>

</div>
<div id='tab-node-0-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-4-1.png" alt="plot of chunk tab-node-0-get-signatures-4"/></p>

</div>
<div id='tab-node-0-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-5-1.png" alt="plot of chunk tab-node-0-get-signatures-5"/></p>

</div>
<div id='tab-node-0-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-6-1.png" alt="plot of chunk tab-node-0-get-signatures-6"/></p>

</div>
<div id='tab-node-0-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-7-1.png" alt="plot of chunk tab-node-0-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-0-signature_compare](figure_cola/node-0-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-0-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-0-dimension-reduction'>
<ul>
<li><a href='#tab-node-0-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-0-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-0-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-0-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-0-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-0-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-0-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-1-1.png" alt="plot of chunk tab-node-0-dimension-reduction-1"/></p>

</div>
<div id='tab-node-0-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-2-1.png" alt="plot of chunk tab-node-0-dimension-reduction-2"/></p>

</div>
<div id='tab-node-0-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-3-1.png" alt="plot of chunk tab-node-0-dimension-reduction-3"/></p>

</div>
<div id='tab-node-0-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-4-1.png" alt="plot of chunk tab-node-0-dimension-reduction-4"/></p>

</div>
<div id='tab-node-0-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-5-1.png" alt="plot of chunk tab-node-0-dimension-reduction-5"/></p>

</div>
<div id='tab-node-0-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-6-1.png" alt="plot of chunk tab-node-0-dimension-reduction-6"/></p>

</div>
<div id='tab-node-0-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-7-1.png" alt="plot of chunk tab-node-0-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-0-collect-classes](figure_cola/node-0-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node01


Parent node: [Node0](#Node0).
Child nodes: 
                Node011-leaf
        ,
                [Node012](#Node012)
        ,
                Node021-leaf
        ,
                Node022-leaf
        ,
                Node023-leaf
        ,
                Node024-leaf
        ,
                Node031-leaf
        ,
                Node032-leaf
        ,
                Node033-leaf
        ,
                Node034-leaf
        ,
                Node041-leaf
        ,
                Node042-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["01"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 69 columns.
#>   Top rows (1000) are extracted by 'SD' method.
#>   Subgroups are detected by 'kmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 2.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-01-collect-plots](figure_cola/node-01-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-01-select-partition-number](figure_cola/node-01-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.5069 0.494   0.494
#> 3 3 0.704           0.682       0.861         0.1881 0.962   0.922
#> 4 4 0.607           0.597       0.791         0.1175 0.897   0.775
#> 5 5 0.542           0.663       0.759         0.0761 0.931   0.814
#> 6 6 0.589           0.546       0.664         0.0632 0.898   0.703
#> 7 7 0.602           0.458       0.682         0.0557 0.835   0.481
#> 8 8 0.619           0.406       0.656         0.0221 0.894   0.550
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 2
```


Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-01-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-01-get-classes'>
<ul>
<li><a href='#tab-node-01-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-01-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-01-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-01-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-01-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-01-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-01-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-01-get-classes-1'>
<p><a id='tab-node-01-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.ZB.A96G.01     1       0          1  1  0
#&gt; TCGA.XM.A8R8.01     2       0          1  0  1
#&gt; TCGA.XU.AAXX.01     2       0          1  0  1
#&gt; TCGA.ZT.A8OM.01     2       0          1  0  1
#&gt; TCGA.3S.AAYX.01     2       0          1  0  1
#&gt; TCGA.5U.AB0F.01     2       0          1  0  1
#&gt; TCGA.X7.A8DJ.01     1       0          1  1  0
#&gt; TCGA.ZB.A96D.01     2       0          1  0  1
#&gt; TCGA.X7.A8DG.01     1       0          1  1  0
#&gt; TCGA.4V.A9QI.01     1       0          1  1  0
#&gt; TCGA.4V.A9QX.01     2       0          1  0  1
#&gt; TCGA.4X.A9FB.01     1       0          1  1  0
#&gt; TCGA.YT.A95E.01     1       0          1  1  0
#&gt; TCGA.X7.A8D7.01     2       0          1  0  1
#&gt; TCGA.4V.A9QQ.01     2       0          1  0  1
#&gt; TCGA.X7.A8M4.01     1       0          1  1  0
#&gt; TCGA.4V.A9QJ.01     1       0          1  1  0
#&gt; TCGA.X7.A8D6.01     2       0          1  0  1
#&gt; TCGA.ZC.AAAF.01     2       0          1  0  1
#&gt; TCGA.4X.A9FC.01     2       0          1  0  1
#&gt; TCGA.3T.AA9L.01     2       0          1  0  1
#&gt; TCGA.XU.A92W.01     1       0          1  1  0
#&gt; TCGA.X7.A8DI.01     2       0          1  0  1
#&gt; TCGA.XU.AAXY.01     1       0          1  1  0
#&gt; TCGA.4V.A9QU.01     2       0          1  0  1
#&gt; TCGA.X7.A8DF.01     1       0          1  1  0
#&gt; TCGA.XU.A932.01     1       0          1  1  0
#&gt; TCGA.3G.AB0O.01     1       0          1  1  0
#&gt; TCGA.X7.A8M7.01     1       0          1  1  0
#&gt; TCGA.XM.A8R9.01     2       0          1  0  1
#&gt; TCGA.XM.AAZ1.01     1       0          1  1  0
#&gt; TCGA.X7.A8DE.01     2       0          1  0  1
#&gt; TCGA.X7.A8D7.11     2       0          1  0  1
#&gt; TCGA.X7.A8M8.01     1       0          1  1  0
#&gt; TCGA.X7.A8D6.11     2       0          1  0  1
#&gt; TCGA.4V.A9QT.01     2       0          1  0  1
#&gt; TCGA.XM.A8RL.01     1       0          1  1  0
#&gt; TCGA.XM.A8RE.01     2       0          1  0  1
#&gt; TCGA.XM.A8RH.01     2       0          1  0  1
#&gt; TCGA.ZC.AAAH.01     1       0          1  1  0
#&gt; TCGA.XH.A853.01     1       0          1  1  0
#&gt; TCGA.X7.A8DD.01     2       0          1  0  1
#&gt; TCGA.ZB.A96A.01     1       0          1  1  0
#&gt; TCGA.XU.AAY0.01     2       0          1  0  1
#&gt; TCGA.XM.A8RB.01     2       0          1  0  1
#&gt; TCGA.ZB.A96R.01     1       0          1  1  0
#&gt; TCGA.XM.A8RD.01     2       0          1  0  1
#&gt; TCGA.X7.A8DC.01     1       0          1  1  0
#&gt; TCGA.YT.A95H.01     1       0          1  1  0
#&gt; TCGA.ZC.AAAA.01     1       0          1  1  0
#&gt; TCGA.XU.A92R.01     2       0          1  0  1
#&gt; TCGA.YT.A95G.01     2       0          1  0  1
#&gt; TCGA.XU.A92U.01     1       0          1  1  0
#&gt; TCGA.3Q.A9WF.01     1       0          1  1  0
#&gt; TCGA.XU.AAXV.01     2       0          1  0  1
#&gt; TCGA.XU.AAXW.01     2       0          1  0  1
#&gt; TCGA.4V.A9QW.01     1       0          1  1  0
#&gt; TCGA.XU.AAXZ.01     1       0          1  1  0
#&gt; TCGA.X7.A8DB.01     2       0          1  0  1
#&gt; TCGA.ZB.A96O.01     2       0          1  0  1
#&gt; TCGA.XU.AAY1.01     2       0          1  0  1
#&gt; TCGA.4V.A9QS.01     2       0          1  0  1
#&gt; TCGA.X7.A8M6.01     1       0          1  1  0
#&gt; TCGA.3G.AB0T.01     1       0          1  1  0
#&gt; TCGA.4X.A9F9.01     2       0          1  0  1
#&gt; TCGA.XU.A92Y.01     2       0          1  0  1
#&gt; TCGA.ZB.A96B.01     1       0          1  1  0
#&gt; TCGA.ZB.A96P.01     1       0          1  1  0
#&gt; TCGA.ZB.A963.01     1       0          1  1  0
</code></pre>

<script>
$('#tab-node-01-get-classes-1-a').parent().next().next().hide();
$('#tab-node-01-get-classes-1-a').click(function(){
  $('#tab-node-01-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-2'>
<p><a id='tab-node-01-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.ZB.A96G.01     1  0.2959     0.6610 0.90 0.00 0.10
#&gt; TCGA.XM.A8R8.01     2  0.5835     0.7490 0.00 0.66 0.34
#&gt; TCGA.XU.AAXX.01     2  0.3686     0.8804 0.00 0.86 0.14
#&gt; TCGA.ZT.A8OM.01     2  0.2066     0.9051 0.00 0.94 0.06
#&gt; TCGA.3S.AAYX.01     2  0.5948     0.7332 0.00 0.64 0.36
#&gt; TCGA.5U.AB0F.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.X7.A8DJ.01     1  0.4555     0.5279 0.80 0.00 0.20
#&gt; TCGA.ZB.A96D.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.X7.A8DG.01     1  0.2066     0.6849 0.94 0.00 0.06
#&gt; TCGA.4V.A9QI.01     1  0.5560    -0.1529 0.70 0.00 0.30
#&gt; TCGA.4V.A9QX.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.4X.A9FB.01     1  0.0000     0.6952 1.00 0.00 0.00
#&gt; TCGA.YT.A95E.01     1  0.6126    -0.5512 0.60 0.00 0.40
#&gt; TCGA.X7.A8D7.01     2  0.5706     0.7739 0.00 0.68 0.32
#&gt; TCGA.4V.A9QQ.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.0892     0.6910 0.98 0.00 0.02
#&gt; TCGA.4V.A9QJ.01     1  0.4291     0.6066 0.82 0.00 0.18
#&gt; TCGA.X7.A8D6.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.ZC.AAAF.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.4X.A9FC.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.3T.AA9L.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.XU.A92W.01     1  0.2537     0.6845 0.92 0.00 0.08
#&gt; TCGA.X7.A8DI.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.XU.AAXY.01     1  0.3686     0.6203 0.86 0.00 0.14
#&gt; TCGA.4V.A9QU.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.X7.A8DF.01     1  0.2537     0.6837 0.92 0.00 0.08
#&gt; TCGA.XU.A932.01     1  0.4291     0.5490 0.82 0.00 0.18
#&gt; TCGA.3G.AB0O.01     1  0.5560    -0.0934 0.70 0.00 0.30
#&gt; TCGA.X7.A8M7.01     1  0.6045    -0.2944 0.62 0.00 0.38
#&gt; TCGA.XM.A8R9.01     2  0.0892     0.9108 0.00 0.98 0.02
#&gt; TCGA.XM.AAZ1.01     1  0.1529     0.6907 0.96 0.00 0.04
#&gt; TCGA.X7.A8DE.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.X7.A8D7.11     2  0.5706     0.7739 0.00 0.68 0.32
#&gt; TCGA.X7.A8M8.01     3  0.6244     0.8451 0.44 0.00 0.56
#&gt; TCGA.X7.A8D6.11     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.4V.A9QT.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.XM.A8RL.01     1  0.2959     0.6466 0.90 0.00 0.10
#&gt; TCGA.XM.A8RE.01     2  0.2066     0.9051 0.00 0.94 0.06
#&gt; TCGA.XM.A8RH.01     2  0.2066     0.9051 0.00 0.94 0.06
#&gt; TCGA.ZC.AAAH.01     1  0.0000     0.6952 1.00 0.00 0.00
#&gt; TCGA.XH.A853.01     3  0.6302     0.8975 0.48 0.00 0.52
#&gt; TCGA.X7.A8DD.01     2  0.2066     0.9051 0.00 0.94 0.06
#&gt; TCGA.ZB.A96A.01     1  0.2537     0.6837 0.92 0.00 0.08
#&gt; TCGA.XU.AAY0.01     2  0.6045     0.7374 0.00 0.62 0.38
#&gt; TCGA.XM.A8RB.01     2  0.5397     0.7983 0.00 0.72 0.28
#&gt; TCGA.ZB.A96R.01     1  0.0892     0.6910 0.98 0.00 0.02
#&gt; TCGA.XM.A8RD.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.X7.A8DC.01     1  0.3686     0.6054 0.86 0.00 0.14
#&gt; TCGA.YT.A95H.01     1  0.2066     0.6825 0.94 0.00 0.06
#&gt; TCGA.ZC.AAAA.01     1  0.2066     0.6960 0.94 0.00 0.06
#&gt; TCGA.XU.A92R.01     2  0.5706     0.7538 0.00 0.68 0.32
#&gt; TCGA.YT.A95G.01     2  0.0892     0.9108 0.00 0.98 0.02
#&gt; TCGA.XU.A92U.01     1  0.4002     0.6445 0.84 0.00 0.16
#&gt; TCGA.3Q.A9WF.01     3  0.6309     0.8689 0.50 0.00 0.50
#&gt; TCGA.XU.AAXV.01     2  0.2959     0.8951 0.00 0.90 0.10
#&gt; TCGA.XU.AAXW.01     2  0.5835     0.7490 0.00 0.66 0.34
#&gt; TCGA.4V.A9QW.01     1  0.3686     0.6054 0.86 0.00 0.14
#&gt; TCGA.XU.AAXZ.01     1  0.3686     0.6397 0.86 0.00 0.14
#&gt; TCGA.X7.A8DB.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.ZB.A96O.01     2  0.2066     0.9051 0.00 0.94 0.06
#&gt; TCGA.XU.AAY1.01     2  0.5706     0.7538 0.00 0.68 0.32
#&gt; TCGA.4V.A9QS.01     2  0.2066     0.9051 0.00 0.94 0.06
#&gt; TCGA.X7.A8M6.01     1  0.1529     0.6864 0.96 0.00 0.04
#&gt; TCGA.3G.AB0T.01     1  0.6045    -0.5804 0.62 0.00 0.38
#&gt; TCGA.4X.A9F9.01     2  0.0000     0.9152 0.00 1.00 0.00
#&gt; TCGA.XU.A92Y.01     2  0.2066     0.9051 0.00 0.94 0.06
#&gt; TCGA.ZB.A96B.01     1  0.6302    -0.8733 0.52 0.00 0.48
#&gt; TCGA.ZB.A96P.01     1  0.2066     0.6685 0.94 0.00 0.06
#&gt; TCGA.ZB.A963.01     1  0.4555     0.5249 0.80 0.00 0.20
</code></pre>

<script>
$('#tab-node-01-get-classes-2-a').parent().next().next().hide();
$('#tab-node-01-get-classes-2-a').click(function(){
  $('#tab-node-01-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-3'>
<p><a id='tab-node-01-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.ZB.A96G.01     1  0.4227      0.598 0.82 0.00 0.12 0.06
#&gt; TCGA.XM.A8R8.01     4  0.4713      0.984 0.00 0.36 0.00 0.64
#&gt; TCGA.XU.AAXX.01     2  0.4292      0.700 0.00 0.82 0.08 0.10
#&gt; TCGA.ZT.A8OM.01     2  0.3198      0.801 0.00 0.88 0.08 0.04
#&gt; TCGA.3S.AAYX.01     4  0.4624      0.958 0.00 0.34 0.00 0.66
#&gt; TCGA.5U.AB0F.01     2  0.0707      0.825 0.00 0.98 0.00 0.02
#&gt; TCGA.X7.A8DJ.01     1  0.7004      0.354 0.58 0.00 0.20 0.22
#&gt; TCGA.ZB.A96D.01     2  0.1211      0.816 0.00 0.96 0.00 0.04
#&gt; TCGA.X7.A8DG.01     1  0.1913      0.612 0.94 0.00 0.04 0.02
#&gt; TCGA.4V.A9QI.01     1  0.6510     -0.129 0.54 0.00 0.38 0.08
#&gt; TCGA.4V.A9QX.01     2  0.0000      0.828 0.00 1.00 0.00 0.00
#&gt; TCGA.4X.A9FB.01     1  0.1637      0.621 0.94 0.00 0.00 0.06
#&gt; TCGA.YT.A95E.01     1  0.5594     -0.365 0.52 0.00 0.46 0.02
#&gt; TCGA.X7.A8D7.01     2  0.7602     -0.490 0.00 0.42 0.20 0.38
#&gt; TCGA.4V.A9QQ.01     2  0.0000      0.828 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8M4.01     1  0.4553      0.553 0.78 0.00 0.04 0.18
#&gt; TCGA.4V.A9QJ.01     1  0.6286      0.443 0.66 0.00 0.20 0.14
#&gt; TCGA.X7.A8D6.01     2  0.2830      0.810 0.00 0.90 0.06 0.04
#&gt; TCGA.ZC.AAAF.01     2  0.2011      0.789 0.00 0.92 0.00 0.08
#&gt; TCGA.4X.A9FC.01     2  0.0000      0.828 0.00 1.00 0.00 0.00
#&gt; TCGA.3T.AA9L.01     2  0.1637      0.801 0.00 0.94 0.00 0.06
#&gt; TCGA.XU.A92W.01     1  0.4227      0.593 0.82 0.00 0.12 0.06
#&gt; TCGA.X7.A8DI.01     2  0.1211      0.816 0.00 0.96 0.00 0.04
#&gt; TCGA.XU.AAXY.01     1  0.2647      0.584 0.88 0.00 0.12 0.00
#&gt; TCGA.4V.A9QU.01     2  0.1211      0.821 0.00 0.96 0.00 0.04
#&gt; TCGA.X7.A8DF.01     1  0.5784      0.522 0.70 0.00 0.10 0.20
#&gt; TCGA.XU.A932.01     1  0.2345      0.583 0.90 0.00 0.10 0.00
#&gt; TCGA.3G.AB0O.01     1  0.5636      0.315 0.68 0.00 0.26 0.06
#&gt; TCGA.X7.A8M7.01     3  0.7372      0.157 0.42 0.00 0.42 0.16
#&gt; TCGA.XM.A8R9.01     2  0.2011      0.789 0.00 0.92 0.00 0.08
#&gt; TCGA.XM.AAZ1.01     1  0.1913      0.613 0.94 0.00 0.02 0.04
#&gt; TCGA.X7.A8DE.01     2  0.1637      0.801 0.00 0.94 0.00 0.06
#&gt; TCGA.X7.A8D7.11     2  0.7602     -0.490 0.00 0.42 0.20 0.38
#&gt; TCGA.X7.A8M8.01     3  0.4797      0.772 0.26 0.00 0.72 0.02
#&gt; TCGA.X7.A8D6.11     2  0.2830      0.810 0.00 0.90 0.06 0.04
#&gt; TCGA.4V.A9QT.01     2  0.2411      0.820 0.00 0.92 0.04 0.04
#&gt; TCGA.XM.A8RL.01     1  0.3335      0.565 0.86 0.00 0.12 0.02
#&gt; TCGA.XM.A8RE.01     2  0.1913      0.819 0.00 0.94 0.04 0.02
#&gt; TCGA.XM.A8RH.01     2  0.2706      0.802 0.00 0.90 0.08 0.02
#&gt; TCGA.ZC.AAAH.01     1  0.2011      0.614 0.92 0.00 0.00 0.08
#&gt; TCGA.XH.A853.01     3  0.4134      0.784 0.26 0.00 0.74 0.00
#&gt; TCGA.X7.A8DD.01     2  0.1913      0.819 0.00 0.94 0.04 0.02
#&gt; TCGA.ZB.A96A.01     1  0.6110      0.484 0.66 0.00 0.10 0.24
#&gt; TCGA.XU.AAY0.01     4  0.4624      0.957 0.00 0.34 0.00 0.66
#&gt; TCGA.XM.A8RB.01     2  0.6299     -0.414 0.00 0.52 0.06 0.42
#&gt; TCGA.ZB.A96R.01     1  0.4088      0.590 0.82 0.00 0.04 0.14
#&gt; TCGA.XM.A8RD.01     2  0.2011      0.789 0.00 0.92 0.00 0.08
#&gt; TCGA.X7.A8DC.01     1  0.7674      0.143 0.46 0.00 0.28 0.26
#&gt; TCGA.YT.A95H.01     1  0.6110      0.469 0.66 0.00 0.10 0.24
#&gt; TCGA.ZC.AAAA.01     1  0.3037      0.600 0.88 0.00 0.10 0.02
#&gt; TCGA.XU.A92R.01     4  0.4713      0.984 0.00 0.36 0.00 0.64
#&gt; TCGA.YT.A95G.01     2  0.0000      0.828 0.00 1.00 0.00 0.00
#&gt; TCGA.XU.A92U.01     1  0.6122      0.498 0.68 0.00 0.16 0.16
#&gt; TCGA.3Q.A9WF.01     3  0.4277      0.776 0.28 0.00 0.72 0.00
#&gt; TCGA.XU.AAXV.01     2  0.4491      0.733 0.00 0.80 0.06 0.14
#&gt; TCGA.XU.AAXW.01     4  0.4713      0.984 0.00 0.36 0.00 0.64
#&gt; TCGA.4V.A9QW.01     1  0.7583      0.134 0.48 0.00 0.28 0.24
#&gt; TCGA.XU.AAXZ.01     1  0.4079      0.556 0.80 0.00 0.18 0.02
#&gt; TCGA.X7.A8DB.01     2  0.1913      0.828 0.00 0.94 0.04 0.02
#&gt; TCGA.ZB.A96O.01     2  0.1913      0.819 0.00 0.94 0.04 0.02
#&gt; TCGA.XU.AAY1.01     4  0.4713      0.984 0.00 0.36 0.00 0.64
#&gt; TCGA.4V.A9QS.01     2  0.2706      0.802 0.00 0.90 0.08 0.02
#&gt; TCGA.X7.A8M6.01     1  0.3037      0.591 0.88 0.00 0.10 0.02
#&gt; TCGA.3G.AB0T.01     1  0.5594     -0.398 0.52 0.00 0.46 0.02
#&gt; TCGA.4X.A9F9.01     2  0.1913      0.815 0.00 0.94 0.04 0.02
#&gt; TCGA.XU.A92Y.01     2  0.2411      0.820 0.00 0.92 0.04 0.04
#&gt; TCGA.ZB.A96B.01     3  0.5355      0.693 0.36 0.00 0.62 0.02
#&gt; TCGA.ZB.A96P.01     1  0.2830      0.609 0.90 0.00 0.06 0.04
#&gt; TCGA.ZB.A963.01     1  0.4642      0.465 0.74 0.00 0.24 0.02
</code></pre>

<script>
$('#tab-node-01-get-classes-3-a').parent().next().next().hide();
$('#tab-node-01-get-classes-3-a').click(function(){
  $('#tab-node-01-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-4'>
<p><a id='tab-node-01-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.ZB.A96G.01     5  0.3697     0.6545 0.00 0.00 0.10 0.08 0.82
#&gt; TCGA.XM.A8R8.01     4  0.2732     0.8161 0.00 0.16 0.00 0.84 0.00
#&gt; TCGA.XU.AAXX.01     2  0.5425     0.6837 0.32 0.60 0.00 0.08 0.00
#&gt; TCGA.ZT.A8OM.01     2  0.4132     0.7726 0.26 0.72 0.00 0.02 0.00
#&gt; TCGA.3S.AAYX.01     4  0.2732     0.8161 0.00 0.16 0.00 0.84 0.00
#&gt; TCGA.5U.AB0F.01     2  0.2280     0.7993 0.12 0.88 0.00 0.00 0.00
#&gt; TCGA.X7.A8DJ.01     5  0.6604     0.4200 0.12 0.00 0.22 0.06 0.60
#&gt; TCGA.ZB.A96D.01     2  0.0609     0.8189 0.02 0.98 0.00 0.00 0.00
#&gt; TCGA.X7.A8DG.01     5  0.1043     0.6756 0.00 0.00 0.04 0.00 0.96
#&gt; TCGA.4V.A9QI.01     5  0.6983    -0.2067 0.10 0.00 0.38 0.06 0.46
#&gt; TCGA.4V.A9QX.01     2  0.2280     0.8154 0.12 0.88 0.00 0.00 0.00
#&gt; TCGA.4X.A9FB.01     5  0.1648     0.6772 0.00 0.00 0.02 0.04 0.94
#&gt; TCGA.YT.A95E.01     3  0.5220     0.5338 0.02 0.00 0.58 0.02 0.38
#&gt; TCGA.X7.A8D7.01     4  0.8468     0.5422 0.28 0.22 0.18 0.32 0.00
#&gt; TCGA.4V.A9QQ.01     2  0.0609     0.8202 0.02 0.98 0.00 0.00 0.00
#&gt; TCGA.X7.A8M4.01     5  0.4096     0.6128 0.20 0.00 0.00 0.04 0.76
#&gt; TCGA.4V.A9QJ.01     5  0.5727     0.4043 0.34 0.00 0.10 0.00 0.56
#&gt; TCGA.X7.A8D6.01     2  0.3424     0.7975 0.24 0.76 0.00 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     2  0.2012     0.8013 0.06 0.92 0.00 0.02 0.00
#&gt; TCGA.4X.A9FC.01     2  0.0000     0.8220 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.3T.AA9L.01     2  0.2873     0.8007 0.12 0.86 0.00 0.02 0.00
#&gt; TCGA.XU.A92W.01     5  0.3390     0.6572 0.00 0.00 0.10 0.06 0.84
#&gt; TCGA.X7.A8DI.01     2  0.1410     0.8113 0.06 0.94 0.00 0.00 0.00
#&gt; TCGA.XU.AAXY.01     5  0.4225     0.6261 0.02 0.00 0.12 0.06 0.80
#&gt; TCGA.4V.A9QU.01     2  0.1043     0.8143 0.04 0.96 0.00 0.00 0.00
#&gt; TCGA.X7.A8DF.01     5  0.5205     0.5407 0.28 0.00 0.04 0.02 0.66
#&gt; TCGA.XU.A932.01     5  0.4855     0.5887 0.04 0.00 0.14 0.06 0.76
#&gt; TCGA.3G.AB0O.01     5  0.6124     0.0749 0.10 0.00 0.30 0.02 0.58
#&gt; TCGA.X7.A8M7.01     3  0.6671     0.4236 0.24 0.00 0.42 0.00 0.34
#&gt; TCGA.XM.A8R9.01     2  0.3291     0.8077 0.12 0.84 0.00 0.04 0.00
#&gt; TCGA.XM.AAZ1.01     5  0.0609     0.6765 0.00 0.00 0.02 0.00 0.98
#&gt; TCGA.X7.A8DE.01     2  0.1043     0.8161 0.04 0.96 0.00 0.00 0.00
#&gt; TCGA.X7.A8D7.11     4  0.8468     0.5422 0.28 0.22 0.18 0.32 0.00
#&gt; TCGA.X7.A8M8.01     3  0.3922     0.7470 0.00 0.00 0.78 0.04 0.18
#&gt; TCGA.X7.A8D6.11     2  0.3424     0.7975 0.24 0.76 0.00 0.00 0.00
#&gt; TCGA.4V.A9QT.01     2  0.2732     0.7978 0.16 0.84 0.00 0.00 0.00
#&gt; TCGA.XM.A8RL.01     5  0.2610     0.6573 0.02 0.00 0.06 0.02 0.90
#&gt; TCGA.XM.A8RE.01     2  0.3690     0.7784 0.20 0.78 0.00 0.02 0.00
#&gt; TCGA.XM.A8RH.01     2  0.3999     0.7824 0.24 0.74 0.00 0.02 0.00
#&gt; TCGA.ZC.AAAH.01     5  0.0609     0.6791 0.00 0.00 0.00 0.02 0.98
#&gt; TCGA.XH.A853.01     3  0.3922     0.7470 0.00 0.00 0.78 0.04 0.18
#&gt; TCGA.X7.A8DD.01     2  0.3999     0.7677 0.24 0.74 0.00 0.02 0.00
#&gt; TCGA.ZB.A96A.01     5  0.5548     0.5883 0.22 0.00 0.06 0.04 0.68
#&gt; TCGA.XU.AAY0.01     4  0.3106     0.8050 0.02 0.14 0.00 0.84 0.00
#&gt; TCGA.XM.A8RB.01     4  0.7439     0.2973 0.22 0.36 0.04 0.38 0.00
#&gt; TCGA.ZB.A96R.01     5  0.2077     0.6728 0.04 0.00 0.00 0.04 0.92
#&gt; TCGA.XM.A8RD.01     2  0.1648     0.8073 0.04 0.94 0.00 0.02 0.00
#&gt; TCGA.X7.A8DC.01     5  0.5447     0.3124 0.44 0.00 0.06 0.00 0.50
#&gt; TCGA.YT.A95H.01     5  0.4644     0.5519 0.28 0.00 0.00 0.04 0.68
#&gt; TCGA.ZC.AAAA.01     5  0.3700     0.6592 0.06 0.00 0.08 0.02 0.84
#&gt; TCGA.XU.A92R.01     4  0.2929     0.8107 0.00 0.18 0.00 0.82 0.00
#&gt; TCGA.YT.A95G.01     2  0.2929     0.8196 0.18 0.82 0.00 0.00 0.00
#&gt; TCGA.XU.A92U.01     5  0.4644     0.5477 0.28 0.00 0.04 0.00 0.68
#&gt; TCGA.3Q.A9WF.01     3  0.3922     0.7470 0.00 0.00 0.78 0.04 0.18
#&gt; TCGA.XU.AAXV.01     2  0.5555     0.6287 0.22 0.64 0.00 0.14 0.00
#&gt; TCGA.XU.AAXW.01     4  0.2732     0.8161 0.00 0.16 0.00 0.84 0.00
#&gt; TCGA.4V.A9QW.01     5  0.5447     0.3124 0.44 0.00 0.06 0.00 0.50
#&gt; TCGA.XU.AAXZ.01     5  0.2516     0.6454 0.00 0.00 0.14 0.00 0.86
#&gt; TCGA.X7.A8DB.01     2  0.2929     0.8077 0.18 0.82 0.00 0.00 0.00
#&gt; TCGA.ZB.A96O.01     2  0.4252     0.7529 0.28 0.70 0.00 0.02 0.00
#&gt; TCGA.XU.AAY1.01     4  0.2929     0.8107 0.00 0.18 0.00 0.82 0.00
#&gt; TCGA.4V.A9QS.01     2  0.4456     0.7296 0.32 0.66 0.00 0.02 0.00
#&gt; TCGA.X7.A8M6.01     5  0.4106     0.5968 0.04 0.00 0.14 0.02 0.80
#&gt; TCGA.3G.AB0T.01     3  0.6355     0.5048 0.10 0.00 0.50 0.02 0.38
#&gt; TCGA.4X.A9F9.01     2  0.2020     0.8183 0.10 0.90 0.00 0.00 0.00
#&gt; TCGA.XU.A92Y.01     2  0.4254     0.7598 0.22 0.74 0.00 0.04 0.00
#&gt; TCGA.ZB.A96B.01     3  0.5293     0.7151 0.06 0.00 0.68 0.02 0.24
#&gt; TCGA.ZB.A96P.01     5  0.3455     0.6503 0.06 0.00 0.04 0.04 0.86
#&gt; TCGA.ZB.A963.01     5  0.3274     0.5649 0.00 0.00 0.22 0.00 0.78
</code></pre>

<script>
$('#tab-node-01-get-classes-4-a').parent().next().next().hide();
$('#tab-node-01-get-classes-4-a').click(function(){
  $('#tab-node-01-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-5'>
<p><a id='tab-node-01-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.ZB.A96G.01     5  0.4088     0.5298 0.10 0.00 0.02 0.00 0.78 0.10
#&gt; TCGA.XM.A8R8.01     4  0.1480     0.9525 0.02 0.04 0.00 0.94 0.00 0.00
#&gt; TCGA.XU.AAXX.01     2  0.4879     0.3727 0.04 0.72 0.00 0.12 0.00 0.12
#&gt; TCGA.ZT.A8OM.01     2  0.3111     0.5030 0.02 0.84 0.00 0.02 0.00 0.12
#&gt; TCGA.3S.AAYX.01     4  0.2474     0.9059 0.08 0.04 0.00 0.88 0.00 0.00
#&gt; TCGA.5U.AB0F.01     2  0.4199     0.6499 0.00 0.60 0.38 0.02 0.00 0.00
#&gt; TCGA.X7.A8DJ.01     5  0.5366    -0.2341 0.46 0.00 0.02 0.00 0.46 0.06
#&gt; TCGA.ZB.A96D.01     2  0.4246     0.6527 0.00 0.58 0.40 0.02 0.00 0.00
#&gt; TCGA.X7.A8DG.01     5  0.3544     0.5065 0.12 0.00 0.00 0.00 0.80 0.08
#&gt; TCGA.4V.A9QI.01     5  0.6764    -0.1805 0.30 0.00 0.22 0.02 0.44 0.02
#&gt; TCGA.4V.A9QX.01     2  0.3819     0.6702 0.00 0.70 0.28 0.00 0.00 0.02
#&gt; TCGA.4X.A9FB.01     5  0.3985     0.4510 0.14 0.00 0.00 0.00 0.76 0.10
#&gt; TCGA.YT.A95E.01     5  0.5742     0.2316 0.04 0.00 0.16 0.02 0.66 0.12
#&gt; TCGA.X7.A8D7.01     6  0.5354     1.0000 0.00 0.16 0.00 0.26 0.00 0.58
#&gt; TCGA.4V.A9QQ.01     2  0.4310     0.6469 0.00 0.54 0.44 0.02 0.00 0.00
#&gt; TCGA.X7.A8M4.01     5  0.5364     0.0178 0.30 0.00 0.00 0.00 0.56 0.14
#&gt; TCGA.4V.A9QJ.01     1  0.5672     0.4400 0.52 0.00 0.02 0.00 0.36 0.10
#&gt; TCGA.X7.A8D6.01     2  0.5313     0.5897 0.02 0.70 0.16 0.04 0.00 0.08
#&gt; TCGA.ZC.AAAF.01     2  0.5020     0.6404 0.02 0.56 0.38 0.04 0.00 0.00
#&gt; TCGA.4X.A9FC.01     2  0.4199     0.6621 0.00 0.60 0.38 0.02 0.00 0.00
#&gt; TCGA.3T.AA9L.01     2  0.5304     0.6487 0.06 0.62 0.28 0.04 0.00 0.00
#&gt; TCGA.XU.A92W.01     5  0.3997     0.5177 0.14 0.00 0.02 0.00 0.78 0.06
#&gt; TCGA.X7.A8DI.01     2  0.4310     0.6469 0.00 0.54 0.44 0.02 0.00 0.00
#&gt; TCGA.XU.AAXY.01     5  0.2345     0.5722 0.02 0.00 0.02 0.00 0.90 0.06
#&gt; TCGA.4V.A9QU.01     2  0.4764     0.6479 0.00 0.54 0.42 0.02 0.00 0.02
#&gt; TCGA.X7.A8DF.01     1  0.4482     0.5169 0.60 0.00 0.00 0.00 0.36 0.04
#&gt; TCGA.XU.A932.01     5  0.3103     0.5562 0.04 0.00 0.04 0.00 0.86 0.06
#&gt; TCGA.3G.AB0O.01     5  0.5313     0.3810 0.16 0.00 0.08 0.02 0.70 0.04
#&gt; TCGA.X7.A8M7.01     1  0.5626     0.0305 0.54 0.00 0.10 0.02 0.34 0.00
#&gt; TCGA.XM.A8R9.01     2  0.4502     0.6268 0.00 0.74 0.14 0.10 0.00 0.02
#&gt; TCGA.XM.AAZ1.01     5  0.3985     0.4382 0.10 0.00 0.00 0.00 0.76 0.14
#&gt; TCGA.X7.A8DE.01     2  0.5337     0.6610 0.02 0.60 0.32 0.02 0.00 0.04
#&gt; TCGA.X7.A8D7.11     6  0.5354     1.0000 0.00 0.16 0.00 0.26 0.00 0.58
#&gt; TCGA.X7.A8M8.01     3  0.6259     0.9008 0.10 0.00 0.54 0.00 0.28 0.08
#&gt; TCGA.X7.A8D6.11     2  0.5313     0.5897 0.02 0.70 0.16 0.04 0.00 0.08
#&gt; TCGA.4V.A9QT.01     2  0.5258     0.6586 0.06 0.66 0.24 0.02 0.00 0.02
#&gt; TCGA.XM.A8RL.01     5  0.3321     0.5422 0.10 0.00 0.00 0.00 0.82 0.08
#&gt; TCGA.XM.A8RE.01     2  0.4838     0.6027 0.02 0.70 0.18 0.00 0.00 0.10
#&gt; TCGA.XM.A8RH.01     2  0.3537     0.5562 0.04 0.84 0.02 0.02 0.00 0.08
#&gt; TCGA.ZC.AAAH.01     5  0.4328     0.3812 0.18 0.00 0.00 0.00 0.72 0.10
#&gt; TCGA.XH.A853.01     3  0.6259     0.9008 0.10 0.00 0.54 0.00 0.28 0.08
#&gt; TCGA.X7.A8DD.01     2  0.3846     0.5615 0.00 0.80 0.08 0.02 0.00 0.10
#&gt; TCGA.ZB.A96A.01     1  0.5071     0.4616 0.52 0.00 0.00 0.00 0.40 0.08
#&gt; TCGA.XU.AAY0.01     4  0.0937     0.9560 0.00 0.04 0.00 0.96 0.00 0.00
#&gt; TCGA.XM.A8RB.01     2  0.7396    -0.5104 0.04 0.36 0.04 0.34 0.00 0.22
#&gt; TCGA.ZB.A96R.01     5  0.4929     0.1344 0.28 0.00 0.00 0.00 0.62 0.10
#&gt; TCGA.XM.A8RD.01     2  0.5469     0.6393 0.08 0.68 0.18 0.04 0.00 0.02
#&gt; TCGA.X7.A8DC.01     1  0.3315     0.6076 0.78 0.00 0.02 0.00 0.20 0.00
#&gt; TCGA.YT.A95H.01     1  0.4576     0.5115 0.56 0.00 0.00 0.00 0.40 0.04
#&gt; TCGA.ZC.AAAA.01     5  0.2581     0.5446 0.12 0.00 0.00 0.00 0.86 0.02
#&gt; TCGA.XU.A92R.01     4  0.1480     0.9503 0.00 0.04 0.00 0.94 0.00 0.02
#&gt; TCGA.YT.A95G.01     2  0.3258     0.6528 0.02 0.84 0.10 0.04 0.00 0.00
#&gt; TCGA.XU.A92U.01     1  0.5265     0.4784 0.50 0.00 0.00 0.00 0.40 0.10
#&gt; TCGA.3Q.A9WF.01     3  0.6128     0.8860 0.08 0.00 0.54 0.00 0.30 0.08
#&gt; TCGA.XU.AAXV.01     2  0.5313     0.4768 0.08 0.70 0.04 0.16 0.00 0.02
#&gt; TCGA.XU.AAXW.01     4  0.1480     0.9528 0.02 0.04 0.00 0.94 0.00 0.00
#&gt; TCGA.4V.A9QW.01     1  0.3315     0.6076 0.78 0.00 0.02 0.00 0.20 0.00
#&gt; TCGA.XU.AAXZ.01     5  0.2512     0.5572 0.06 0.00 0.00 0.00 0.88 0.06
#&gt; TCGA.X7.A8DB.01     2  0.4690     0.6424 0.00 0.70 0.22 0.04 0.00 0.04
#&gt; TCGA.ZB.A96O.01     2  0.4392     0.4732 0.02 0.76 0.04 0.02 0.00 0.16
#&gt; TCGA.XU.AAY1.01     4  0.1480     0.9503 0.00 0.04 0.00 0.94 0.00 0.02
#&gt; TCGA.4V.A9QS.01     2  0.3318     0.4765 0.02 0.82 0.00 0.02 0.00 0.14
#&gt; TCGA.X7.A8M6.01     5  0.3660     0.5218 0.16 0.00 0.00 0.00 0.78 0.06
#&gt; TCGA.3G.AB0T.01     5  0.6559    -0.1800 0.26 0.00 0.20 0.02 0.50 0.02
#&gt; TCGA.4X.A9F9.01     2  0.5337     0.6543 0.02 0.60 0.32 0.02 0.00 0.04
#&gt; TCGA.XU.A92Y.01     2  0.4530     0.5290 0.02 0.78 0.06 0.08 0.00 0.06
#&gt; TCGA.ZB.A96B.01     3  0.6654     0.7201 0.12 0.00 0.42 0.02 0.40 0.04
#&gt; TCGA.ZB.A96P.01     5  0.4094     0.5021 0.18 0.00 0.00 0.00 0.74 0.08
#&gt; TCGA.ZB.A963.01     5  0.3073     0.5540 0.08 0.00 0.00 0.00 0.84 0.08
</code></pre>

<script>
$('#tab-node-01-get-classes-5-a').parent().next().next().hide();
$('#tab-node-01-get-classes-5-a').click(function(){
  $('#tab-node-01-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-6'>
<p><a id='tab-node-01-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.ZB.A96G.01     5   0.340     0.4626 0.00 0.02 0.04 0.00 0.80 0.14 0.00
#&gt; TCGA.XM.A8R8.01     4   0.143     0.7669 0.00 0.08 0.00 0.92 0.00 0.00 0.00
#&gt; TCGA.XU.AAXX.01     7   0.166     0.6454 0.02 0.00 0.00 0.06 0.00 0.00 0.92
#&gt; TCGA.ZT.A8OM.01     7   0.315     0.6618 0.04 0.06 0.06 0.00 0.00 0.00 0.84
#&gt; TCGA.3S.AAYX.01     4   0.251     0.7329 0.04 0.06 0.00 0.88 0.00 0.00 0.02
#&gt; TCGA.5U.AB0F.01     2   0.319     0.7090 0.02 0.76 0.00 0.00 0.00 0.00 0.22
#&gt; TCGA.X7.A8DJ.01     1   0.721     0.1692 0.38 0.04 0.10 0.02 0.36 0.10 0.00
#&gt; TCGA.ZB.A96D.01     2   0.226     0.7219 0.00 0.84 0.00 0.00 0.00 0.00 0.16
#&gt; TCGA.X7.A8DG.01     5   0.101     0.4854 0.02 0.00 0.02 0.00 0.96 0.00 0.00
#&gt; TCGA.4V.A9QI.01     3   0.774     0.2373 0.22 0.08 0.34 0.02 0.28 0.06 0.00
#&gt; TCGA.4V.A9QX.01     2   0.407     0.5987 0.04 0.62 0.00 0.00 0.00 0.00 0.34
#&gt; TCGA.4X.A9FB.01     5   0.447     0.4215 0.06 0.02 0.00 0.02 0.72 0.18 0.00
#&gt; TCGA.YT.A95E.01     5   0.706    -0.0626 0.06 0.04 0.30 0.02 0.44 0.14 0.00
#&gt; TCGA.X7.A8D7.01     6   0.526     1.0000 0.00 0.00 0.00 0.26 0.00 0.52 0.22
#&gt; TCGA.4V.A9QQ.01     2   0.378     0.7147 0.02 0.72 0.02 0.00 0.00 0.00 0.24
#&gt; TCGA.X7.A8M4.01     5   0.508     0.2308 0.24 0.00 0.00 0.00 0.56 0.20 0.00
#&gt; TCGA.4V.A9QJ.01     5   0.468    -0.0653 0.42 0.00 0.00 0.02 0.52 0.04 0.00
#&gt; TCGA.X7.A8D6.01     7   0.595     0.2546 0.08 0.26 0.08 0.00 0.00 0.02 0.56
#&gt; TCGA.ZC.AAAF.01     2   0.435     0.7210 0.02 0.68 0.02 0.00 0.00 0.02 0.26
#&gt; TCGA.4X.A9FC.01     2   0.391     0.7164 0.00 0.70 0.06 0.00 0.00 0.00 0.24
#&gt; TCGA.3T.AA9L.01     2   0.453     0.7014 0.02 0.64 0.02 0.00 0.00 0.02 0.30
#&gt; TCGA.XU.A92W.01     5   0.505     0.4050 0.10 0.04 0.02 0.02 0.72 0.10 0.00
#&gt; TCGA.X7.A8DI.01     2   0.432     0.7062 0.00 0.70 0.04 0.00 0.00 0.04 0.22
#&gt; TCGA.XU.AAXY.01     5   0.489     0.4382 0.04 0.02 0.08 0.00 0.70 0.16 0.00
#&gt; TCGA.4V.A9QU.01     2   0.453     0.6829 0.04 0.72 0.02 0.00 0.00 0.04 0.18
#&gt; TCGA.X7.A8DF.01     5   0.394    -0.1290 0.42 0.00 0.02 0.00 0.56 0.00 0.00
#&gt; TCGA.XU.A932.01     5   0.566     0.3984 0.08 0.02 0.08 0.00 0.62 0.20 0.00
#&gt; TCGA.3G.AB0O.01     5   0.750    -0.3274 0.12 0.06 0.30 0.02 0.40 0.10 0.00
#&gt; TCGA.X7.A8M7.01     1   0.637    -0.2590 0.40 0.06 0.30 0.00 0.24 0.00 0.00
#&gt; TCGA.XM.A8R9.01     7   0.528     0.1614 0.04 0.34 0.04 0.00 0.00 0.02 0.56
#&gt; TCGA.XM.AAZ1.01     5   0.320     0.4632 0.06 0.00 0.00 0.00 0.80 0.14 0.00
#&gt; TCGA.X7.A8DE.01     2   0.508     0.6467 0.02 0.62 0.04 0.00 0.00 0.04 0.28
#&gt; TCGA.X7.A8D7.11     6   0.526     1.0000 0.00 0.00 0.00 0.26 0.00 0.52 0.22
#&gt; TCGA.X7.A8M8.01     3   0.189     0.6522 0.00 0.00 0.88 0.00 0.12 0.00 0.00
#&gt; TCGA.X7.A8D6.11     7   0.595     0.2546 0.08 0.26 0.08 0.00 0.00 0.02 0.56
#&gt; TCGA.4V.A9QT.01     2   0.587     0.5052 0.10 0.52 0.02 0.00 0.00 0.04 0.32
#&gt; TCGA.XM.A8RL.01     5   0.449     0.4450 0.06 0.02 0.04 0.00 0.74 0.14 0.00
#&gt; TCGA.XM.A8RE.01     7   0.453     0.5091 0.02 0.18 0.04 0.00 0.00 0.04 0.72
#&gt; TCGA.XM.A8RH.01     7   0.228     0.6567 0.04 0.08 0.00 0.00 0.00 0.00 0.88
#&gt; TCGA.ZC.AAAH.01     5   0.403     0.3938 0.12 0.00 0.00 0.00 0.72 0.16 0.00
#&gt; TCGA.XH.A853.01     3   0.189     0.6522 0.00 0.00 0.88 0.00 0.12 0.00 0.00
#&gt; TCGA.X7.A8DD.01     7   0.238     0.6566 0.02 0.12 0.00 0.00 0.00 0.00 0.86
#&gt; TCGA.ZB.A96A.01     5   0.497     0.0182 0.34 0.02 0.02 0.00 0.58 0.04 0.00
#&gt; TCGA.XU.AAY0.01     4   0.340     0.6569 0.06 0.04 0.00 0.82 0.00 0.00 0.08
#&gt; TCGA.XM.A8RB.01     4   0.749    -0.3282 0.10 0.16 0.00 0.34 0.00 0.08 0.32
#&gt; TCGA.ZB.A96R.01     5   0.574     0.1856 0.24 0.02 0.00 0.02 0.56 0.16 0.00
#&gt; TCGA.XM.A8RD.01     2   0.534     0.3212 0.06 0.50 0.00 0.02 0.00 0.02 0.40
#&gt; TCGA.X7.A8DC.01     1   0.391     0.5615 0.70 0.00 0.06 0.00 0.24 0.00 0.00
#&gt; TCGA.YT.A95H.01     5   0.500    -0.1005 0.40 0.00 0.00 0.00 0.48 0.12 0.00
#&gt; TCGA.ZC.AAAA.01     5   0.523     0.3748 0.18 0.00 0.06 0.00 0.64 0.12 0.00
#&gt; TCGA.XU.A92R.01     4   0.272     0.7360 0.04 0.12 0.00 0.84 0.00 0.00 0.00
#&gt; TCGA.YT.A95G.01     7   0.331     0.4543 0.02 0.24 0.00 0.00 0.00 0.00 0.74
#&gt; TCGA.XU.A92U.01     5   0.508     0.1993 0.28 0.02 0.00 0.04 0.62 0.04 0.00
#&gt; TCGA.3Q.A9WF.01     3   0.189     0.6522 0.00 0.00 0.88 0.00 0.12 0.00 0.00
#&gt; TCGA.XU.AAXV.01     7   0.520     0.5930 0.04 0.14 0.02 0.08 0.00 0.02 0.70
#&gt; TCGA.XU.AAXW.01     4   0.143     0.7669 0.00 0.08 0.00 0.92 0.00 0.00 0.00
#&gt; TCGA.4V.A9QW.01     1   0.391     0.5615 0.70 0.00 0.06 0.00 0.24 0.00 0.00
#&gt; TCGA.XU.AAXZ.01     5   0.291     0.4747 0.00 0.02 0.02 0.02 0.86 0.08 0.00
#&gt; TCGA.X7.A8DB.01     2   0.581     0.3555 0.06 0.50 0.02 0.00 0.00 0.06 0.36
#&gt; TCGA.ZB.A96O.01     7   0.291     0.6620 0.02 0.08 0.02 0.00 0.00 0.02 0.86
#&gt; TCGA.XU.AAY1.01     4   0.228     0.7605 0.04 0.08 0.00 0.88 0.00 0.00 0.00
#&gt; TCGA.4V.A9QS.01     7   0.101     0.6769 0.02 0.00 0.02 0.00 0.00 0.00 0.96
#&gt; TCGA.X7.A8M6.01     5   0.537     0.3716 0.20 0.02 0.04 0.00 0.64 0.10 0.00
#&gt; TCGA.3G.AB0T.01     3   0.718     0.2759 0.24 0.06 0.36 0.02 0.30 0.02 0.00
#&gt; TCGA.4X.A9F9.01     2   0.407     0.6137 0.04 0.62 0.00 0.00 0.00 0.00 0.34
#&gt; TCGA.XU.A92Y.01     7   0.374     0.6615 0.04 0.08 0.02 0.02 0.00 0.02 0.82
#&gt; TCGA.ZB.A96B.01     3   0.639     0.5605 0.10 0.04 0.58 0.02 0.20 0.06 0.00
#&gt; TCGA.ZB.A96P.01     5   0.608     0.3553 0.20 0.02 0.04 0.00 0.54 0.20 0.00
#&gt; TCGA.ZB.A963.01     5   0.424     0.4320 0.00 0.02 0.10 0.02 0.76 0.10 0.00
</code></pre>

<script>
$('#tab-node-01-get-classes-6-a').parent().next().next().hide();
$('#tab-node-01-get-classes-6-a').click(function(){
  $('#tab-node-01-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-7'>
<p><a id='tab-node-01-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7   p8
#&gt; TCGA.ZB.A96G.01     5   0.651     0.0713 0.14 0.04 0.00 0.00 0.48 0.14 0.00 0.20
#&gt; TCGA.XM.A8R8.01     4   0.156     0.9337 0.00 0.00 0.00 0.92 0.00 0.00 0.06 0.02
#&gt; TCGA.XU.AAXX.01     7   0.397     0.5423 0.00 0.10 0.10 0.02 0.00 0.02 0.76 0.00
#&gt; TCGA.ZT.A8OM.01     7   0.286     0.6025 0.00 0.00 0.08 0.00 0.00 0.00 0.82 0.10
#&gt; TCGA.3S.AAYX.01     4   0.286     0.8864 0.00 0.00 0.00 0.84 0.00 0.02 0.06 0.08
#&gt; TCGA.5U.AB0F.01     2   0.417     0.6885 0.00 0.70 0.02 0.02 0.00 0.00 0.22 0.04
#&gt; TCGA.X7.A8DJ.01     1   0.652     0.1193 0.44 0.08 0.00 0.00 0.30 0.08 0.00 0.10
#&gt; TCGA.ZB.A96D.01     2   0.502     0.7009 0.02 0.62 0.02 0.02 0.00 0.02 0.28 0.02
#&gt; TCGA.X7.A8DG.01     5   0.255     0.1962 0.04 0.00 0.00 0.00 0.84 0.00 0.00 0.12
#&gt; TCGA.4V.A9QI.01     1   0.491     0.3446 0.66 0.00 0.10 0.00 0.18 0.02 0.00 0.04
#&gt; TCGA.4V.A9QX.01     2   0.592     0.3483 0.00 0.46 0.06 0.00 0.00 0.06 0.36 0.06
#&gt; TCGA.4X.A9FB.01     5   0.128     0.2919 0.04 0.00 0.00 0.00 0.94 0.00 0.00 0.02
#&gt; TCGA.YT.A95E.01     5   0.767    -0.0165 0.28 0.02 0.16 0.04 0.36 0.06 0.00 0.08
#&gt; TCGA.X7.A8D7.01     6   0.377     1.0000 0.00 0.00 0.00 0.08 0.00 0.70 0.22 0.00
#&gt; TCGA.4V.A9QQ.01     2   0.308     0.6721 0.00 0.66 0.00 0.00 0.00 0.00 0.34 0.00
#&gt; TCGA.X7.A8M4.01     5   0.528    -0.1649 0.16 0.02 0.00 0.00 0.58 0.02 0.00 0.22
#&gt; TCGA.4V.A9QJ.01     8   0.454     0.7670 0.12 0.00 0.00 0.00 0.32 0.00 0.00 0.56
#&gt; TCGA.X7.A8D6.01     7   0.640     0.2826 0.00 0.16 0.06 0.02 0.00 0.04 0.52 0.20
#&gt; TCGA.ZC.AAAF.01     2   0.523     0.6746 0.02 0.66 0.04 0.02 0.00 0.02 0.20 0.04
#&gt; TCGA.4X.A9FC.01     2   0.408     0.5821 0.00 0.56 0.02 0.00 0.00 0.00 0.40 0.02
#&gt; TCGA.3T.AA9L.01     2   0.606     0.6240 0.02 0.56 0.10 0.02 0.00 0.04 0.24 0.02
#&gt; TCGA.XU.A92W.01     1   0.710    -0.0392 0.36 0.02 0.02 0.00 0.26 0.16 0.00 0.18
#&gt; TCGA.X7.A8DI.01     2   0.489     0.6736 0.02 0.62 0.04 0.00 0.00 0.02 0.28 0.02
#&gt; TCGA.XU.AAXY.01     5   0.558     0.2482 0.22 0.00 0.00 0.00 0.54 0.16 0.00 0.08
#&gt; TCGA.4V.A9QU.01     2   0.590     0.5370 0.00 0.54 0.08 0.04 0.00 0.02 0.28 0.04
#&gt; TCGA.X7.A8DF.01     1   0.598    -0.2113 0.38 0.06 0.00 0.00 0.32 0.00 0.00 0.24
#&gt; TCGA.XU.A932.01     5   0.578     0.2522 0.22 0.00 0.00 0.00 0.52 0.14 0.00 0.12
#&gt; TCGA.3G.AB0O.01     1   0.531     0.1134 0.56 0.00 0.04 0.02 0.32 0.02 0.00 0.04
#&gt; TCGA.X7.A8M7.01     1   0.313     0.3558 0.84 0.02 0.04 0.00 0.06 0.00 0.00 0.04
#&gt; TCGA.XM.A8R9.01     7   0.410     0.3405 0.00 0.20 0.02 0.00 0.00 0.00 0.70 0.08
#&gt; TCGA.XM.AAZ1.01     5   0.424    -0.1459 0.04 0.00 0.00 0.04 0.66 0.00 0.00 0.26
#&gt; TCGA.X7.A8DE.01     2   0.553     0.6176 0.02 0.52 0.04 0.02 0.00 0.02 0.36 0.02
#&gt; TCGA.X7.A8D7.11     6   0.377     1.0000 0.00 0.00 0.00 0.08 0.00 0.70 0.22 0.00
#&gt; TCGA.X7.A8M8.01     3   0.286     0.9911 0.20 0.00 0.78 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.X7.A8D6.11     7   0.640     0.2826 0.00 0.16 0.06 0.02 0.00 0.04 0.52 0.20
#&gt; TCGA.4V.A9QT.01     2   0.628     0.5113 0.00 0.54 0.12 0.04 0.00 0.04 0.22 0.04
#&gt; TCGA.XM.A8RL.01     5   0.345     0.3223 0.12 0.00 0.00 0.02 0.80 0.04 0.00 0.02
#&gt; TCGA.XM.A8RE.01     7   0.378     0.4609 0.00 0.16 0.04 0.00 0.00 0.02 0.76 0.02
#&gt; TCGA.XM.A8RH.01     7   0.161     0.6015 0.00 0.04 0.04 0.00 0.00 0.00 0.92 0.00
#&gt; TCGA.ZC.AAAH.01     5   0.141     0.2816 0.02 0.02 0.00 0.00 0.94 0.00 0.00 0.02
#&gt; TCGA.XH.A853.01     3   0.330     0.9822 0.20 0.02 0.76 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.X7.A8DD.01     7   0.227     0.5832 0.00 0.08 0.00 0.00 0.00 0.02 0.88 0.02
#&gt; TCGA.ZB.A96A.01     5   0.553    -0.1532 0.24 0.04 0.00 0.00 0.50 0.00 0.00 0.22
#&gt; TCGA.XU.AAY0.01     4   0.156     0.8986 0.00 0.00 0.00 0.90 0.00 0.00 0.10 0.00
#&gt; TCGA.XM.A8RB.01     7   0.806    -0.1196 0.00 0.14 0.12 0.16 0.00 0.12 0.36 0.10
#&gt; TCGA.ZB.A96R.01     5   0.374     0.1425 0.18 0.02 0.00 0.00 0.74 0.00 0.00 0.06
#&gt; TCGA.XM.A8RD.01     7   0.437    -0.1780 0.00 0.34 0.02 0.02 0.00 0.00 0.60 0.02
#&gt; TCGA.X7.A8DC.01     1   0.539     0.1276 0.54 0.08 0.00 0.00 0.10 0.00 0.00 0.28
#&gt; TCGA.YT.A95H.01     5   0.613    -0.1144 0.36 0.06 0.00 0.00 0.40 0.02 0.00 0.16
#&gt; TCGA.ZC.AAAA.01     1   0.520    -0.0790 0.46 0.02 0.02 0.00 0.44 0.04 0.00 0.02
#&gt; TCGA.XU.A92R.01     4   0.128     0.9420 0.00 0.02 0.00 0.94 0.00 0.00 0.04 0.00
#&gt; TCGA.YT.A95G.01     7   0.272     0.4802 0.00 0.18 0.02 0.00 0.00 0.00 0.80 0.00
#&gt; TCGA.XU.A92U.01     8   0.503     0.7560 0.08 0.00 0.00 0.04 0.38 0.00 0.00 0.50
#&gt; TCGA.3Q.A9WF.01     3   0.286     0.9911 0.20 0.00 0.78 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.XU.AAXV.01     7   0.326     0.5610 0.00 0.06 0.02 0.02 0.00 0.02 0.84 0.04
#&gt; TCGA.XU.AAXW.01     4   0.174     0.9405 0.00 0.02 0.00 0.92 0.00 0.00 0.04 0.02
#&gt; TCGA.4V.A9QW.01     1   0.539     0.1276 0.54 0.08 0.00 0.00 0.10 0.00 0.00 0.28
#&gt; TCGA.XU.AAXZ.01     5   0.651     0.0895 0.20 0.02 0.02 0.04 0.50 0.02 0.00 0.20
#&gt; TCGA.X7.A8DB.01     7   0.596    -0.0184 0.00 0.32 0.08 0.02 0.00 0.02 0.50 0.06
#&gt; TCGA.ZB.A96O.01     7   0.207     0.6066 0.00 0.04 0.04 0.00 0.00 0.00 0.90 0.02
#&gt; TCGA.XU.AAY1.01     4   0.128     0.9420 0.00 0.02 0.00 0.94 0.00 0.00 0.04 0.00
#&gt; TCGA.4V.A9QS.01     7   0.345     0.5829 0.00 0.06 0.08 0.00 0.00 0.00 0.80 0.06
#&gt; TCGA.X7.A8M6.01     1   0.549     0.1053 0.54 0.02 0.02 0.02 0.34 0.04 0.00 0.02
#&gt; TCGA.3G.AB0T.01     1   0.403     0.2614 0.72 0.00 0.16 0.00 0.10 0.02 0.00 0.00
#&gt; TCGA.4X.A9F9.01     2   0.498     0.5887 0.00 0.58 0.08 0.00 0.00 0.02 0.30 0.02
#&gt; TCGA.XU.A92Y.01     7   0.227     0.6067 0.00 0.02 0.00 0.02 0.00 0.00 0.88 0.08
#&gt; TCGA.ZB.A96B.01     1   0.489    -0.2120 0.56 0.02 0.34 0.00 0.06 0.02 0.00 0.00
#&gt; TCGA.ZB.A96P.01     5   0.513     0.1712 0.34 0.00 0.00 0.00 0.52 0.10 0.00 0.04
#&gt; TCGA.ZB.A963.01     5   0.705     0.0955 0.20 0.04 0.04 0.04 0.46 0.02 0.00 0.20
</code></pre>

<script>
$('#tab-node-01-get-classes-7-a').parent().next().next().hide();
$('#tab-node-01-get-classes-7-a').click(function(){
  $('#tab-node-01-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-01-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-01-consensus-heatmap'>
<ul>
<li><a href='#tab-node-01-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-01-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-01-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-01-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-01-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-01-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-01-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-01-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-01-membership-heatmap'>
<ul>
<li><a href='#tab-node-01-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-01-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-01-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-01-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-01-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-01-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-01-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-1-1.png" alt="plot of chunk tab-node-01-membership-heatmap-1"/></p>

</div>
<div id='tab-node-01-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-2-1.png" alt="plot of chunk tab-node-01-membership-heatmap-2"/></p>

</div>
<div id='tab-node-01-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-3-1.png" alt="plot of chunk tab-node-01-membership-heatmap-3"/></p>

</div>
<div id='tab-node-01-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-4-1.png" alt="plot of chunk tab-node-01-membership-heatmap-4"/></p>

</div>
<div id='tab-node-01-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-5-1.png" alt="plot of chunk tab-node-01-membership-heatmap-5"/></p>

</div>
<div id='tab-node-01-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-6-1.png" alt="plot of chunk tab-node-01-membership-heatmap-6"/></p>

</div>
<div id='tab-node-01-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-7-1.png" alt="plot of chunk tab-node-01-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-01-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-01-get-signatures'>
<ul>
<li><a href='#tab-node-01-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-01-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-01-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-01-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-01-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-01-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-01-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-1-1.png" alt="plot of chunk tab-node-01-get-signatures-1"/></p>

</div>
<div id='tab-node-01-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-2-1.png" alt="plot of chunk tab-node-01-get-signatures-2"/></p>

</div>
<div id='tab-node-01-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-3-1.png" alt="plot of chunk tab-node-01-get-signatures-3"/></p>

</div>
<div id='tab-node-01-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-4-1.png" alt="plot of chunk tab-node-01-get-signatures-4"/></p>

</div>
<div id='tab-node-01-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-5-1.png" alt="plot of chunk tab-node-01-get-signatures-5"/></p>

</div>
<div id='tab-node-01-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-6-1.png" alt="plot of chunk tab-node-01-get-signatures-6"/></p>

</div>
<div id='tab-node-01-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-7-1.png" alt="plot of chunk tab-node-01-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-01-signature_compare](figure_cola/node-01-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-01-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-01-dimension-reduction'>
<ul>
<li><a href='#tab-node-01-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-01-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-01-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-01-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-01-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-01-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-01-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-1-1.png" alt="plot of chunk tab-node-01-dimension-reduction-1"/></p>

</div>
<div id='tab-node-01-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-2-1.png" alt="plot of chunk tab-node-01-dimension-reduction-2"/></p>

</div>
<div id='tab-node-01-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-3-1.png" alt="plot of chunk tab-node-01-dimension-reduction-3"/></p>

</div>
<div id='tab-node-01-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-4-1.png" alt="plot of chunk tab-node-01-dimension-reduction-4"/></p>

</div>
<div id='tab-node-01-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-5-1.png" alt="plot of chunk tab-node-01-dimension-reduction-5"/></p>

</div>
<div id='tab-node-01-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-6-1.png" alt="plot of chunk tab-node-01-dimension-reduction-6"/></p>

</div>
<div id='tab-node-01-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-7-1.png" alt="plot of chunk tab-node-01-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-01-collect-classes](figure_cola/node-01-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node012


Parent node: [Node01](#Node01).
Child nodes: 
                Node0121-leaf
        ,
                Node0122-leaf
        ,
                Node0123-leaf
        ,
                Node0124-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["012"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 36 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'kmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 7.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-012-collect-plots](figure_cola/node-012-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-012-select-partition-number](figure_cola/node-012-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.5132 0.487   0.487
#> 3 3 0.692           0.580       0.762         0.2302 0.870   0.738
#> 4 4 1.000           0.993       0.994         0.1369 0.867   0.663
#> 5 5 0.882           0.591       0.752         0.0777 0.937   0.774
#> 6 6 0.908           0.664       0.798         0.0601 0.884   0.535
#> 7 7 0.923           0.937       0.898         0.0275 0.930   0.633
#> 8 8 0.879           0.918       0.882         0.0170 0.978   0.848
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 7
#> attr(,"optional")
#> [1] 2 4 6
```

There is also optional best $k$ = 2 4 6 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-012-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-012-get-classes'>
<ul>
<li><a href='#tab-node-012-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-012-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-012-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-012-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-012-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-012-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-012-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-012-get-classes-1'>
<p><a id='tab-node-012-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.XM.A8R8.01     2       0          1  0  1
#&gt; TCGA.XU.AAXX.01     1       0          1  1  0
#&gt; TCGA.ZT.A8OM.01     2       0          1  0  1
#&gt; TCGA.3S.AAYX.01     1       0          1  1  0
#&gt; TCGA.5U.AB0F.01     2       0          1  0  1
#&gt; TCGA.ZB.A96D.01     2       0          1  0  1
#&gt; TCGA.4V.A9QX.01     2       0          1  0  1
#&gt; TCGA.X7.A8D7.01     1       0          1  1  0
#&gt; TCGA.4V.A9QQ.01     1       0          1  1  0
#&gt; TCGA.X7.A8D6.01     1       0          1  1  0
#&gt; TCGA.ZC.AAAF.01     2       0          1  0  1
#&gt; TCGA.4X.A9FC.01     1       0          1  1  0
#&gt; TCGA.3T.AA9L.01     1       0          1  1  0
#&gt; TCGA.X7.A8DI.01     1       0          1  1  0
#&gt; TCGA.4V.A9QU.01     2       0          1  0  1
#&gt; TCGA.XM.A8R9.01     2       0          1  0  1
#&gt; TCGA.X7.A8DE.01     2       0          1  0  1
#&gt; TCGA.X7.A8D7.11     1       0          1  1  0
#&gt; TCGA.X7.A8D6.11     2       0          1  0  1
#&gt; TCGA.4V.A9QT.01     1       0          1  1  0
#&gt; TCGA.XM.A8RE.01     1       0          1  1  0
#&gt; TCGA.XM.A8RH.01     1       0          1  1  0
#&gt; TCGA.X7.A8DD.01     1       0          1  1  0
#&gt; TCGA.XU.AAY0.01     2       0          1  0  1
#&gt; TCGA.XM.A8RB.01     1       0          1  1  0
#&gt; TCGA.XM.A8RD.01     2       0          1  0  1
#&gt; TCGA.XU.A92R.01     2       0          1  0  1
#&gt; TCGA.YT.A95G.01     2       0          1  0  1
#&gt; TCGA.XU.AAXV.01     2       0          1  0  1
#&gt; TCGA.XU.AAXW.01     1       0          1  1  0
#&gt; TCGA.X7.A8DB.01     1       0          1  1  0
#&gt; TCGA.ZB.A96O.01     1       0          1  1  0
#&gt; TCGA.XU.AAY1.01     1       0          1  1  0
#&gt; TCGA.4V.A9QS.01     2       0          1  0  1
#&gt; TCGA.4X.A9F9.01     1       0          1  1  0
#&gt; TCGA.XU.A92Y.01     2       0          1  0  1
</code></pre>

<script>
$('#tab-node-012-get-classes-1-a').parent().next().next().hide();
$('#tab-node-012-get-classes-1-a').click(function(){
  $('#tab-node-012-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-012-get-classes-2'>
<p><a id='tab-node-012-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.XM.A8R8.01     3   0.628      0.353 0.00 0.46 0.54
#&gt; TCGA.XU.AAXX.01     1   0.628      0.468 0.54 0.00 0.46
#&gt; TCGA.ZT.A8OM.01     2   0.628      0.369 0.00 0.54 0.46
#&gt; TCGA.3S.AAYX.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.5U.AB0F.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.ZB.A96D.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.4V.A9QX.01     2   0.628      0.369 0.00 0.54 0.46
#&gt; TCGA.X7.A8D7.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.4V.A9QQ.01     3   0.966     -0.021 0.24 0.30 0.46
#&gt; TCGA.X7.A8D6.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.4X.A9FC.01     1   0.628      0.468 0.54 0.00 0.46
#&gt; TCGA.3T.AA9L.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.X7.A8DI.01     1   0.628      0.468 0.54 0.00 0.46
#&gt; TCGA.4V.A9QU.01     2   0.628      0.369 0.00 0.54 0.46
#&gt; TCGA.XM.A8R9.01     3   0.628      0.353 0.00 0.46 0.54
#&gt; TCGA.X7.A8DE.01     2   0.628      0.369 0.00 0.54 0.46
#&gt; TCGA.X7.A8D7.11     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.X7.A8D6.11     3   0.628      0.353 0.00 0.46 0.54
#&gt; TCGA.4V.A9QT.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.XM.A8RE.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.XM.A8RH.01     1   0.628      0.468 0.54 0.00 0.46
#&gt; TCGA.X7.A8DD.01     1   0.334      0.746 0.88 0.00 0.12
#&gt; TCGA.XU.AAY0.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.XM.A8RB.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.XM.A8RD.01     2   0.628      0.369 0.00 0.54 0.46
#&gt; TCGA.XU.A92R.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.YT.A95G.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.XU.AAXV.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.XU.AAXW.01     1   0.628      0.468 0.54 0.00 0.46
#&gt; TCGA.X7.A8DB.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.ZB.A96O.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.XU.AAY1.01     3   0.966     -0.021 0.24 0.30 0.46
#&gt; TCGA.4V.A9QS.01     2   0.000      0.665 0.00 1.00 0.00
#&gt; TCGA.4X.A9F9.01     1   0.000      0.814 1.00 0.00 0.00
#&gt; TCGA.XU.A92Y.01     2   0.000      0.665 0.00 1.00 0.00
</code></pre>

<script>
$('#tab-node-012-get-classes-2-a').parent().next().next().hide();
$('#tab-node-012-get-classes-2-a').click(function(){
  $('#tab-node-012-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-012-get-classes-3'>
<p><a id='tab-node-012-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.XM.A8R8.01     3  0.0000      0.993 0.00 0.00 1.00 0.00
#&gt; TCGA.XU.AAXX.01     4  0.0707      0.986 0.02 0.00 0.00 0.98
#&gt; TCGA.ZT.A8OM.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.3S.AAYX.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0F.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A96D.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.4V.A9QX.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8D7.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QQ.01     4  0.0707      0.976 0.00 0.02 0.00 0.98
#&gt; TCGA.X7.A8D6.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.4X.A9FC.01     4  0.0707      0.976 0.00 0.02 0.00 0.98
#&gt; TCGA.3T.AA9L.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DI.01     4  0.0707      0.986 0.02 0.00 0.00 0.98
#&gt; TCGA.4V.A9QU.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8R9.01     3  0.0707      0.986 0.00 0.00 0.98 0.02
#&gt; TCGA.X7.A8DE.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8D7.11     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D6.11     3  0.0000      0.993 0.00 0.00 1.00 0.00
#&gt; TCGA.4V.A9QT.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RE.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RH.01     4  0.0707      0.986 0.02 0.00 0.00 0.98
#&gt; TCGA.X7.A8DD.01     4  0.0707      0.986 0.02 0.00 0.00 0.98
#&gt; TCGA.XU.AAY0.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8RB.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RD.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.XU.A92R.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.YT.A95G.01     2  0.0707      0.981 0.00 0.98 0.00 0.02
#&gt; TCGA.XU.AAXV.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.XU.AAXW.01     4  0.0707      0.986 0.02 0.00 0.00 0.98
#&gt; TCGA.X7.A8DB.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96O.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAY1.01     4  0.0707      0.976 0.00 0.02 0.00 0.98
#&gt; TCGA.4V.A9QS.01     2  0.0000      0.997 0.00 1.00 0.00 0.00
#&gt; TCGA.4X.A9F9.01     1  0.0000      1.000 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Y.01     2  0.0707      0.981 0.00 0.98 0.00 0.02
</code></pre>

<script>
$('#tab-node-012-get-classes-3-a').parent().next().next().hide();
$('#tab-node-012-get-classes-3-a').click(function(){
  $('#tab-node-012-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-012-get-classes-4'>
<p><a id='tab-node-012-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3 p4   p5
#&gt; TCGA.XM.A8R8.01     3   0.423      0.966 0.00 0.00 0.58  0 0.42
#&gt; TCGA.XU.AAXX.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.ZT.A8OM.01     2   0.000      0.457 0.00 1.00 0.00  0 0.00
#&gt; TCGA.3S.AAYX.01     1   0.418      0.883 0.60 0.00 0.40  0 0.00
#&gt; TCGA.5U.AB0F.01     5   0.431      0.781 0.00 0.50 0.00  0 0.50
#&gt; TCGA.ZB.A96D.01     2   0.430     -0.792 0.00 0.52 0.00  0 0.48
#&gt; TCGA.4V.A9QX.01     2   0.000      0.457 0.00 1.00 0.00  0 0.00
#&gt; TCGA.X7.A8D7.01     1   0.418      0.883 0.60 0.00 0.40  0 0.00
#&gt; TCGA.4V.A9QQ.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.X7.A8D6.01     1   0.000      0.644 1.00 0.00 0.00  0 0.00
#&gt; TCGA.ZC.AAAF.01     2   0.431     -0.852 0.00 0.50 0.00  0 0.50
#&gt; TCGA.4X.A9FC.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.3T.AA9L.01     1   0.418      0.883 0.60 0.00 0.40  0 0.00
#&gt; TCGA.X7.A8DI.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.4V.A9QU.01     2   0.000      0.457 0.00 1.00 0.00  0 0.00
#&gt; TCGA.XM.A8R9.01     3   0.430      0.943 0.00 0.00 0.52  0 0.48
#&gt; TCGA.X7.A8DE.01     2   0.000      0.457 0.00 1.00 0.00  0 0.00
#&gt; TCGA.X7.A8D7.11     1   0.000      0.644 1.00 0.00 0.00  0 0.00
#&gt; TCGA.X7.A8D6.11     3   0.418      0.968 0.00 0.00 0.60  0 0.40
#&gt; TCGA.4V.A9QT.01     1   0.418      0.883 0.60 0.00 0.40  0 0.00
#&gt; TCGA.XM.A8RE.01     1   0.000      0.644 1.00 0.00 0.00  0 0.00
#&gt; TCGA.XM.A8RH.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.X7.A8DD.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.XU.AAY0.01     2   0.431     -0.852 0.00 0.50 0.00  0 0.50
#&gt; TCGA.XM.A8RB.01     1   0.418      0.883 0.60 0.00 0.40  0 0.00
#&gt; TCGA.XM.A8RD.01     2   0.000      0.457 0.00 1.00 0.00  0 0.00
#&gt; TCGA.XU.A92R.01     5   0.431      0.781 0.00 0.50 0.00  0 0.50
#&gt; TCGA.YT.A95G.01     5   0.423      0.813 0.00 0.42 0.00  0 0.58
#&gt; TCGA.XU.AAXV.01     2   0.430     -0.792 0.00 0.52 0.00  0 0.48
#&gt; TCGA.XU.AAXW.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.X7.A8DB.01     1   0.418      0.883 0.60 0.00 0.40  0 0.00
#&gt; TCGA.ZB.A96O.01     1   0.418      0.883 0.60 0.00 0.40  0 0.00
#&gt; TCGA.XU.AAY1.01     4   0.000      1.000 0.00 0.00 0.00  1 0.00
#&gt; TCGA.4V.A9QS.01     2   0.430     -0.792 0.00 0.52 0.00  0 0.48
#&gt; TCGA.4X.A9F9.01     1   0.413      0.875 0.62 0.00 0.38  0 0.00
#&gt; TCGA.XU.A92Y.01     5   0.423      0.813 0.00 0.42 0.00  0 0.58
</code></pre>

<script>
$('#tab-node-012-get-classes-4-a').parent().next().next().hide();
$('#tab-node-012-get-classes-4-a').click(function(){
  $('#tab-node-012-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-012-get-classes-5'>
<p><a id='tab-node-012-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.XM.A8R8.01     3  0.1267      0.900 0.00 0.00 0.94 0.00 0.00 0.06
#&gt; TCGA.XU.AAXX.01     4  0.0000      0.869 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZT.A8OM.01     2  0.0547      1.000 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.3S.AAYX.01     1  0.3869     -1.000 0.50 0.00 0.00 0.00 0.00 0.50
#&gt; TCGA.5U.AB0F.01     5  0.0000      0.939 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.ZB.A96D.01     5  0.0547      0.936 0.00 0.02 0.00 0.00 0.98 0.00
#&gt; TCGA.4V.A9QX.01     2  0.0547      1.000 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.X7.A8D7.01     1  0.3869     -1.000 0.50 0.00 0.00 0.00 0.00 0.50
#&gt; TCGA.4V.A9QQ.01     4  0.3076      0.869 0.00 0.00 0.00 0.76 0.00 0.24
#&gt; TCGA.X7.A8D6.01     1  0.0000      0.339 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     5  0.0547      0.936 0.00 0.00 0.00 0.00 0.98 0.02
#&gt; TCGA.4X.A9FC.01     4  0.3076      0.869 0.00 0.00 0.00 0.76 0.00 0.24
#&gt; TCGA.3T.AA9L.01     6  0.3869      1.000 0.50 0.00 0.00 0.00 0.00 0.50
#&gt; TCGA.X7.A8DI.01     4  0.3076      0.869 0.00 0.00 0.00 0.76 0.00 0.24
#&gt; TCGA.4V.A9QU.01     2  0.0547      1.000 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.XM.A8R9.01     3  0.2981      0.844 0.00 0.02 0.82 0.00 0.00 0.16
#&gt; TCGA.X7.A8DE.01     2  0.0547      1.000 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.X7.A8D7.11     1  0.0000      0.339 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D6.11     3  0.0000      0.908 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QT.01     6  0.3869      1.000 0.50 0.00 0.00 0.00 0.00 0.50
#&gt; TCGA.XM.A8RE.01     1  0.0000      0.339 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RH.01     4  0.0000      0.869 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8DD.01     4  0.0000      0.869 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XU.AAY0.01     5  0.0000      0.939 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XM.A8RB.01     6  0.3869      1.000 0.50 0.00 0.00 0.00 0.00 0.50
#&gt; TCGA.XM.A8RD.01     2  0.0547      1.000 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.XU.A92R.01     5  0.0547      0.936 0.00 0.00 0.00 0.00 0.98 0.02
#&gt; TCGA.YT.A95G.01     5  0.2981      0.826 0.00 0.02 0.00 0.00 0.82 0.16
#&gt; TCGA.XU.AAXV.01     5  0.1092      0.931 0.00 0.02 0.00 0.00 0.96 0.02
#&gt; TCGA.XU.AAXW.01     4  0.0000      0.869 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8DB.01     6  0.3869      1.000 0.50 0.00 0.00 0.00 0.00 0.50
#&gt; TCGA.ZB.A96O.01     1  0.3869     -1.000 0.50 0.00 0.00 0.00 0.00 0.50
#&gt; TCGA.XU.AAY1.01     4  0.3076      0.869 0.00 0.00 0.00 0.76 0.00 0.24
#&gt; TCGA.4V.A9QS.01     5  0.1092      0.931 0.00 0.02 0.00 0.00 0.96 0.02
#&gt; TCGA.4X.A9F9.01     1  0.3864     -0.920 0.52 0.00 0.00 0.00 0.00 0.48
#&gt; TCGA.XU.A92Y.01     5  0.2981      0.826 0.00 0.02 0.00 0.00 0.82 0.16
</code></pre>

<script>
$('#tab-node-012-get-classes-5-a').parent().next().next().hide();
$('#tab-node-012-get-classes-5-a').click(function(){
  $('#tab-node-012-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-012-get-classes-6'>
<p><a id='tab-node-012-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.XM.A8R8.01     3  0.3370      0.774 0.16 0.00 0.78 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.AAXX.01     4  0.0000      1.000 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.ZT.A8OM.01     2  0.0504      1.000 0.00 0.98 0.00 0.00 0.02 0.00 0.00
#&gt; TCGA.3S.AAYX.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.5U.AB0F.01     5  0.0000      0.901 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A96D.01     5  0.0504      0.896 0.00 0.02 0.00 0.00 0.98 0.00 0.00
#&gt; TCGA.4V.A9QX.01     2  0.0504      1.000 0.00 0.98 0.00 0.00 0.02 0.00 0.00
#&gt; TCGA.X7.A8D7.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.4V.A9QQ.01     7  0.4328      0.934 0.06 0.00 0.00 0.34 0.00 0.00 0.60
#&gt; TCGA.X7.A8D6.01     1  0.3139      1.000 0.70 0.00 0.00 0.00 0.00 0.30 0.00
#&gt; TCGA.ZC.AAAF.01     5  0.1006      0.892 0.02 0.00 0.00 0.00 0.96 0.00 0.02
#&gt; TCGA.4X.A9FC.01     7  0.3294      0.978 0.00 0.00 0.00 0.34 0.00 0.00 0.66
#&gt; TCGA.3T.AA9L.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.X7.A8DI.01     7  0.3294      0.978 0.00 0.00 0.00 0.34 0.00 0.00 0.66
#&gt; TCGA.4V.A9QU.01     2  0.0504      1.000 0.00 0.98 0.00 0.00 0.02 0.00 0.00
#&gt; TCGA.XM.A8R9.01     3  0.3680      0.752 0.06 0.02 0.78 0.00 0.00 0.00 0.14
#&gt; TCGA.X7.A8DE.01     2  0.0504      1.000 0.00 0.98 0.00 0.00 0.02 0.00 0.00
#&gt; TCGA.X7.A8D7.11     1  0.3139      1.000 0.70 0.00 0.00 0.00 0.00 0.30 0.00
#&gt; TCGA.X7.A8D6.11     3  0.0000      0.821 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QT.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XM.A8RE.01     1  0.3139      1.000 0.70 0.00 0.00 0.00 0.00 0.30 0.00
#&gt; TCGA.XM.A8RH.01     4  0.0000      1.000 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DD.01     4  0.0000      1.000 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.AAY0.01     5  0.0000      0.901 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8RB.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XM.A8RD.01     2  0.0504      1.000 0.00 0.98 0.00 0.00 0.02 0.00 0.00
#&gt; TCGA.XU.A92R.01     5  0.1006      0.892 0.02 0.00 0.00 0.00 0.96 0.00 0.02
#&gt; TCGA.YT.A95G.01     5  0.4479      0.645 0.06 0.02 0.00 0.00 0.66 0.00 0.26
#&gt; TCGA.XU.AAXV.01     5  0.0504      0.896 0.00 0.02 0.00 0.00 0.98 0.00 0.00
#&gt; TCGA.XU.AAXW.01     4  0.0000      1.000 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8DB.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.ZB.A96O.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XU.AAY1.01     7  0.3294      0.978 0.00 0.00 0.00 0.34 0.00 0.00 0.66
#&gt; TCGA.4V.A9QS.01     5  0.0000      0.901 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.4X.A9F9.01     6  0.0504      0.971 0.02 0.00 0.00 0.00 0.00 0.98 0.00
#&gt; TCGA.XU.A92Y.01     5  0.4479      0.645 0.06 0.02 0.00 0.00 0.66 0.00 0.26
</code></pre>

<script>
$('#tab-node-012-get-classes-6-a').parent().next().next().hide();
$('#tab-node-012-get-classes-6-a').click(function(){
  $('#tab-node-012-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-012-get-classes-7'>
<p><a id='tab-node-012-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7   p8
#&gt; TCGA.XM.A8R8.01     3  0.4856      0.574 0.24 0.00 0.62 0.08 0.00 0.00 0.00 0.06
#&gt; TCGA.XU.AAXX.01     4  0.2756      0.947 0.00 0.00 0.00 0.74 0.00 0.00 0.26 0.00
#&gt; TCGA.ZT.A8OM.01     2  0.0000      0.981 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.3S.AAYX.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.5U.AB0F.01     5  0.0000      0.895 0.00 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96D.01     5  0.0941      0.882 0.00 0.02 0.00 0.00 0.96 0.00 0.00 0.02
#&gt; TCGA.4V.A9QX.01     2  0.0000      0.981 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D7.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.4V.A9QQ.01     7  0.0471      0.980 0.00 0.00 0.00 0.00 0.00 0.00 0.98 0.02
#&gt; TCGA.X7.A8D6.01     1  0.2938      0.931 0.70 0.00 0.00 0.00 0.00 0.30 0.00 0.00
#&gt; TCGA.ZC.AAAF.01     5  0.1341      0.859 0.00 0.00 0.00 0.08 0.92 0.00 0.00 0.00
#&gt; TCGA.4X.A9FC.01     7  0.0000      0.993 0.00 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.3T.AA9L.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8DI.01     7  0.0000      0.993 0.00 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.4V.A9QU.01     2  0.0471      0.979 0.00 0.98 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.XM.A8R9.01     3  0.3015      0.457 0.00 0.00 0.68 0.00 0.00 0.00 0.00 0.32
#&gt; TCGA.X7.A8DE.01     2  0.0471      0.979 0.00 0.98 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.X7.A8D7.11     1  0.4857      0.857 0.52 0.00 0.00 0.00 0.00 0.30 0.00 0.18
#&gt; TCGA.X7.A8D6.11     3  0.0000      0.670 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QT.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8RE.01     1  0.2938      0.931 0.70 0.00 0.00 0.00 0.00 0.30 0.00 0.00
#&gt; TCGA.XM.A8RH.01     4  0.4191      0.947 0.02 0.00 0.00 0.66 0.00 0.00 0.26 0.06
#&gt; TCGA.X7.A8DD.01     4  0.4191      0.947 0.02 0.00 0.00 0.66 0.00 0.00 0.26 0.06
#&gt; TCGA.XU.AAY0.01     5  0.0000      0.895 0.00 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RB.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8RD.01     2  0.0941      0.959 0.00 0.96 0.00 0.02 0.00 0.00 0.00 0.02
#&gt; TCGA.XU.A92R.01     5  0.1341      0.859 0.00 0.00 0.00 0.08 0.92 0.00 0.00 0.00
#&gt; TCGA.YT.A95G.01     8  0.3142      1.000 0.00 0.00 0.00 0.00 0.36 0.00 0.00 0.64
#&gt; TCGA.XU.AAXV.01     5  0.2132      0.841 0.04 0.00 0.00 0.08 0.88 0.00 0.00 0.00
#&gt; TCGA.XU.AAXW.01     4  0.2756      0.947 0.00 0.00 0.00 0.74 0.00 0.00 0.26 0.00
#&gt; TCGA.X7.A8DB.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A96O.01     6  0.0000      0.996 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XU.AAY1.01     7  0.0000      0.993 0.00 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.4V.A9QS.01     5  0.2132      0.841 0.04 0.00 0.00 0.08 0.88 0.00 0.00 0.00
#&gt; TCGA.4X.A9F9.01     6  0.0471      0.970 0.02 0.00 0.00 0.00 0.00 0.98 0.00 0.00
#&gt; TCGA.XU.A92Y.01     8  0.3142      1.000 0.00 0.00 0.00 0.00 0.36 0.00 0.00 0.64
</code></pre>

<script>
$('#tab-node-012-get-classes-7-a').parent().next().next().hide();
$('#tab-node-012-get-classes-7-a').click(function(){
  $('#tab-node-012-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-012-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-012-consensus-heatmap'>
<ul>
<li><a href='#tab-node-012-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-012-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-012-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-012-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-012-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-012-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-012-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-012-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-012-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-012-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-012-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-012-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-012-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-012-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-012-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-012-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-012-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-012-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-012-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-012-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-012-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-012-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-012-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-012-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-012-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-012-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-012-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-012-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-012-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-012-membership-heatmap'>
<ul>
<li><a href='#tab-node-012-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-012-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-012-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-012-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-012-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-012-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-012-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-012-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-012-membership-heatmap-1-1.png" alt="plot of chunk tab-node-012-membership-heatmap-1"/></p>

</div>
<div id='tab-node-012-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-012-membership-heatmap-2-1.png" alt="plot of chunk tab-node-012-membership-heatmap-2"/></p>

</div>
<div id='tab-node-012-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-012-membership-heatmap-3-1.png" alt="plot of chunk tab-node-012-membership-heatmap-3"/></p>

</div>
<div id='tab-node-012-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-012-membership-heatmap-4-1.png" alt="plot of chunk tab-node-012-membership-heatmap-4"/></p>

</div>
<div id='tab-node-012-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-012-membership-heatmap-5-1.png" alt="plot of chunk tab-node-012-membership-heatmap-5"/></p>

</div>
<div id='tab-node-012-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-012-membership-heatmap-6-1.png" alt="plot of chunk tab-node-012-membership-heatmap-6"/></p>

</div>
<div id='tab-node-012-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-012-membership-heatmap-7-1.png" alt="plot of chunk tab-node-012-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-012-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-012-get-signatures'>
<ul>
<li><a href='#tab-node-012-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-012-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-012-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-012-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-012-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-012-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-012-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-012-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-012-get-signatures-1-1.png" alt="plot of chunk tab-node-012-get-signatures-1"/></p>

</div>
<div id='tab-node-012-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-012-get-signatures-2-1.png" alt="plot of chunk tab-node-012-get-signatures-2"/></p>

</div>
<div id='tab-node-012-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-012-get-signatures-3-1.png" alt="plot of chunk tab-node-012-get-signatures-3"/></p>

</div>
<div id='tab-node-012-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-012-get-signatures-4-1.png" alt="plot of chunk tab-node-012-get-signatures-4"/></p>

</div>
<div id='tab-node-012-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-012-get-signatures-5-1.png" alt="plot of chunk tab-node-012-get-signatures-5"/></p>

</div>
<div id='tab-node-012-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-012-get-signatures-6-1.png" alt="plot of chunk tab-node-012-get-signatures-6"/></p>

</div>
<div id='tab-node-012-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-012-get-signatures-7-1.png" alt="plot of chunk tab-node-012-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-012-signature_compare](figure_cola/node-012-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-012-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-012-dimension-reduction'>
<ul>
<li><a href='#tab-node-012-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-012-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-012-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-012-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-012-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-012-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-012-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-012-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-012-dimension-reduction-1-1.png" alt="plot of chunk tab-node-012-dimension-reduction-1"/></p>

</div>
<div id='tab-node-012-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-012-dimension-reduction-2-1.png" alt="plot of chunk tab-node-012-dimension-reduction-2"/></p>

</div>
<div id='tab-node-012-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-012-dimension-reduction-3-1.png" alt="plot of chunk tab-node-012-dimension-reduction-3"/></p>

</div>
<div id='tab-node-012-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-012-dimension-reduction-4-1.png" alt="plot of chunk tab-node-012-dimension-reduction-4"/></p>

</div>
<div id='tab-node-012-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-012-dimension-reduction-5-1.png" alt="plot of chunk tab-node-012-dimension-reduction-5"/></p>

</div>
<div id='tab-node-012-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-012-dimension-reduction-6-1.png" alt="plot of chunk tab-node-012-dimension-reduction-6"/></p>

</div>
<div id='tab-node-012-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-012-dimension-reduction-7-1.png" alt="plot of chunk tab-node-012-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-012-collect-classes](figure_cola/node-012-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node02


Parent node: [Node0](#Node0).
Child nodes: 
                Node011-leaf
        ,
                [Node012](#Node012)
        ,
                Node021-leaf
        ,
                Node022-leaf
        ,
                Node023-leaf
        ,
                Node024-leaf
        ,
                Node031-leaf
        ,
                Node032-leaf
        ,
                Node033-leaf
        ,
                Node034-leaf
        ,
                Node041-leaf
        ,
                Node042-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["02"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 19 columns.
#>   Top rows (1000) are extracted by 'SD' method.
#>   Subgroups are detected by 'kmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 4.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-02-collect-plots](figure_cola/node-02-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-02-select-partition-number](figure_cola/node-02-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 0.135           0.425       0.754         0.4960 0.474   0.474
#> 3 3 0.374           0.669       0.820         0.3763 0.690   0.430
#> 4 4 0.906           0.961       0.953         0.1411 0.836   0.517
#> 5 5 0.895           0.889       0.912         0.0486 1.000   1.000
#> 6 6 0.842           0.842       0.858         0.0325 0.977   0.889
#> 7 7 0.830           0.792       0.848         0.0339 0.942   0.688
#> 8 8 0.825           0.565       0.776         0.0207 0.977   0.818
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 4
```


Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-02-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-02-get-classes'>
<ul>
<li><a href='#tab-node-02-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-02-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-02-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-02-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-02-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-02-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-02-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-02-get-classes-1'>
<p><a id='tab-node-02-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2
#&gt; TCGA.ZB.A965.01     2   0.999      0.391 0.48 0.52
#&gt; TCGA.ZB.A96C.01     2   0.680      0.397 0.18 0.82
#&gt; TCGA.ZB.A969.01     2   0.722      0.373 0.20 0.80
#&gt; TCGA.XM.AAZ2.01     1   0.925      0.405 0.66 0.34
#&gt; TCGA.XM.A8RG.01     1   0.000      0.646 1.00 0.00
#&gt; TCGA.3G.AB0Q.01     1   0.990     -0.252 0.56 0.44
#&gt; TCGA.4X.A9FA.01     1   0.680      0.490 0.82 0.18
#&gt; TCGA.XM.A8RF.01     1   0.995      0.255 0.54 0.46
#&gt; TCGA.ZL.A9V6.01     1   0.000      0.646 1.00 0.00
#&gt; TCGA.XU.A92O.01     1   0.000      0.646 1.00 0.00
#&gt; TCGA.ZB.A962.01     2   0.904      0.500 0.32 0.68
#&gt; TCGA.YT.A95D.01     2   0.680      0.397 0.18 0.82
#&gt; TCGA.ZB.A96L.01     2   0.722      0.373 0.20 0.80
#&gt; TCGA.ZB.A96H.01     1   0.141      0.625 0.98 0.02
#&gt; TCGA.XU.A92T.01     2   0.904      0.500 0.32 0.68
#&gt; TCGA.3G.AB19.01     1   0.995      0.255 0.54 0.46
#&gt; TCGA.XM.AAZ3.01     1   0.000      0.646 1.00 0.00
#&gt; TCGA.ZB.A964.01     2   0.999      0.391 0.48 0.52
#&gt; TCGA.XU.A92Q.01     2   0.999      0.391 0.48 0.52
</code></pre>

<script>
$('#tab-node-02-get-classes-1-a').parent().next().next().hide();
$('#tab-node-02-get-classes-1-a').click(function(){
  $('#tab-node-02-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-2'>
<p><a id='tab-node-02-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.ZB.A965.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.ZB.A96C.01     3   0.788      0.489 0.10 0.26 0.64
#&gt; TCGA.ZB.A969.01     3   0.383      0.604 0.02 0.10 0.88
#&gt; TCGA.XM.AAZ2.01     1   0.613      0.233 0.60 0.00 0.40
#&gt; TCGA.XM.A8RG.01     1   0.296      0.789 0.90 0.10 0.00
#&gt; TCGA.3G.AB0Q.01     3   0.991      0.217 0.30 0.30 0.40
#&gt; TCGA.4X.A9FA.01     1   0.685      0.241 0.60 0.02 0.38
#&gt; TCGA.XM.A8RF.01     3   0.540      0.446 0.28 0.00 0.72
#&gt; TCGA.ZL.A9V6.01     1   0.296      0.789 0.90 0.10 0.00
#&gt; TCGA.XU.A92O.01     1   0.296      0.789 0.90 0.10 0.00
#&gt; TCGA.ZB.A962.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.YT.A95D.01     3   0.788      0.489 0.10 0.26 0.64
#&gt; TCGA.ZB.A96L.01     3   0.383      0.604 0.02 0.10 0.88
#&gt; TCGA.ZB.A96H.01     1   0.296      0.789 0.90 0.10 0.00
#&gt; TCGA.XU.A92T.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.3G.AB19.01     3   0.540      0.446 0.28 0.00 0.72
#&gt; TCGA.XM.AAZ3.01     1   0.296      0.789 0.90 0.10 0.00
#&gt; TCGA.ZB.A964.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.XU.A92Q.01     2   0.000      1.000 0.00 1.00 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-2-a').parent().next().next().hide();
$('#tab-node-02-get-classes-2-a').click(function(){
  $('#tab-node-02-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-3'>
<p><a id='tab-node-02-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.ZB.A965.01     2  0.1913      0.965 0.00 0.94 0.04 0.02
#&gt; TCGA.ZB.A96C.01     4  0.2011      0.953 0.00 0.08 0.00 0.92
#&gt; TCGA.ZB.A969.01     3  0.1211      0.936 0.00 0.00 0.96 0.04
#&gt; TCGA.XM.AAZ2.01     4  0.2706      0.913 0.08 0.02 0.00 0.90
#&gt; TCGA.XM.A8RG.01     1  0.0000      0.990 1.00 0.00 0.00 0.00
#&gt; TCGA.3G.AB0Q.01     4  0.2011      0.953 0.00 0.08 0.00 0.92
#&gt; TCGA.4X.A9FA.01     4  0.2335      0.931 0.06 0.02 0.00 0.92
#&gt; TCGA.XM.A8RF.01     3  0.3198      0.937 0.04 0.00 0.88 0.08
#&gt; TCGA.ZL.A9V6.01     1  0.0000      0.990 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     1  0.0000      0.990 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A962.01     2  0.0000      0.975 0.00 1.00 0.00 0.00
#&gt; TCGA.YT.A95D.01     4  0.2011      0.953 0.00 0.08 0.00 0.92
#&gt; TCGA.ZB.A96L.01     3  0.1211      0.936 0.00 0.00 0.96 0.04
#&gt; TCGA.ZB.A96H.01     1  0.1211      0.960 0.96 0.00 0.04 0.00
#&gt; TCGA.XU.A92T.01     2  0.0707      0.986 0.00 0.98 0.00 0.02
#&gt; TCGA.3G.AB19.01     3  0.3198      0.937 0.04 0.00 0.88 0.08
#&gt; TCGA.XM.AAZ3.01     1  0.0000      0.990 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A964.01     2  0.0707      0.986 0.00 0.98 0.00 0.02
#&gt; TCGA.XU.A92Q.01     2  0.0707      0.986 0.00 0.98 0.00 0.02
</code></pre>

<script>
$('#tab-node-02-get-classes-3-a').parent().next().next().hide();
$('#tab-node-02-get-classes-3-a').click(function(){
  $('#tab-node-02-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-4'>
<p><a id='tab-node-02-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.ZB.A965.01     2   0.165      0.899 0.02 0.94 0.04 0.00 0.00
#&gt; TCGA.ZB.A96C.01     4   0.293      0.885 0.00 0.00 0.18 0.82 0.00
#&gt; TCGA.ZB.A969.01     5   0.000      0.817 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.XM.AAZ2.01     4   0.000      0.925 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XM.A8RG.01     1   0.252      0.904 0.86 0.00 0.14 0.00 0.00
#&gt; TCGA.3G.AB0Q.01     4   0.000      0.925 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.4X.A9FA.01     4   0.000      0.925 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XM.A8RF.01     5   0.406      0.817 0.00 0.00 0.36 0.00 0.64
#&gt; TCGA.ZL.A9V6.01     1   0.000      0.948 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     1   0.000      0.948 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A962.01     2   0.368      0.741 0.00 0.72 0.28 0.00 0.00
#&gt; TCGA.YT.A95D.01     4   0.293      0.885 0.00 0.00 0.18 0.82 0.00
#&gt; TCGA.ZB.A96L.01     5   0.000      0.817 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.ZB.A96H.01     1   0.104      0.932 0.96 0.00 0.04 0.00 0.00
#&gt; TCGA.XU.A92T.01     2   0.000      0.928 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.3G.AB19.01     5   0.406      0.817 0.00 0.00 0.36 0.00 0.64
#&gt; TCGA.XM.AAZ3.01     1   0.173      0.933 0.92 0.00 0.08 0.00 0.00
#&gt; TCGA.ZB.A964.01     2   0.000      0.928 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2   0.000      0.928 0.00 1.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-4-a').parent().next().next().hide();
$('#tab-node-02-get-classes-4-a').click(function(){
  $('#tab-node-02-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-5'>
<p><a id='tab-node-02-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.ZB.A965.01     2  0.3073      0.787 0.00 0.84 0.08 0.00 0.00 0.08
#&gt; TCGA.ZB.A96C.01     4  0.0000      0.771 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A969.01     6  0.3647      1.000 0.00 0.00 0.00 0.00 0.36 0.64
#&gt; TCGA.XM.AAZ2.01     4  0.4144      0.811 0.00 0.00 0.36 0.62 0.00 0.02
#&gt; TCGA.XM.A8RG.01     1  0.4067      0.762 0.70 0.00 0.26 0.00 0.00 0.04
#&gt; TCGA.3G.AB0Q.01     4  0.3499      0.839 0.00 0.00 0.32 0.68 0.00 0.00
#&gt; TCGA.4X.A9FA.01     4  0.3499      0.839 0.00 0.00 0.32 0.68 0.00 0.00
#&gt; TCGA.XM.A8RF.01     5  0.0000      0.978 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.ZL.A9V6.01     1  0.0000      0.874 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     1  0.0000      0.874 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A962.01     2  0.5712      0.491 0.00 0.52 0.26 0.00 0.00 0.22
#&gt; TCGA.YT.A95D.01     4  0.0000      0.771 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A96L.01     6  0.3647      1.000 0.00 0.00 0.00 0.00 0.36 0.64
#&gt; TCGA.ZB.A96H.01     1  0.2474      0.814 0.88 0.00 0.08 0.00 0.00 0.04
#&gt; TCGA.XU.A92T.01     2  0.0547      0.852 0.00 0.98 0.00 0.00 0.00 0.02
#&gt; TCGA.3G.AB19.01     5  0.0547      0.978 0.00 0.00 0.02 0.00 0.98 0.00
#&gt; TCGA.XM.AAZ3.01     1  0.2790      0.842 0.84 0.00 0.14 0.00 0.00 0.02
#&gt; TCGA.ZB.A964.01     2  0.0000      0.856 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.0000      0.856 0.00 1.00 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-5-a').parent().next().next().hide();
$('#tab-node-02-get-classes-5-a').click(function(){
  $('#tab-node-02-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-6'>
<p><a id='tab-node-02-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.ZB.A965.01     2  0.5086      0.458 0.00 0.64 0.22 0.00 0.00 0.06 0.08
#&gt; TCGA.ZB.A96C.01     7  0.3358      1.000 0.00 0.00 0.00 0.36 0.00 0.00 0.64
#&gt; TCGA.ZB.A969.01     6  0.2832      0.981 0.00 0.00 0.00 0.00 0.24 0.76 0.00
#&gt; TCGA.XM.AAZ2.01     4  0.1928      0.872 0.00 0.00 0.00 0.90 0.00 0.08 0.02
#&gt; TCGA.XM.A8RG.01     1  0.5412      0.601 0.60 0.00 0.08 0.00 0.00 0.08 0.24
#&gt; TCGA.3G.AB0Q.01     4  0.0000      0.937 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FA.01     4  0.0000      0.937 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RF.01     5  0.0504      0.981 0.00 0.00 0.02 0.00 0.98 0.00 0.00
#&gt; TCGA.ZL.A9V6.01     1  0.0000      0.781 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92O.01     1  0.0000      0.781 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A962.01     3  0.3221      0.000 0.00 0.32 0.68 0.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95D.01     7  0.3358      1.000 0.00 0.00 0.00 0.36 0.00 0.00 0.64
#&gt; TCGA.ZB.A96L.01     6  0.3307      0.981 0.00 0.00 0.00 0.00 0.24 0.74 0.02
#&gt; TCGA.ZB.A96H.01     1  0.4457      0.575 0.72 0.00 0.16 0.00 0.00 0.06 0.06
#&gt; TCGA.XU.A92T.01     2  0.0504      0.809 0.00 0.98 0.02 0.00 0.00 0.00 0.00
#&gt; TCGA.3G.AB19.01     5  0.0000      0.981 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.AAZ3.01     1  0.3086      0.738 0.80 0.00 0.04 0.00 0.00 0.00 0.16
#&gt; TCGA.ZB.A964.01     2  0.0000      0.812 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.0000      0.812 0.00 1.00 0.00 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-6-a').parent().next().next().hide();
$('#tab-node-02-get-classes-6-a').click(function(){
  $('#tab-node-02-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-7'>
<p><a id='tab-node-02-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7   p8
#&gt; TCGA.ZB.A965.01     2  0.4756      0.373 0.00 0.56 0.00 0.00 0.00 0.04 0.06 0.34
#&gt; TCGA.ZB.A96C.01     7  0.3193      1.000 0.00 0.00 0.00 0.38 0.00 0.00 0.62 0.00
#&gt; TCGA.ZB.A969.01     6  0.3299      0.944 0.00 0.00 0.00 0.00 0.18 0.76 0.06 0.00
#&gt; TCGA.XM.AAZ2.01     4  0.3637      0.730 0.00 0.00 0.04 0.80 0.00 0.02 0.06 0.08
#&gt; TCGA.XM.A8RG.01     1  0.5532      0.255 0.64 0.00 0.08 0.00 0.00 0.10 0.10 0.08
#&gt; TCGA.3G.AB0Q.01     4  0.0000      0.864 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FA.01     4  0.0000      0.864 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RF.01     5  0.3185      0.833 0.00 0.00 0.04 0.00 0.82 0.00 0.08 0.06
#&gt; TCGA.ZL.A9V6.01     1  0.3318     -0.246 0.54 0.00 0.00 0.00 0.00 0.00 0.00 0.46
#&gt; TCGA.XU.A92O.01     1  0.3318     -0.246 0.54 0.00 0.00 0.00 0.00 0.00 0.00 0.46
#&gt; TCGA.ZB.A962.01     3  0.2114      0.000 0.00 0.16 0.84 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.YT.A95D.01     7  0.3193      1.000 0.00 0.00 0.00 0.38 0.00 0.00 0.62 0.00
#&gt; TCGA.ZB.A96L.01     6  0.2267      0.944 0.00 0.00 0.00 0.00 0.18 0.82 0.00 0.00
#&gt; TCGA.ZB.A96H.01     8  0.2938      0.000 0.30 0.00 0.00 0.00 0.00 0.00 0.00 0.70
#&gt; TCGA.XU.A92T.01     2  0.0941      0.770 0.00 0.96 0.02 0.00 0.00 0.00 0.02 0.00
#&gt; TCGA.3G.AB19.01     5  0.0000      0.833 0.00 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.AAZ3.01     1  0.0000      0.287 1.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A964.01     2  0.0808      0.771 0.00 0.96 0.04 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XU.A92Q.01     2  0.1408      0.767 0.00 0.94 0.02 0.00 0.00 0.02 0.00 0.02
</code></pre>

<script>
$('#tab-node-02-get-classes-7-a').parent().next().next().hide();
$('#tab-node-02-get-classes-7-a').click(function(){
  $('#tab-node-02-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-02-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-02-consensus-heatmap'>
<ul>
<li><a href='#tab-node-02-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-02-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-02-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-02-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-02-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-02-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-02-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-02-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-02-membership-heatmap'>
<ul>
<li><a href='#tab-node-02-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-02-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-02-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-02-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-02-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-02-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-02-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-1-1.png" alt="plot of chunk tab-node-02-membership-heatmap-1"/></p>

</div>
<div id='tab-node-02-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-2-1.png" alt="plot of chunk tab-node-02-membership-heatmap-2"/></p>

</div>
<div id='tab-node-02-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-3-1.png" alt="plot of chunk tab-node-02-membership-heatmap-3"/></p>

</div>
<div id='tab-node-02-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-4-1.png" alt="plot of chunk tab-node-02-membership-heatmap-4"/></p>

</div>
<div id='tab-node-02-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-5-1.png" alt="plot of chunk tab-node-02-membership-heatmap-5"/></p>

</div>
<div id='tab-node-02-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-6-1.png" alt="plot of chunk tab-node-02-membership-heatmap-6"/></p>

</div>
<div id='tab-node-02-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-7-1.png" alt="plot of chunk tab-node-02-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-02-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-02-get-signatures'>
<ul>
<li><a href='#tab-node-02-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-02-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-02-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-02-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-02-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-02-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-02-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-1-1.png" alt="plot of chunk tab-node-02-get-signatures-1"/></p>

</div>
<div id='tab-node-02-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-2-1.png" alt="plot of chunk tab-node-02-get-signatures-2"/></p>

</div>
<div id='tab-node-02-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-3-1.png" alt="plot of chunk tab-node-02-get-signatures-3"/></p>

</div>
<div id='tab-node-02-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-4-1.png" alt="plot of chunk tab-node-02-get-signatures-4"/></p>

</div>
<div id='tab-node-02-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-5-1.png" alt="plot of chunk tab-node-02-get-signatures-5"/></p>

</div>
<div id='tab-node-02-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-6-1.png" alt="plot of chunk tab-node-02-get-signatures-6"/></p>

</div>
<div id='tab-node-02-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-7-1.png" alt="plot of chunk tab-node-02-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-02-signature_compare](figure_cola/node-02-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-02-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-02-dimension-reduction'>
<ul>
<li><a href='#tab-node-02-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-02-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-02-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-02-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-02-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-02-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-02-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-1-1.png" alt="plot of chunk tab-node-02-dimension-reduction-1"/></p>

</div>
<div id='tab-node-02-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-2-1.png" alt="plot of chunk tab-node-02-dimension-reduction-2"/></p>

</div>
<div id='tab-node-02-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-3-1.png" alt="plot of chunk tab-node-02-dimension-reduction-3"/></p>

</div>
<div id='tab-node-02-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-4-1.png" alt="plot of chunk tab-node-02-dimension-reduction-4"/></p>

</div>
<div id='tab-node-02-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-5-1.png" alt="plot of chunk tab-node-02-dimension-reduction-5"/></p>

</div>
<div id='tab-node-02-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-6-1.png" alt="plot of chunk tab-node-02-dimension-reduction-6"/></p>

</div>
<div id='tab-node-02-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-7-1.png" alt="plot of chunk tab-node-02-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-02-collect-classes](figure_cola/node-02-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node03


Parent node: [Node0](#Node0).
Child nodes: 
                Node011-leaf
        ,
                [Node012](#Node012)
        ,
                Node021-leaf
        ,
                Node022-leaf
        ,
                Node023-leaf
        ,
                Node024-leaf
        ,
                Node031-leaf
        ,
                Node032-leaf
        ,
                Node033-leaf
        ,
                Node034-leaf
        ,
                Node041-leaf
        ,
                Node042-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["03"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 24 columns.
#>   Top rows (1000) are extracted by 'SD' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 4.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-03-collect-plots](figure_cola/node-03-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-03-select-partition-number](figure_cola/node-03-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 0.482           0.935       0.945         0.5121 0.482   0.482
#> 3 3 1.000           1.000       1.000         0.3590 0.714   0.466
#> 4 4 1.000           0.998       0.996         0.0777 0.946   0.821
#> 5 5 0.945           0.916       0.967         0.0420 0.975   0.899
#> 6 6 0.853           0.820       0.907         0.0386 1.000   1.000
#> 7 7 0.866           0.645       0.883         0.0325 0.953   0.790
#> 8 8 0.846           0.636       0.873         0.0223 0.986   0.918
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 4
#> attr(,"optional")
#> [1] 3
```

There is also optional best $k$ = 3 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-03-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-03-get-classes'>
<ul>
<li><a href='#tab-node-03-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-03-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-03-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-03-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-03-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-03-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-03-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-03-get-classes-1'>
<p><a id='tab-node-03-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2
#&gt; TCGA.ZB.A96K.01     2   0.529      0.943 0.12 0.88
#&gt; TCGA.XU.A930.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.ZB.A96M.01     2   0.000      0.910 0.00 1.00
#&gt; TCGA.ZB.A96Q.01     2   0.529      0.943 0.12 0.88
#&gt; TCGA.X7.A8D9.01     2   0.000      0.910 0.00 1.00
#&gt; TCGA.5V.A9RR.01     2   0.529      0.943 0.12 0.88
#&gt; TCGA.ZB.A961.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.XM.A8RC.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.X7.A8M1.01     2   0.529      0.943 0.12 0.88
#&gt; TCGA.4X.A9FD.01     1   0.529      0.891 0.88 0.12
#&gt; TCGA.5K.AAAP.01     2   0.529      0.943 0.12 0.88
#&gt; TCGA.XU.A92X.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.5G.A9ZZ.01     1   0.529      0.891 0.88 0.12
#&gt; TCGA.3G.AB14.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.YT.A95F.01     2   0.000      0.910 0.00 1.00
#&gt; TCGA.4V.A9QR.01     1   0.529      0.891 0.88 0.12
#&gt; TCGA.XM.A8RI.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.4V.A9QL.01     2   0.000      0.910 0.00 1.00
#&gt; TCGA.X7.A8M0.01     2   0.000      0.910 0.00 1.00
#&gt; TCGA.ZB.A96F.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.X7.A8D8.01     2   0.529      0.943 0.12 0.88
#&gt; TCGA.4V.A9QM.01     2   0.529      0.943 0.12 0.88
#&gt; TCGA.5U.AB0E.01     1   0.000      0.959 1.00 0.00
#&gt; TCGA.ZB.A96E.01     2   0.529      0.943 0.12 0.88
</code></pre>

<script>
$('#tab-node-03-get-classes-1-a').parent().next().next().hide();
$('#tab-node-03-get-classes-1-a').click(function(){
  $('#tab-node-03-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-2'>
<p><a id='tab-node-03-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2 p3
#&gt; TCGA.ZB.A96K.01     2       0          1  0  1  0
#&gt; TCGA.XU.A930.01     1       0          1  1  0  0
#&gt; TCGA.ZB.A96M.01     3       0          1  0  0  1
#&gt; TCGA.ZB.A96Q.01     2       0          1  0  1  0
#&gt; TCGA.X7.A8D9.01     3       0          1  0  0  1
#&gt; TCGA.5V.A9RR.01     2       0          1  0  1  0
#&gt; TCGA.ZB.A961.01     1       0          1  1  0  0
#&gt; TCGA.XM.A8RC.01     1       0          1  1  0  0
#&gt; TCGA.X7.A8M1.01     2       0          1  0  1  0
#&gt; TCGA.4X.A9FD.01     3       0          1  0  0  1
#&gt; TCGA.5K.AAAP.01     2       0          1  0  1  0
#&gt; TCGA.XU.A92X.01     1       0          1  1  0  0
#&gt; TCGA.5G.A9ZZ.01     3       0          1  0  0  1
#&gt; TCGA.3G.AB14.01     1       0          1  1  0  0
#&gt; TCGA.YT.A95F.01     3       0          1  0  0  1
#&gt; TCGA.4V.A9QR.01     3       0          1  0  0  1
#&gt; TCGA.XM.A8RI.01     1       0          1  1  0  0
#&gt; TCGA.4V.A9QL.01     3       0          1  0  0  1
#&gt; TCGA.X7.A8M0.01     3       0          1  0  0  1
#&gt; TCGA.ZB.A96F.01     1       0          1  1  0  0
#&gt; TCGA.X7.A8D8.01     2       0          1  0  1  0
#&gt; TCGA.4V.A9QM.01     2       0          1  0  1  0
#&gt; TCGA.5U.AB0E.01     1       0          1  1  0  0
#&gt; TCGA.ZB.A96E.01     2       0          1  0  1  0
</code></pre>

<script>
$('#tab-node-03-get-classes-2-a').parent().next().next().hide();
$('#tab-node-03-get-classes-2-a').click(function(){
  $('#tab-node-03-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-3'>
<p><a id='tab-node-03-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2   p3   p4
#&gt; TCGA.ZB.A96K.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.XU.A930.01     1  0.0707      0.985 0.98  0 0.00 0.02
#&gt; TCGA.ZB.A96M.01     3  0.0000      1.000 0.00  0 1.00 0.00
#&gt; TCGA.ZB.A96Q.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.X7.A8D9.01     3  0.0000      1.000 0.00  0 1.00 0.00
#&gt; TCGA.5V.A9RR.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.ZB.A961.01     1  0.0707      0.985 0.98  0 0.00 0.02
#&gt; TCGA.XM.A8RC.01     1  0.0000      0.995 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8M1.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4X.A9FD.01     4  0.0707      1.000 0.00  0 0.02 0.98
#&gt; TCGA.5K.AAAP.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.XU.A92X.01     1  0.0000      0.995 1.00  0 0.00 0.00
#&gt; TCGA.5G.A9ZZ.01     4  0.0707      1.000 0.00  0 0.02 0.98
#&gt; TCGA.3G.AB14.01     1  0.0000      0.995 1.00  0 0.00 0.00
#&gt; TCGA.YT.A95F.01     3  0.0000      1.000 0.00  0 1.00 0.00
#&gt; TCGA.4V.A9QR.01     4  0.0707      1.000 0.00  0 0.02 0.98
#&gt; TCGA.XM.A8RI.01     1  0.0000      0.995 1.00  0 0.00 0.00
#&gt; TCGA.4V.A9QL.01     3  0.0000      1.000 0.00  0 1.00 0.00
#&gt; TCGA.X7.A8M0.01     3  0.0000      1.000 0.00  0 1.00 0.00
#&gt; TCGA.ZB.A96F.01     1  0.0000      0.995 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8D8.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.4V.A9QM.01     2  0.0000      1.000 0.00  1 0.00 0.00
#&gt; TCGA.5U.AB0E.01     1  0.0000      0.995 1.00  0 0.00 0.00
#&gt; TCGA.ZB.A96E.01     2  0.0000      1.000 0.00  1 0.00 0.00
</code></pre>

<script>
$('#tab-node-03-get-classes-3-a').parent().next().next().hide();
$('#tab-node-03-get-classes-3-a').click(function(){
  $('#tab-node-03-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-4'>
<p><a id='tab-node-03-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.ZB.A96K.01     2  0.0000      0.967 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XU.A930.01     5  0.2929      0.000 0.18 0.00 0.00 0.00 0.82
#&gt; TCGA.ZB.A96M.01     3  0.0000      0.989 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A96Q.01     2  0.1732      0.938 0.00 0.92 0.00 0.00 0.08
#&gt; TCGA.X7.A8D9.01     3  0.0000      0.989 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.5V.A9RR.01     2  0.0000      0.967 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A961.01     1  0.1410      0.904 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.XM.A8RC.01     1  0.2020      0.903 0.90 0.00 0.00 0.00 0.10
#&gt; TCGA.X7.A8M1.01     2  0.0000      0.967 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FD.01     4  0.0000      1.000 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.5K.AAAP.01     2  0.1410      0.948 0.00 0.94 0.00 0.00 0.06
#&gt; TCGA.XU.A92X.01     1  0.0000      0.938 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5G.A9ZZ.01     4  0.0000      1.000 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.3G.AB14.01     1  0.1043      0.930 0.96 0.00 0.00 0.00 0.04
#&gt; TCGA.YT.A95F.01     3  0.0000      0.989 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.4V.A9QR.01     4  0.0000      1.000 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.XM.A8RI.01     1  0.2020      0.903 0.90 0.00 0.00 0.00 0.10
#&gt; TCGA.4V.A9QL.01     3  0.0000      0.989 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.X7.A8M0.01     3  0.1043      0.954 0.00 0.00 0.96 0.04 0.00
#&gt; TCGA.ZB.A96F.01     1  0.0000      0.938 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8D8.01     2  0.0000      0.967 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QM.01     2  0.0000      0.967 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0E.01     1  0.0609      0.931 0.98 0.00 0.00 0.00 0.02
#&gt; TCGA.ZB.A96E.01     2  0.2280      0.911 0.00 0.88 0.00 0.00 0.12
</code></pre>

<script>
$('#tab-node-03-get-classes-4-a').parent().next().next().hide();
$('#tab-node-03-get-classes-4-a').click(function(){
  $('#tab-node-03-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-5'>
<p><a id='tab-node-03-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.ZB.A96K.01     2  0.1814      0.860 0.00 0.90 0.00 0.00 0.10 0.00
#&gt; TCGA.XU.A930.01     6  0.0937      0.000 0.04 0.00 0.00 0.00 0.00 0.96
#&gt; TCGA.ZB.A96M.01     3  0.0000      0.966 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96Q.01     2  0.2790      0.789 0.00 0.84 0.00 0.00 0.14 0.02
#&gt; TCGA.X7.A8D9.01     3  0.0000      0.966 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.5V.A9RR.01     2  0.2454      0.847 0.00 0.84 0.00 0.00 0.16 0.00
#&gt; TCGA.ZB.A961.01     1  0.4873      0.409 0.52 0.00 0.00 0.00 0.42 0.06
#&gt; TCGA.XM.A8RC.01     1  0.2728      0.803 0.86 0.00 0.00 0.00 0.10 0.04
#&gt; TCGA.X7.A8M1.01     2  0.0000      0.854 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4X.A9FD.01     4  0.0547      0.977 0.00 0.00 0.00 0.98 0.02 0.00
#&gt; TCGA.5K.AAAP.01     2  0.1556      0.831 0.00 0.92 0.00 0.00 0.08 0.00
#&gt; TCGA.XU.A92X.01     1  0.1807      0.843 0.92 0.00 0.00 0.00 0.06 0.02
#&gt; TCGA.5G.A9ZZ.01     4  0.0547      0.977 0.00 0.00 0.00 0.98 0.02 0.00
#&gt; TCGA.3G.AB14.01     1  0.1556      0.842 0.92 0.00 0.00 0.00 0.08 0.00
#&gt; TCGA.YT.A95F.01     3  0.0000      0.966 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QR.01     4  0.0000      0.983 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.XM.A8RI.01     1  0.2512      0.826 0.88 0.00 0.00 0.00 0.06 0.06
#&gt; TCGA.4V.A9QL.01     3  0.0000      0.966 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M0.01     3  0.2794      0.852 0.00 0.00 0.86 0.06 0.08 0.00
#&gt; TCGA.ZB.A96F.01     1  0.0937      0.850 0.96 0.00 0.00 0.00 0.04 0.00
#&gt; TCGA.X7.A8D8.01     2  0.2454      0.847 0.00 0.84 0.00 0.00 0.16 0.00
#&gt; TCGA.4V.A9QM.01     2  0.2260      0.853 0.00 0.86 0.00 0.00 0.14 0.00
#&gt; TCGA.5U.AB0E.01     1  0.1092      0.851 0.96 0.00 0.00 0.00 0.02 0.02
#&gt; TCGA.ZB.A96E.01     2  0.3679      0.722 0.00 0.76 0.00 0.00 0.20 0.04
</code></pre>

<script>
$('#tab-node-03-get-classes-5-a').parent().next().next().hide();
$('#tab-node-03-get-classes-5-a').click(function(){
  $('#tab-node-03-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-6'>
<p><a id='tab-node-03-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.ZB.A96K.01     2  0.0863     0.7733 0.00 0.96 0.00 0.00 0.00 0.00 0.04
#&gt; TCGA.XU.A930.01     6  0.0504     0.0000 0.02 0.00 0.00 0.00 0.00 0.98 0.00
#&gt; TCGA.ZB.A96M.01     3  0.0000     0.9126 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96Q.01     2  0.3496    -0.0681 0.00 0.58 0.00 0.00 0.00 0.00 0.42
#&gt; TCGA.X7.A8D9.01     3  0.0000     0.9126 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5V.A9RR.01     2  0.0504     0.7796 0.00 0.98 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.ZB.A961.01     5  0.3413     0.0000 0.38 0.00 0.00 0.00 0.62 0.00 0.00
#&gt; TCGA.XM.A8RC.01     1  0.4107     0.6165 0.70 0.00 0.00 0.00 0.24 0.02 0.04
#&gt; TCGA.X7.A8M1.01     2  0.0863     0.7714 0.00 0.96 0.00 0.00 0.00 0.00 0.04
#&gt; TCGA.4X.A9FD.01     4  0.0000     0.9818 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.5K.AAAP.01     2  0.3139     0.3934 0.00 0.70 0.00 0.00 0.00 0.00 0.30
#&gt; TCGA.XU.A92X.01     1  0.1671     0.6934 0.90 0.00 0.00 0.00 0.10 0.00 0.00
#&gt; TCGA.5G.A9ZZ.01     4  0.1006     0.9633 0.00 0.00 0.00 0.96 0.02 0.00 0.02
#&gt; TCGA.3G.AB14.01     1  0.2278     0.6982 0.88 0.00 0.00 0.00 0.08 0.00 0.04
#&gt; TCGA.YT.A95F.01     3  0.0000     0.9126 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QR.01     4  0.0000     0.9818 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RI.01     1  0.3863     0.6453 0.74 0.00 0.00 0.00 0.20 0.04 0.02
#&gt; TCGA.4V.A9QL.01     3  0.0000     0.9126 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M0.01     3  0.5507     0.5747 0.00 0.00 0.64 0.06 0.10 0.02 0.18
#&gt; TCGA.ZB.A96F.01     1  0.1006     0.7359 0.96 0.00 0.00 0.00 0.02 0.00 0.02
#&gt; TCGA.X7.A8D8.01     2  0.0863     0.7691 0.00 0.96 0.00 0.00 0.00 0.00 0.04
#&gt; TCGA.4V.A9QM.01     2  0.0504     0.7796 0.00 0.98 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.5U.AB0E.01     1  0.1006     0.7447 0.96 0.00 0.00 0.00 0.02 0.00 0.02
#&gt; TCGA.ZB.A96E.01     7  0.3517     0.0000 0.00 0.28 0.00 0.00 0.02 0.00 0.70
</code></pre>

<script>
$('#tab-node-03-get-classes-6-a').parent().next().next().hide();
$('#tab-node-03-get-classes-6-a').click(function(){
  $('#tab-node-03-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-7'>
<p><a id='tab-node-03-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7   p8
#&gt; TCGA.ZB.A96K.01     2  0.0941      0.740 0.00 0.96 0.00 0.00 0.00 0.00 0.02 0.02
#&gt; TCGA.XU.A930.01     6  0.0000      0.000 0.00 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.ZB.A96M.01     3  0.0000      1.000 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.ZB.A96Q.01     2  0.3318     -0.118 0.00 0.54 0.00 0.00 0.00 0.00 0.46 0.00
#&gt; TCGA.X7.A8D9.01     3  0.0000      1.000 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5V.A9RR.01     2  0.1887      0.699 0.00 0.90 0.00 0.00 0.00 0.00 0.06 0.04
#&gt; TCGA.ZB.A961.01     5  0.0471      0.000 0.02 0.00 0.00 0.00 0.98 0.00 0.00 0.00
#&gt; TCGA.XM.A8RC.01     1  0.5024      0.673 0.64 0.00 0.00 0.00 0.02 0.04 0.10 0.20
#&gt; TCGA.X7.A8M1.01     2  0.1765      0.698 0.00 0.88 0.00 0.00 0.00 0.00 0.12 0.00
#&gt; TCGA.4X.A9FD.01     4  0.1607      0.910 0.00 0.00 0.00 0.92 0.00 0.00 0.04 0.04
#&gt; TCGA.5K.AAAP.01     2  0.3291      0.469 0.00 0.70 0.00 0.00 0.00 0.00 0.28 0.02
#&gt; TCGA.XU.A92X.01     1  0.3054      0.763 0.80 0.00 0.00 0.00 0.12 0.00 0.00 0.08
#&gt; TCGA.5G.A9ZZ.01     4  0.1091      0.918 0.00 0.00 0.00 0.94 0.00 0.00 0.00 0.06
#&gt; TCGA.3G.AB14.01     1  0.2591      0.786 0.86 0.00 0.00 0.00 0.02 0.00 0.08 0.04
#&gt; TCGA.YT.A95F.01     3  0.0000      1.000 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.4V.A9QR.01     4  0.0000      0.935 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.XM.A8RI.01     1  0.4202      0.748 0.74 0.00 0.00 0.00 0.02 0.04 0.06 0.14
#&gt; TCGA.4V.A9QL.01     3  0.0000      1.000 0.00 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.X7.A8M0.01     8  0.3618      0.000 0.00 0.00 0.38 0.02 0.00 0.00 0.00 0.60
#&gt; TCGA.ZB.A96F.01     1  0.1741      0.793 0.92 0.00 0.00 0.00 0.02 0.00 0.04 0.02
#&gt; TCGA.X7.A8D8.01     2  0.1557      0.713 0.00 0.92 0.00 0.00 0.00 0.00 0.06 0.02
#&gt; TCGA.4V.A9QM.01     2  0.0000      0.741 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.5U.AB0E.01     1  0.1804      0.783 0.90 0.00 0.00 0.00 0.08 0.02 0.00 0.00
#&gt; TCGA.ZB.A96E.01     7  0.3404      0.000 0.00 0.24 0.00 0.00 0.00 0.00 0.72 0.04
</code></pre>

<script>
$('#tab-node-03-get-classes-7-a').parent().next().next().hide();
$('#tab-node-03-get-classes-7-a').click(function(){
  $('#tab-node-03-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-03-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-03-consensus-heatmap'>
<ul>
<li><a href='#tab-node-03-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-03-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-03-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-03-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-03-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-03-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-03-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-03-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-03-membership-heatmap'>
<ul>
<li><a href='#tab-node-03-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-03-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-03-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-03-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-03-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-03-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-03-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-1-1.png" alt="plot of chunk tab-node-03-membership-heatmap-1"/></p>

</div>
<div id='tab-node-03-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-2-1.png" alt="plot of chunk tab-node-03-membership-heatmap-2"/></p>

</div>
<div id='tab-node-03-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-3-1.png" alt="plot of chunk tab-node-03-membership-heatmap-3"/></p>

</div>
<div id='tab-node-03-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-4-1.png" alt="plot of chunk tab-node-03-membership-heatmap-4"/></p>

</div>
<div id='tab-node-03-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-5-1.png" alt="plot of chunk tab-node-03-membership-heatmap-5"/></p>

</div>
<div id='tab-node-03-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-6-1.png" alt="plot of chunk tab-node-03-membership-heatmap-6"/></p>

</div>
<div id='tab-node-03-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-7-1.png" alt="plot of chunk tab-node-03-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-03-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-03-get-signatures'>
<ul>
<li><a href='#tab-node-03-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-03-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-03-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-03-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-03-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-03-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-03-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-1-1.png" alt="plot of chunk tab-node-03-get-signatures-1"/></p>

</div>
<div id='tab-node-03-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-2-1.png" alt="plot of chunk tab-node-03-get-signatures-2"/></p>

</div>
<div id='tab-node-03-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-3-1.png" alt="plot of chunk tab-node-03-get-signatures-3"/></p>

</div>
<div id='tab-node-03-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-4-1.png" alt="plot of chunk tab-node-03-get-signatures-4"/></p>

</div>
<div id='tab-node-03-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-5-1.png" alt="plot of chunk tab-node-03-get-signatures-5"/></p>

</div>
<div id='tab-node-03-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-6-1.png" alt="plot of chunk tab-node-03-get-signatures-6"/></p>

</div>
<div id='tab-node-03-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-7-1.png" alt="plot of chunk tab-node-03-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-03-signature_compare](figure_cola/node-03-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-03-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-03-dimension-reduction'>
<ul>
<li><a href='#tab-node-03-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-03-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-03-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-03-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-03-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-03-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-03-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-1-1.png" alt="plot of chunk tab-node-03-dimension-reduction-1"/></p>

</div>
<div id='tab-node-03-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-2-1.png" alt="plot of chunk tab-node-03-dimension-reduction-2"/></p>

</div>
<div id='tab-node-03-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-3-1.png" alt="plot of chunk tab-node-03-dimension-reduction-3"/></p>

</div>
<div id='tab-node-03-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-4-1.png" alt="plot of chunk tab-node-03-dimension-reduction-4"/></p>

</div>
<div id='tab-node-03-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-5-1.png" alt="plot of chunk tab-node-03-dimension-reduction-5"/></p>

</div>
<div id='tab-node-03-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-6-1.png" alt="plot of chunk tab-node-03-dimension-reduction-6"/></p>

</div>
<div id='tab-node-03-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-7-1.png" alt="plot of chunk tab-node-03-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-03-collect-classes](figure_cola/node-03-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node04


Parent node: [Node0](#Node0).
Child nodes: 
                Node011-leaf
        ,
                [Node012](#Node012)
        ,
                Node021-leaf
        ,
                Node022-leaf
        ,
                Node023-leaf
        ,
                Node024-leaf
        ,
                Node031-leaf
        ,
                Node032-leaf
        ,
                Node033-leaf
        ,
                Node034-leaf
        ,
                Node041-leaf
        ,
                Node042-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["04"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 14 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 7.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-04-collect-plots](figure_cola/node-04-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-04-select-partition-number](figure_cola/node-04-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.5389 0.462   0.462
#> 3 3 1.000           0.929       1.000         0.1222 0.934   0.857
#> 4 4 1.000           0.920       0.997         0.1787 0.890   0.722
#> 5 5 0.901           0.749       0.966         0.0338 0.989   0.962
#> 6 6 0.945           0.753       0.989         0.0977 0.912   0.680
#> 7 7 0.901           0.723       0.973         0.0788 0.934   0.647
#> 8 8 0.912           0.528       0.950         0.0291 0.989   0.909
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 7
#> attr(,"optional")
#> [1] 2 4 6
```

There is also optional best $k$ = 2 4 6 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-04-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-04-get-classes'>
<ul>
<li><a href='#tab-node-04-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-04-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-04-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-04-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-04-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-04-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-04-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-04-get-classes-1'>
<p><a id='tab-node-04-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.3S.A8YW.01     1       0          1  1  0
#&gt; TCGA.4V.A9QN.01     2       0          1  0  1
#&gt; TCGA.XU.A936.01     1       0          1  1  0
#&gt; TCGA.XU.A931.01     2       0          1  0  1
#&gt; TCGA.XU.A92Z.01     2       0          1  0  1
#&gt; TCGA.5U.AB0D.01     1       0          1  1  0
#&gt; TCGA.ZB.A96V.01     1       0          1  1  0
#&gt; TCGA.ZB.A96I.01     2       0          1  0  1
#&gt; TCGA.X7.A8M5.01     2       0          1  0  1
#&gt; TCGA.ZB.A966.01     1       0          1  1  0
#&gt; TCGA.XU.A92V.01     2       0          1  0  1
#&gt; TCGA.XU.A933.01     1       0          1  1  0
#&gt; TCGA.ZC.AAA7.01     1       0          1  1  0
#&gt; TCGA.X7.A8M3.01     2       0          1  0  1
</code></pre>

<script>
$('#tab-node-04-get-classes-1-a').parent().next().next().hide();
$('#tab-node-04-get-classes-1-a').click(function(){
  $('#tab-node-04-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-04-get-classes-2'>
<p><a id='tab-node-04-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2 p3
#&gt; TCGA.3S.A8YW.01     1       0          1  1  0  0
#&gt; TCGA.4V.A9QN.01     2       0          1  0  1  0
#&gt; TCGA.XU.A936.01     1       0          1  1  0  0
#&gt; TCGA.XU.A931.01     2       0          1  0  1  0
#&gt; TCGA.XU.A92Z.01     3       0          0  0  0  1
#&gt; TCGA.5U.AB0D.01     1       0          1  1  0  0
#&gt; TCGA.ZB.A96V.01     1       0          1  1  0  0
#&gt; TCGA.ZB.A96I.01     2       0          1  0  1  0
#&gt; TCGA.X7.A8M5.01     2       0          1  0  1  0
#&gt; TCGA.ZB.A966.01     1       0          1  1  0  0
#&gt; TCGA.XU.A92V.01     2       0          1  0  1  0
#&gt; TCGA.XU.A933.01     1       0          1  1  0  0
#&gt; TCGA.ZC.AAA7.01     1       0          1  1  0  0
#&gt; TCGA.X7.A8M3.01     2       0          1  0  1  0
</code></pre>

<script>
$('#tab-node-04-get-classes-2-a').parent().next().next().hide();
$('#tab-node-04-get-classes-2-a').click(function(){
  $('#tab-node-04-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-04-get-classes-3'>
<p><a id='tab-node-04-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2 p3   p4
#&gt; TCGA.3S.A8YW.01     1   0.000      1.000 1.00  0  0 0.00
#&gt; TCGA.4V.A9QN.01     2   0.000      1.000 0.00  1  0 0.00
#&gt; TCGA.XU.A936.01     4   0.121      0.938 0.04  0  0 0.96
#&gt; TCGA.XU.A931.01     2   0.000      1.000 0.00  1  0 0.00
#&gt; TCGA.XU.A92Z.01     3   0.000      0.000 0.00  0  1 0.00
#&gt; TCGA.5U.AB0D.01     1   0.000      1.000 1.00  0  0 0.00
#&gt; TCGA.ZB.A96V.01     1   0.000      1.000 1.00  0  0 0.00
#&gt; TCGA.ZB.A96I.01     2   0.000      1.000 0.00  1  0 0.00
#&gt; TCGA.X7.A8M5.01     2   0.000      1.000 0.00  1  0 0.00
#&gt; TCGA.ZB.A966.01     4   0.000      0.938 0.00  0  0 1.00
#&gt; TCGA.XU.A92V.01     2   0.000      1.000 0.00  1  0 0.00
#&gt; TCGA.XU.A933.01     1   0.000      1.000 1.00  0  0 0.00
#&gt; TCGA.ZC.AAA7.01     1   0.000      1.000 1.00  0  0 0.00
#&gt; TCGA.X7.A8M3.01     2   0.000      1.000 0.00  1  0 0.00
</code></pre>

<script>
$('#tab-node-04-get-classes-3-a').parent().next().next().hide();
$('#tab-node-04-get-classes-3-a').click(function(){
  $('#tab-node-04-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-04-get-classes-4'>
<p><a id='tab-node-04-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2 p3   p4   p5
#&gt; TCGA.3S.A8YW.01     1  0.0000      1.000 1.00 0.00  0 0.00 0.00
#&gt; TCGA.4V.A9QN.01     2  0.0000      0.938 0.00 1.00  0 0.00 0.00
#&gt; TCGA.XU.A936.01     4  0.0609      0.000 0.02 0.00  0 0.98 0.00
#&gt; TCGA.XU.A931.01     2  0.0000      0.938 0.00 1.00  0 0.00 0.00
#&gt; TCGA.XU.A92Z.01     3  0.0000      0.000 0.00 0.00  1 0.00 0.00
#&gt; TCGA.5U.AB0D.01     1  0.0000      1.000 1.00 0.00  0 0.00 0.00
#&gt; TCGA.ZB.A96V.01     1  0.0000      1.000 1.00 0.00  0 0.00 0.00
#&gt; TCGA.ZB.A96I.01     2  0.0000      0.938 0.00 1.00  0 0.00 0.00
#&gt; TCGA.X7.A8M5.01     2  0.3106      0.870 0.00 0.84  0 0.02 0.14
#&gt; TCGA.ZB.A966.01     5  0.2516      0.000 0.00 0.00  0 0.14 0.86
#&gt; TCGA.XU.A92V.01     2  0.3106      0.870 0.00 0.84  0 0.02 0.14
#&gt; TCGA.XU.A933.01     1  0.0000      1.000 1.00 0.00  0 0.00 0.00
#&gt; TCGA.ZC.AAA7.01     1  0.0000      1.000 1.00 0.00  0 0.00 0.00
#&gt; TCGA.X7.A8M3.01     2  0.0000      0.938 0.00 1.00  0 0.00 0.00
</code></pre>

<script>
$('#tab-node-04-get-classes-4-a').parent().next().next().hide();
$('#tab-node-04-get-classes-4-a').click(function(){
  $('#tab-node-04-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-04-get-classes-5'>
<p><a id='tab-node-04-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1   p2 p3 p4 p5   p6
#&gt; TCGA.3S.A8YW.01     1  0.0000      1.000  1 0.00  0  0  0 0.00
#&gt; TCGA.4V.A9QN.01     2  0.0000      0.993  0 1.00  0  0  0 0.00
#&gt; TCGA.XU.A936.01     4  0.0000      0.000  0 0.00  0  1  0 0.00
#&gt; TCGA.XU.A931.01     2  0.0000      0.993  0 1.00  0  0  0 0.00
#&gt; TCGA.XU.A92Z.01     3  0.0000      0.000  0 0.00  1  0  0 0.00
#&gt; TCGA.5U.AB0D.01     1  0.0000      1.000  1 0.00  0  0  0 0.00
#&gt; TCGA.ZB.A96V.01     1  0.0000      1.000  1 0.00  0  0  0 0.00
#&gt; TCGA.ZB.A96I.01     2  0.0547      0.978  0 0.98  0  0  0 0.02
#&gt; TCGA.X7.A8M5.01     6  0.0000      0.793  0 0.00  0  0  0 1.00
#&gt; TCGA.ZB.A966.01     5  0.0000      0.000  0 0.00  0  0  1 0.00
#&gt; TCGA.XU.A92V.01     6  0.2260      0.796  0 0.14  0  0  0 0.86
#&gt; TCGA.XU.A933.01     1  0.0000      1.000  1 0.00  0  0  0 0.00
#&gt; TCGA.ZC.AAA7.01     1  0.0000      1.000  1 0.00  0  0  0 0.00
#&gt; TCGA.X7.A8M3.01     2  0.0000      0.993  0 1.00  0  0  0 0.00
</code></pre>

<script>
$('#tab-node-04-get-classes-5-a').parent().next().next().hide();
$('#tab-node-04-get-classes-5-a').click(function(){
  $('#tab-node-04-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-04-get-classes-6'>
<p><a id='tab-node-04-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2 p3 p4 p5   p6   p7
#&gt; TCGA.3S.A8YW.01     1  0.0000      1.000 1.00 0.00  0  0  0 0.00 0.00
#&gt; TCGA.4V.A9QN.01     2  0.0000      0.970 0.00 1.00  0  0  0 0.00 0.00
#&gt; TCGA.XU.A936.01     4  0.0000      0.000 0.00 0.00  0  1  0 0.00 0.00
#&gt; TCGA.XU.A931.01     2  0.0000      0.970 0.00 1.00  0  0  0 0.00 0.00
#&gt; TCGA.XU.A92Z.01     3  0.0000      0.000 0.00 0.00  1  0  0 0.00 0.00
#&gt; TCGA.5U.AB0D.01     1  0.0000      1.000 1.00 0.00  0  0  0 0.00 0.00
#&gt; TCGA.ZB.A96V.01     7  0.0504      0.811 0.02 0.00  0  0  0 0.00 0.98
#&gt; TCGA.ZB.A96I.01     2  0.1433      0.906 0.00 0.92  0  0  0 0.08 0.00
#&gt; TCGA.X7.A8M5.01     6  0.0000      0.843 0.00 0.00  0  0  0 1.00 0.00
#&gt; TCGA.ZB.A966.01     5  0.0000      0.000 0.00 0.00  0  0  1 0.00 0.00
#&gt; TCGA.XU.A92V.01     6  0.2163      0.844 0.00 0.10  0  0  0 0.88 0.02
#&gt; TCGA.XU.A933.01     1  0.0000      1.000 1.00 0.00  0  0  0 0.00 0.00
#&gt; TCGA.ZC.AAA7.01     7  0.2259      0.813 0.16 0.00  0  0  0 0.00 0.84
#&gt; TCGA.X7.A8M3.01     2  0.0000      0.970 0.00 1.00  0  0  0 0.00 0.00
</code></pre>

<script>
$('#tab-node-04-get-classes-6-a').parent().next().next().hide();
$('#tab-node-04-get-classes-6-a').click(function(){
  $('#tab-node-04-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-04-get-classes-7'>
<p><a id='tab-node-04-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2 p3 p4 p5   p6   p7   p8
#&gt; TCGA.3S.A8YW.01     1   0.000      1.000 1.00 0.00  0  0  0 0.00 0.00 0.00
#&gt; TCGA.4V.A9QN.01     2   0.000      0.818 0.00 1.00  0  0  0 0.00 0.00 0.00
#&gt; TCGA.XU.A936.01     4   0.000      0.000 0.00 0.00  0  1  0 0.00 0.00 0.00
#&gt; TCGA.XU.A931.01     2   0.109      0.805 0.00 0.94  0  0  0 0.00 0.00 0.06
#&gt; TCGA.XU.A92Z.01     3   0.000      0.000 0.00 0.00  1  0  0 0.00 0.00 0.00
#&gt; TCGA.5U.AB0D.01     1   0.000      1.000 1.00 0.00  0  0  0 0.00 0.00 0.00
#&gt; TCGA.ZB.A96V.01     7   0.000      0.839 0.00 0.00  0  0  0 0.00 1.00 0.00
#&gt; TCGA.ZB.A96I.01     2   0.332      0.273 0.00 0.54  0  0  0 0.00 0.00 0.46
#&gt; TCGA.X7.A8M5.01     6   0.000      0.000 0.00 0.00  0  0  0 1.00 0.00 0.00
#&gt; TCGA.ZB.A966.01     5   0.000      0.000 0.00 0.00  0  0  1 0.00 0.00 0.00
#&gt; TCGA.XU.A92V.01     8   0.109      0.000 0.00 0.00  0  0  0 0.06 0.00 0.94
#&gt; TCGA.XU.A933.01     1   0.000      1.000 1.00 0.00  0  0  0 0.00 0.00 0.00
#&gt; TCGA.ZC.AAA7.01     7   0.176      0.840 0.12 0.00  0  0  0 0.00 0.88 0.00
#&gt; TCGA.X7.A8M3.01     2   0.000      0.818 0.00 1.00  0  0  0 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-04-get-classes-7-a').parent().next().next().hide();
$('#tab-node-04-get-classes-7-a').click(function(){
  $('#tab-node-04-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-04-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-04-consensus-heatmap'>
<ul>
<li><a href='#tab-node-04-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-04-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-04-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-04-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-04-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-04-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-04-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-04-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-04-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-04-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-04-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-04-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-04-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-04-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-04-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-04-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-04-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-04-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-04-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-04-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-04-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-04-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-04-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-04-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-04-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-04-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-04-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-04-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-04-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-04-membership-heatmap'>
<ul>
<li><a href='#tab-node-04-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-04-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-04-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-04-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-04-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-04-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-04-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-04-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-04-membership-heatmap-1-1.png" alt="plot of chunk tab-node-04-membership-heatmap-1"/></p>

</div>
<div id='tab-node-04-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-04-membership-heatmap-2-1.png" alt="plot of chunk tab-node-04-membership-heatmap-2"/></p>

</div>
<div id='tab-node-04-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-04-membership-heatmap-3-1.png" alt="plot of chunk tab-node-04-membership-heatmap-3"/></p>

</div>
<div id='tab-node-04-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-04-membership-heatmap-4-1.png" alt="plot of chunk tab-node-04-membership-heatmap-4"/></p>

</div>
<div id='tab-node-04-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-04-membership-heatmap-5-1.png" alt="plot of chunk tab-node-04-membership-heatmap-5"/></p>

</div>
<div id='tab-node-04-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-04-membership-heatmap-6-1.png" alt="plot of chunk tab-node-04-membership-heatmap-6"/></p>

</div>
<div id='tab-node-04-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-04-membership-heatmap-7-1.png" alt="plot of chunk tab-node-04-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-04-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-04-get-signatures'>
<ul>
<li><a href='#tab-node-04-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-04-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-04-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-04-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-04-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-04-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-04-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-04-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-04-get-signatures-1-1.png" alt="plot of chunk tab-node-04-get-signatures-1"/></p>

</div>
<div id='tab-node-04-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-04-get-signatures-2-1.png" alt="plot of chunk tab-node-04-get-signatures-2"/></p>

</div>
<div id='tab-node-04-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-04-get-signatures-3-1.png" alt="plot of chunk tab-node-04-get-signatures-3"/></p>

</div>
<div id='tab-node-04-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-04-get-signatures-4-1.png" alt="plot of chunk tab-node-04-get-signatures-4"/></p>

</div>
<div id='tab-node-04-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-04-get-signatures-5-1.png" alt="plot of chunk tab-node-04-get-signatures-5"/></p>

</div>
<div id='tab-node-04-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-04-get-signatures-6-1.png" alt="plot of chunk tab-node-04-get-signatures-6"/></p>

</div>
<div id='tab-node-04-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-04-get-signatures-7-1.png" alt="plot of chunk tab-node-04-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-04-signature_compare](figure_cola/node-04-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-04-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-04-dimension-reduction'>
<ul>
<li><a href='#tab-node-04-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-04-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-04-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-04-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-04-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-04-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-04-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-04-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-04-dimension-reduction-1-1.png" alt="plot of chunk tab-node-04-dimension-reduction-1"/></p>

</div>
<div id='tab-node-04-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-04-dimension-reduction-2-1.png" alt="plot of chunk tab-node-04-dimension-reduction-2"/></p>

</div>
<div id='tab-node-04-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-04-dimension-reduction-3-1.png" alt="plot of chunk tab-node-04-dimension-reduction-3"/></p>

</div>
<div id='tab-node-04-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-04-dimension-reduction-4-1.png" alt="plot of chunk tab-node-04-dimension-reduction-4"/></p>

</div>
<div id='tab-node-04-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-04-dimension-reduction-5-1.png" alt="plot of chunk tab-node-04-dimension-reduction-5"/></p>

</div>
<div id='tab-node-04-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-04-dimension-reduction-6-1.png" alt="plot of chunk tab-node-04-dimension-reduction-6"/></p>

</div>
<div id='tab-node-04-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-04-dimension-reduction-7-1.png" alt="plot of chunk tab-node-04-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-04-collect-classes](figure_cola/node-04-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

## Session info


```r
sessionInfo()
```

```
#> R version 4.1.0 (2021-05-18)
#> Platform: x86_64-pc-linux-gnu (64-bit)
#> Running under: CentOS Linux 7 (Core)
#> 
#> Matrix products: default
#> BLAS/LAPACK: /usr/lib64/libopenblas-r0.3.3.so
#> 
#> locale:
#>  [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C               LC_TIME=en_US.UTF-8       
#>  [4] LC_COLLATE=en_US.UTF-8     LC_MONETARY=en_US.UTF-8    LC_MESSAGES=en_US.UTF-8   
#>  [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                  LC_ADDRESS=C              
#> [10] LC_TELEPHONE=C             LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       
#> 
#> attached base packages:
#> [1] grid      stats     graphics  grDevices utils     datasets  methods   base     
#> 
#> other attached packages:
#> [1] genefilter_1.74.0    ComplexHeatmap_2.8.0 markdown_1.1         knitr_1.33          
#> [5] matrixStats_0.59.0   cola_1.9.4          
#> 
#> loaded via a namespace (and not attached):
#>   [1] bitops_1.0-7           bit64_4.0.5            doParallel_1.0.16      RColorBrewer_1.1-2    
#>   [5] httr_1.4.2             GenomeInfoDb_1.28.1    data.tree_1.0.0        tools_4.1.0           
#>   [9] utf8_1.2.1             R6_2.5.0               irlba_2.3.3            DBI_1.1.1             
#>  [13] BiocGenerics_0.38.0    colorspace_2.0-2       GetoptLong_1.0.5       gridExtra_2.3         
#>  [17] tidyselect_1.1.1       bit_4.0.4              compiler_4.1.0         Biobase_2.52.0        
#>  [21] Cairo_1.5-12.2         xml2_1.3.2             microbenchmark_1.4-7   slam_0.1-48           
#>  [25] scales_1.1.1           askpass_1.1            stringr_1.4.0          digest_0.6.27         
#>  [29] XVector_0.32.0         pkgconfig_2.0.3        umap_0.2.7.0           fastmap_1.1.0         
#>  [33] highr_0.9              rlang_0.4.11           GlobalOptions_0.1.2    rstudioapi_0.13       
#>  [37] RSQLite_2.2.7          impute_1.66.0          generics_0.1.0         shape_1.4.6           
#>  [41] jsonlite_1.7.2         mclust_5.4.7           dplyr_1.0.7            dendextend_1.15.1     
#>  [45] RCurl_1.98-1.3         magrittr_2.0.1         GenomeInfoDbData_1.2.6 Matrix_1.3-4          
#>  [49] fansi_0.5.0            Rcpp_1.0.7             munsell_0.5.0          S4Vectors_0.30.0      
#>  [53] viridis_0.6.1          reticulate_1.20        lifecycle_1.0.0        scatterplot3d_0.3-41  
#>  [57] stringi_1.7.3          zlibbioc_1.38.0        blob_1.2.1             parallel_4.1.0        
#>  [61] crayon_1.4.1           lattice_0.20-44        Biostrings_2.60.1      splines_4.1.0         
#>  [65] annotate_1.70.0        circlize_0.4.13        KEGGREST_1.32.0        polylabelr_0.2.0      
#>  [69] pillar_1.6.1           rjson_0.2.20           codetools_0.2-18       stats4_4.1.0          
#>  [73] XML_3.99-0.6           glue_1.4.2             evaluate_0.14          png_0.1-7             
#>  [77] vctrs_0.3.8            foreach_1.5.1          polyclip_1.10-0        purrr_0.3.4           
#>  [81] gtable_0.3.0           openssl_1.4.4          assertthat_0.2.1       clue_0.3-59           
#>  [85] cachem_1.0.5           ggplot2_3.3.5          xfun_0.24              eulerr_6.1.0          
#>  [89] xtable_1.8-4           skmeans_0.2-13         RSpectra_0.16-0        viridisLite_0.4.0     
#>  [93] survival_3.2-11        tibble_3.1.2           Polychrome_1.3.1       iterators_1.0.13      
#>  [97] AnnotationDbi_1.54.1   memoise_2.0.0          IRanges_2.26.0         cluster_2.1.2         
#> [101] ellipsis_0.3.2         brew_1.0-6
```




