REFEREE'S NOTE TO MS NOOR
WHAT I FOUND IN MESSY FILE
The file had 97 rows. Before any calculation I had to clean it:
Price was stored as text because of 1,250 with a comma.
Staple A, City 2, 2026-01-15 = 1,250 — flagged / implausible.
Sweetener D, City 1, 2026-01-22 = 9,999 — flagged / implausible.
One row was labelled oil b (lowercase) with price 108.5 — this fits Staple A (99–120), not Oil B (298–350). I fixed it to Staple A.
One duplicate: Staple A, City 1, 2026-01-08, 99.5 appeared twice. I dropped 1 copy.
One missing value: Pulse C, City 2, 2026-01-01 = NaN. I kept it as missing, I did not fill it with 0.
Cleaning decisions:Drop duplicate, fix oil b → Staple A, drop 1,250 and 9,999.
I did NOT guess the flagged values as 125 / 99 — there is no evidence for those values in the file.

CLEANED SUMMARY:
First-to-last = first-week average (1 Jan, 2 cities) vs last-week average (19 Mar, 2 cities).
ITEM: STAPLE A:
valid n: 23
mean:111.26
median:112.5
first wk avg:104
last wk avg:117.50
first to last%:+12.98

ITEM: OIL B
valid n:24
mean:324.83
median:324
first wk avg:301
last wk avg:347
first to last %:+15.28%

ITEM : PULSE C
valid n:23
mean:205.91
median:206
first wk avg:200
last wk avg:210.50
first to last %:+5.25%

ITEM:SWEETENER D
valid n:23
mean:167.15
median:167.50
first wk avg:152
last wk avg:181.50
first to last%:+19.41%

With / without flagged value:

STAPLE A
with 1,250
n:24
mean:158.71
median:112.50
Without 1,250
n:23
mean:111.26
median:112.50

SWEETENER D
with 9,999
n:24
mean:576.81
median:167.75
without 9,999
n:23
mean:167.15
median:167.50

MY RECOMMENDATION : 
1. Staple A: 
For Staple A, I would report the mean of 111.26 because after cleaning, the mean and median are almost the same, so the mean uses all 23 valid prices without being dragged by an outlier. O
Oil B: 
For Oil B, I would report the mean of 324.83 because there were no flagged values for Oil B, and the mean and median are almost the same, so the mean is a fair summary of the typical level. O
Pulse C: 
For Pulse C, I would report the mean of 205.91 because it is calculated on 23 valid prices, the 1 NaN is excluded not filled with 0, and the mean and median are almost the same. O
Sweetener D: 
For Sweetener D, I would report the mean of 167.15 because after dropping the flagged 9,999, the mean and median are almost the same, so the mean is no longer distorted. O

WHAT I WILL NOT CLAIM :
I will not claim that inflation, hoarding, or a supply shortage caused the price rise. C — not supported
One possible explanation is that the 1,250 and 9,999 values were data-entry errors. E — possible, not proven
One possible explanation is that the first-to-last rise reflects a general upward trend in these illustrative prices over Jan to Mar. E — possible, not proven
Price data alone cannot show cause. To claim cause, I would need extra data such as supply quantities, transport costs, wholesale prices, or a record of what changed in those weeks.

AUDIT OF MY FIRST DRAFT:
In my first draft I said: "Prices rose because of inflation / supply problems.
"That was a C pretending to be an O, because the file only has item, city, date, and price. It has no data on inflation, supply, demand, or costs, so I cannot recompute a cause from it.
Corrected version: "Prices were higher in the last week than in the first week for all 4 items, with the largest first-to-last rise for Sweetener D at +19.41%." O
Second corrected version: "One possible explanation is a data-entry error for the flagged values, but I cannot prove that from price data alone." E