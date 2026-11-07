# Who drives the debate in the House of Commons?

Graph analytics project (Albert School, 2026).

Every MP is a node, and there is an edge A -> B when B speaks right after A in the same debate. The weight is the number of times it happens. There is one graph per Prime Minister: Sunak, Starmer and Burnham (Jan 2023 to Nov 2026).

## Data

- Debate transcripts from TheyWorkForYou (mySociety): https://www.theyworkforyou.com/pwdata/scrapedxml/debates/
- MP parties from mySociety's member list: https://github.com/mysociety/parlparse/blob/master/members/people.json

The raw files are not in the repo (about 450 MB). The first notebook downloads them into `data/raw/` and rebuilds everything. The processed graph tables, `data/nodes.csv` and `data/edges.csv`, are included.

## Running it

```
pip install pandas networkx matplotlib scipy
```

Then run the notebooks in order:

1. `01_build_graph_tables` downloads the files, cleans them and builds the nodes and edges
2. `02_graph_structure` connectivity, diameter, radius
3. `03_centrality` degree, PageRank, betweenness, by MP and by party
4. `04_communities` Louvain and label propagation

Tables and figures are saved in `results/`. The first run takes a while because of the download.
