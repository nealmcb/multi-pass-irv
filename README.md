# Analysis of multi-pass IRV elections

The multi-pass Instant-runoff voting (IRV) election method, also known as Preferential Block Voting, is considered by Fairvote to be a type of Ranked-choice voting (RCV). It is used in many cities in Utah, and was used for the Portland, Maine, Charter Commission Election.

This repository has the cast vote records for some of these elections, to facilitate analysis.

The .text versions come from this provisional pipeline, to convert the csv versions of the Excel files into a form suitable for the OpenSTV software.

# Drop first two columns, drop undervote/overvote, drop first header line, replace multiple tabs with one, avoid leading/trailing tab, drop blank lines
cut -f 3- /srv/voting/stv/Payson_CVR.csv | sed -E -e 's,undervote,,g' -e 's,overvote,,g' -e $'s,\t+,\t,g' -e $'s,\t$,,' -e $'s,^\t,,' -e '/^$/d' | tail +2 > payson.text
