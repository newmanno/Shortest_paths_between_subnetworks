# TopNet: A network topology analysis program written using NetworkX
> This script will take as input two subnetworks, then calculate all shortest paths between each pair of nodes in the two subnetworks. Output is a comma separated list of source and target nodes, along with their pathlength. For each pair of nodes, there can be multiple shortest paths. Each of these can be retained if specified by the user.


## Table of contents
* [General info](#general-info)
* [Dependencies](#dependencies)
* [Importing the network](#importing-the-network)
* [Calculating topological properties](#calculating-topological-properties)

## General info
* Author: [Nolan K Newman](http://blogs.oregonstate.edu/morgunshulzhenkolabs/members/nolan-newman/) - newmanno@oregonstate.edu
* Date: 8/2/2020
* Created with Python v3.5.1

## Dependencies
* NetworkX (v2.2)
* pickle (v4.0)
* Numpy (v1.16.4

## Importing the network
Purpose: This script takes a pickled network file and a mapping file that has the node names in the first column and the node type in the second column (see example below). It outputs the shortest path distance between each node of the node types indicated in the command.

Arguments:
> **Required**
> * Pickled network file, created with import_network_data.py; positional argument
> * --node_map	-	mapping file indicating the type of each node
> * --node_type1	-	The first group of nodes (indicated in the second column of the mapping file)
> * --node_type1	-	The second group of nodes (indicated in the second column of the mapping file)

> **Optional**
> * This code does not currently accept any optional arguments
	
Example input command:
* python find_all_shortest_paths_bw_subnets.py <pickled network file> --node_map <mapping file> --node_type1 gene --node_type2 micro
	
Example node mapping file (only required if BiBC is being calculated based on pre-defined groups (i.e. genes and microbiota). The input is a **CSV** file with **no header**, in the following format:
> GAPDH,gene\
> EGFR,gene\
> TP53,gene\
> ASV1,micro\
> ASV2,micro\
> ASV5,micro
	
Outputs:
* CSV file with the following rows:
> GAPDH,ASV1,2,1
> GAPDH,ASV2,5,2
> GAPDH,ASV5,3,1
> etc. for each pair of nodes belonging to different groups (i.e. gene-gene and micro-micro paths are not calculated)
