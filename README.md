# Overview
This repository contains the source code for the paper "CommDP: Prefix-Tree Based Commuting Trajectory Synthesis with Differential Privacy".
### Description of paper
CommDP, a DP–based residential commuting trajectory synthesis framework built on a prefix tree structure. At the trajectory point level, CommDP employs adaptive temporal discretization to mitigate the sparsity caused by fixed time windows and ensures that all temporal structures are processed within the DP mechanism, thereby maintaining strict privacy protection even with finer-grained discretization. At the trajectory sequence level, CommDP constructs a commuting-feature prefix tree and introduces a hierarchical, pattern-frequency dependent privacy budget allocation strategy to preserve common commuting behaviors while adequately protecting rare patterns. Experiments based on Shenzhen public transport smart card data demonstrate that CommDP significantly outperforms existing mainstream privacy-preserving methods in retaining key commuting characteristics, achieving high data utility while providing strong privacy guarantees.
# Getting Started
The raw data format is as follows:

Fields are comma-separated with the following notation: O for Origin, D for Destination, H for Home, and W for Workplace.
```id,Odate,Ostation,Olon,Olat,Ddate,Dstation,Dlon,Dlat,trans,Hlat,Hlon,Wlat,Wlon```

The raw data preprocessing code is available in ```src/RCDPjour/Pre/CommuterDataExtractor.scala```.
This process concatenates user records with the same ID, filters out round-trip commuting data, and performs adaptive temporal generalization along with traffic zone spatial generalization.

preprocessed data format is as follows：
```Otimestamp Hregion,Dtimestamp Wregion,workhours,differenceOfCommuteDuration```

The data generation code is available in ``` src/RCDPjour/generator/Main_CommDP.java ```.

The evaluation code is available in ```src/RCDPjour/evaluation```
# Evaluating benchmarks

there are two open-source benchmarks available, which are:

-Privtrace: The code repository is available at [Privtrace GitHub repository](https://github.com/DpTrace/PrivTrace).

-ActSTD: The code repository is available at [ActSTD GitHub repository](https://github.com/tsinghua-fib-lab/Activity-Trajectory-Generation).
