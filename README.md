# Analysis of multi-pass IRV elections

The multi-pass Instant-Runoff Voting (IRV) voting method is considered by Fairvote to be
a type of Ranked-Choice Voting (RCV). It is also known as
[Preferential Block Voting](https://en.wikipedia.org/wiki/Preferential_block_voting),
Sequential IRV, Sequential AT-Large IRV, Sequential Ranked Choice Voting, etc.
It is used in several cities in Utah, and was used for the Portland, Maine
[Charter Commission Election](https://portlandphoenix.me/portland-charter-commission-meet-the-candidates/)
in 2021.

It appears to be far inferior to the multi-winner Single-Transferrable-Vote (STV) voting method,
which guarantees Proportional Representation, and which is also sometimes confusingly called RCV.

See also:

* [Voting systems in Utah](https://math.byu.edu/~jarvis/Voting.html)

## CVR data

This repository aims to facilitate analysis. It currently has the
cast vote records for some of these elections.

In order to tabuate the elections via the OpenSTV software, the original .xlsx (Excel) files
have been converted into .text files. For now, the files were saved to .csv from LibreOffice,
and then this pipeline was used to clean and reformat the data.
But note that it is preliminary work, with much room for improvement, and
may have bugs or fail to preserve all the information of interest.

```
# Drop first two columns, drop undervote/overvote, drop first header line,
# replace multiple tabs with one, avoid leading/trailing tab, drop blank lines
cut -f 3- Payson_CVR.csv |
 sed -E -e 's,undervote,,g' -e 's,overvote,,g' -e $'s,\t+,\t,g' -e $'s,\t$,,' -e $'s,^\t,,' -e '/^$/d' |
 tail +2 > payson.text
```
