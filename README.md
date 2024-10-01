# JavaScript CSV Benchmarks

Benchmarks of popular CSV parsers and formatters:

<!-- packages -->
| Package | Version | Published | Parse | Format 
|---------|---------|-----------|-------|--------
| [csv-parse](https://www.npmjs.com/package/csv-parse) | 5.5.6 | 5 months ago | Yes |  
| [csv-parser](https://www.npmjs.com/package/csv-parser) | 3.0.0 | 4 years ago | Yes |  
| [csv-rex](https://www.npmjs.com/package/csv-rex) | 0.7.0 | 1 year ago | Yes | Yes 
| [csv-streamify](https://www.npmjs.com/package/csv-streamify) | 4.0.0 | 7 years ago | Yes |  
| [csv-stringify](https://www.npmjs.com/package/csv-stringify) | 6.5.1 | 2 months ago |  | Yes 
| [csvtojson](https://www.npmjs.com/package/csvtojson) | 2.0.10 | 5 years ago | Yes |  
| [fast-csv](https://www.npmjs.com/package/fast-csv) | 5.0.1 | 8 months ago | Yes | Yes 
| [papaparse](https://www.npmjs.com/package/papaparse) | 5.4.1 | 2 years ago | Yes |  
<!-- packages -->

Your preferred CSV package missing? PRs welcome. Excluded packages in `/docs/EXCLUDED.md`.

## Tests
The tests run on generated data files with 10 - 100 columns and 10K - 1M rows, both quoted and unquoted. The stream implementation for each library were used to keep comparison consistent, but can be slower compared to self chunking in certain use cases.

<!-- tests -->
| columns x rows | cycles 
|----------------|--------
| 10 x 10,000 | 20 
| 100 x 10,000 | 10 
| 10 x 100,000 | 10 
| 100 x 100,000 | 5 
| 10 x 1,000,000 | 5 
<!-- tests -->

## Results 
Benchmarked on GitHub Actions. Only the fastest 5 will be visualized.

### Parse
![Quoted CSV Parser Benchmarks](https://github.com/willfarrell/csv-benchmarks/raw/main/results/parse_quotes%3Dtrue.png)

<!-- parse quotes=true -->
| Package | 10x10K | 100x10K | 10x100K | 100x100K | 10x1000K 
|---------|---|---|---|---|---
| **csv-rex** | 24ms | 188ms | 230ms | 1,890ms | 2,300ms 
| **papaparse** | 42ms | 215ms | 409ms | 2,057ms | 4,016ms 
| **csv-parser** | 38ms | 349ms | 381ms | 3,720ms | 4,081ms 
| **csvtojson** | 58ms | 451ms | 555ms | 4,557ms | 5,598ms 
| **csv-parse** | 77ms | 658ms | 748ms | 6,851ms | 8,345ms 
| **csv-streamify** | 74ms | 721ms | 837ms | 7,966ms | 9,153ms 
| **fast-csv** | 107ms | 947ms | 1,096ms | 9,926ms | 11,432ms 
<!-- parse quotes=true -->

![Non-Quoted CSV Parser Benchmarks](https://github.com/willfarrell/csv-benchmarks/raw/main/results/parse_quotes%3Dfalse.png)

<!-- parse quotes=false -->
| Package | 10x10K | 100x10K | 10x100K | 100x100K | 10x1000K 
|---------|---|---|---|---|---
| **csv-rex** | 9ms | 45ms | 81ms | 458ms | 807ms 
| **csvtojson** | 33ms | 254ms | 329ms | 2,581ms | 3,351ms 
| **csv-parser** | 34ms | 324ms | 352ms | 3,411ms | 3,793ms 
| **papaparse** | 127ms | 62ms | 1,161ms | 542ms | 10,431ms 
| **csv-parse** | 59ms | 526ms | 614ms | 5,579ms | 6,564ms 
| **csv-streamify** | 68ms | 681ms | 787ms | 7,715ms | 8,876ms 
| **fast-csv** | 88ms | 781ms | 912ms | 8,098ms | 9,479ms 
<!-- parse quotes=false -->

### Format

![Non-Quoted CSV Formatter Benchmarks](https://github.com/willfarrell/csv-benchmarks/raw/main/results/format_quotes%3Dfalse.png)

<!-- format quotes=false -->
| Package | 10x10K | 100x10K | 10x100K | 100x100K | 10x1000K 
|---------|---|---|---|---|---
| **csv-rex** | 22ms | 108ms | 223ms | 1,090ms | 2,286ms 
| **csv-stringify** | 25ms | 111ms | 245ms | 1,104ms | 2,505ms 
| **fast-csv** | 29ms | 137ms | 293ms | 1,322ms | 2,810ms 
<!-- format quotes=false -->

## Thanks
- leanylabs who inspired the making of this repo with their article [CSV Parsers Comparison](https://leanylabs.com/blog/js-csv-parsers-benchmarks/).
- [quickchart.io](https://quickchart.io) for the automation of the chart creation.
- GitHub for providing free use of Actions for running the benchmarks.
