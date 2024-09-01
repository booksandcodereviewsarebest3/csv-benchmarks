# JavaScript CSV Benchmarks

Benchmarks of popular CSV parsers and formatters:

<!-- packages -->
| Package | Version | Published | Parse | Format 
|---------|---------|-----------|-------|--------
| [csv-parse](https://www.npmjs.com/package/csv-parse) | 5.5.6 | 4 months ago | Yes |  
| [csv-parser](https://www.npmjs.com/package/csv-parser) | 3.0.0 | 4 years ago | Yes |  
| [csv-rex](https://www.npmjs.com/package/csv-rex) | 0.7.0 | 1 year ago | Yes | Yes 
| [csv-streamify](https://www.npmjs.com/package/csv-streamify) | 4.0.0 | 6 years ago | Yes |  
| [csv-stringify](https://www.npmjs.com/package/csv-stringify) | 6.5.1 | 1 month ago |  | Yes 
| [csvtojson](https://www.npmjs.com/package/csvtojson) | 2.0.10 | 5 years ago | Yes |  
| [fast-csv](https://www.npmjs.com/package/fast-csv) | 5.0.1 | 7 months ago | Yes | Yes 
| [papaparse](https://www.npmjs.com/package/papaparse) | 5.4.1 | 1 year ago | Yes |  
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
| **csv-rex** | 24ms | 172ms | 212ms | 1,724ms | 2,126ms 
| **papaparse** | 43ms | 209ms | 406ms | 1,992ms | 3,918ms 
| **csv-parser** | 38ms | 349ms | 390ms | 3,668ms | 4,116ms 
| **csvtojson** | 56ms | 451ms | 558ms | 4,528ms | 5,611ms 
| **csv-parse** | 77ms | 667ms | 745ms | 6,802ms | 7,873ms 
| **csv-streamify** | 78ms | 700ms | 805ms | 7,778ms | 8,941ms 
| **fast-csv** | 106ms | 937ms | 1,079ms | 9,743ms | 11,226ms 
<!-- parse quotes=true -->

![Non-Quoted CSV Parser Benchmarks](https://github.com/willfarrell/csv-benchmarks/raw/main/results/parse_quotes%3Dfalse.png)

<!-- parse quotes=false -->
| Package | 10x10K | 100x10K | 10x100K | 100x100K | 10x1000K 
|---------|---|---|---|---|---
| **csv-rex** | 9ms | 43ms | 81ms | 446ms | 797ms 
| **csvtojson** | 33ms | 244ms | 328ms | 2,483ms | 3,291ms 
| **csv-parser** | 32ms | 299ms | 332ms | 3,201ms | 3,587ms 
| **papaparse** | 129ms | 59ms | 1,156ms | 552ms | 10,482ms 
| **csv-parse** | 58ms | 518ms | 601ms | 5,525ms | 6,278ms 
| **csv-streamify** | 68ms | 699ms | 810ms | 7,886ms | 9,105ms 
| **fast-csv** | 88ms | 773ms | 904ms | 8,114ms | 9,464ms 
<!-- parse quotes=false -->

### Format

![Non-Quoted CSV Formatter Benchmarks](https://github.com/willfarrell/csv-benchmarks/raw/main/results/format_quotes%3Dfalse.png)

<!-- format quotes=false -->
| Package | 10x10K | 100x10K | 10x100K | 100x100K | 10x1000K 
|---------|---|---|---|---|---
| **csv-rex** | 23ms | 108ms | 228ms | 1,080ms | 2,314ms 
| **csv-stringify** | 26ms | 114ms | 247ms | 1,123ms | 2,362ms 
| **fast-csv** | 29ms | 139ms | 291ms | 1,387ms | 2,854ms 
<!-- format quotes=false -->

## Thanks
- leanylabs who inspired the making of this repo with their article [CSV Parsers Comparison](https://leanylabs.com/blog/js-csv-parsers-benchmarks/).
- [quickchart.io](https://quickchart.io) for the automation of the chart creation.
- GitHub for providing free use of Actions for running the benchmarks.
