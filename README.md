# Market-Basket Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alessandro-macchi/algorithms_for_massive_data/blob/master/project.ipynb)

## Author
**Alessandro Macchi** - github.com/alessandro-macchi

## Overview
This project performs a Market-Basket Analysis to discover frequent actor collaborations within the IMDB Top 1000 movies dataset. By extracting the mos famous actors for each film, it treats each movie as a "basket" to identify pairs of actors who frequently appear together on screen.

The project implements, compares, and verifies the consistency of three fundamental massive-data algorithms:
* **A-priori:** A standard two-pass algorithm that leverages the monotonicity property to filter candidate pairs.
* **PCY (Park-Chen-Yu):** Improves A-priori by utilizing hash-based bitmaps during the first pass to significantly reduce the candidate pair space.
* **SON (Savasere-Omiecinski-Navathe):** Implemented with Spark, it uses parallelization to process data in manageable chunks.

## Performance Results
Because this dataset is relatively small, the classic a-priori algorithm proved to be the fastest in execution. The computational overhead of creating hash tables for PCY and chunking the dataset for SON makes them slower in this specific context. However, these advanced techniques remain structurally necessary and highly effective when scaling to truly massive datasets.

## Key Findings
Using a strict support threshold of 3, the algorithms successfully identified 25 frequent actor pairs out of thousands of possible combinations. They fall into two distinct categories:
* **Legendary Duos:** Al Pacino & Robert De Niro, Robert De Niro & Joe Pesci, ...
* **Franchise Stars:** Emma Watson & Rupert Grint, Mark Hamill & Harrison Ford, and Robert Downey Jr. & Chris Evans, ...
