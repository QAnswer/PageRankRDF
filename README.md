# PageRankRDF

This repository contains a command line tool to compute PageRank scores over RDF graphs. Applying the PageRank algorithm to RDF graphs is not difficult, but doing it in a memory efficient and scalable way is not easy.

## Usage

The usage is very simple. Compile the project:

    mvn clean package
    
The command line tool is then available:

     java -jar target/pagerank-0.1.0.jar
     
It currently supports two computation methods. The first can be used to compute PageRank scores over RDF files in common serilizations like nt or Turtle. An example usage would be:

    java -jar pagerank.jar -in input.ttl -out output.nt
    
**NOTE**: This method is **NOT** memory efficient. You will need a **BIG** machine to run this script (depending on the size of your data)

The second method takes as input a RDF file in hdt format (http://www.rdfhdt.org). Hdt is a compressed format to store RDF. An example usage would be:

    java -jar pagerank.jar -in input.hdt -out output.nt
    
The scores can be stored either by default in nt format using the vRank vocabulary. Also a tsv file can be generated.

The full list of options is:

    Usage: java -jar pagerank.jar -in file -out pagerank [options]
    Options:
      --damping, -D
        specifying the damping factor for the PageRank computation
        Default: 0.85
      --format, -f
        specify the output format for the PageRank scores, either "tsv" or "nt"
        Default: nt
      --help
        displays the list of possible parameters
    * --input, -in
        specify a file in some RDF format or in HDT
      --iteration, -I
        specifying the number are performed by PageRank
        Default: 40
    * --output, -out
        specify the file where the pagerank scores are stored
      --start-value, -S
        specifying the start value for the PageRank computation
        Default: 0.1
 
 ## Citation
 If you find this work useful, please provide the following reference:
 
 ```
     @InProceedings{diefenbach_thalhammer,
            author="Diefenbach, Dennis and Thalhammer, Andreas",
            title={{PageRank and Generic Entity Summarization for RDF Knowledge Bases}},
            booktitle="The Semantic Web",
            year="2018",
            publisher="Springer International Publishing",
            address="Cham",
            pages="145--160",
            doi={10.1007/978-3-319-93417-4_10},
            isbn="978-3-319-93417-4"
    }
 ```
 
 ## Already computed datasets
 
 The PageRank scores of some popular RDF datasets can be found [HERE](https://figshare.com/projects/PageRank_scores_of_some_RDF_graphs/28119)

 ## Acknloweldgements
 We would like to thank @cbobed for his contributions!
