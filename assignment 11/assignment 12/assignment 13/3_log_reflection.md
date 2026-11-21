Cleaning log — what I did before any calculation
1. problem found: price stored as text
   evidence: 1,250 has a comma
   what i did: removed comma, converted to numeric 
2. problem found: flagged value
   evidence: Staple A, City 2, 2026-01-15 = 1,250
   what i did : Dropped the row, did NOT guess it as 125
3. problem found: flagged value
   evidence:Sweetener D, City 1, 2026-01-22 = 9,999
   what i did : Dropped the row, did NOT guess it as 99
4. problem found: Mislabelled item
   evidence: oil b, lowercase, 2026-02-05, City 1, price 108.5
   what i did: Fixed oil b → Staple A, because 108.5 fits Staple A (99-120), not Oil B (298-350)
5. problem found: Duplicate
   evidence:Staple A, City 1, 2026-01-08, 99.5 appears twice
   what i did: dropped 1 copy
6. problem found: missing value
   evidence: Pulse C, City 2, 2026-01-01 = NaN
   what i did: Kept as missing, did NOT fill with 0

   ASK — What I asked the AI (Interpretation Auditor)
   I pasted my statistics table from 2_work.ipynb and asked:"Here is my cleaned table. Interpret it for Ms. Noor. Do not give me a final note, just interpret the numbers."I did NOT replace my note with its text. I used it as a coach / critic only.

CHECK — Audit table: claim, colour, how I checked, accepted or rejected
Green = I can recompute it. Amber = possible explanation. Red = causal claim or refers to data I was not shown

1. Claim: Staple A cleaned mean is 111.26, median is 112.50
Colour: Green
How I checked: Recomputed in 2_work.ipynb, matches my table
Decision: Accepted
2. Claim: Oil B cleaned mean is 324.83, median is 324.00
Colour: Green
How I checked: Recomputed in 2_work.ipynb, matches my table
Decision: Accepted
3. Claim: Pulse C cleaned mean is 205.91 on 23 valid prices
Colour: Green
How I checked: Recomputed, 1 NaN excluded, matches
Decision: Accepted
4. Claim: Sweetener D cleaned mean is 167.15, median is 167.50
Colour: Green
How I checked: Recomputed in 2_work.ipynb, matches my table
Decision: Accepted
5. Claim: With 1,250, Staple A mean is 158.71, median stays 112.50
Colour: Green
How I checked: Recomputed with / without in 2_work.ipynb
Decision: Accepted
6. Claim: With 9,999, Sweetener D mean is 576.81, median moves to 167.75
Colour: Green
How I checked: Recomputed with / without in 2_work.ipynb
Decision: Accepted
7. Claim: Mean uses every value, so one extreme drags it, median only uses the middle value so it is robust
Colour: Green
How I checked: True from definition, and shown by the with / without numbers
Decision: Accepted
8. Claim: The 1,250 and 9,999 values were probably data-entry errors
Colour: Amber
How I checked: Possible, but I have no entry log to prove it
Decision: Accepted as E only, not as fact
9. Claim: Prices rose because of inflation / hoarding / supply shortage
Colour: Red
How I checked: File has only item, city, date, price. No inflation, supply, or cost data
Decision: Rejected
10. Claim: Sweetener D rose the most, so demand for sweetener must have risen
Colour: Red
How I checked: First-to-last rise is +19.41%, but rise does not prove demand caused it
Decision: Rejected
11. Claim: Pulse C is stable because its first-to-last rise is only +5.25%
Colour: Amber
How I checked: +5.25% is the smallest rise, but "stable" is a judgement, not a recomputed number
Decision: Accepted as E only, with the number shown
12. Claim: The median is always better than the mean
Colour: Red
How I checked: Not true. After cleaning, mean is almost equal to median, so mean is fine here. Median is better only when there is an outlier
Decision: Rejected

CONFUSED CLASSMATE — Transcript excerpt
Classmate: "The mean is always the typical price, right? Why do we need the median?"
Me: "Not always. The mean uses every value. So if one value is wrong and huge, the mean gets dragged.
"Classmate: "But why? One value can't change it that much?"
Me: "It can. Look at Sweetener D. Without the flagged value, the mean is 167.15. With 9,999 included, the mean is 576.81. One row moved it by +409.66.
"Classmate: "But why didn't the median move then?"
Me: "Because the median only looks at the middle value when you sort the prices. One huge value at the top doesn't move the middle. It moved from 167.50 to 167.75, only 0.25."
Classmate: "So should we always use the median then?"Me: "No. After we drop the flagged values, the mean and median are almost the same for all 4 items. For Staple A, mean 111.26, median 112.50. So after cleaning, the mean is fine because it uses all valid prices and there is no outlier left to drag it."Classmate: "Okay, so median protects you before cleaning, mean is fine after cleaning?"
Me: "Yes, exactly. Show with / without, clean first, then choose. Don't just pick one and ignore the other."
What the excerpt shows: I explained until the confusion stopped repeating. The key point was not "median is better" — it was "one row moves the mean a lot, the median barely moves, and after cleaning they agree."

REFLECT — Where did my first draft say more than the data allowed?
In my first draft I said: "Prices rose because of inflation / supply problems."
That was a C pretending to be an O, because the file only has item, city, date, and price. It has no data on inflation, supply, demand, or costs, so I cannot recompute a cause from it.
Corrected version: "Prices were higher in the last week than in the first week for all 4 items, with the largest first-to-last rise for Sweetener D at +19.41%." O
Second corrected version: "One possible explanation is a data-entry error for the flagged values, but I cannot prove that from price data alone." E
What I will do next time:
Check data types, duplicates, and labels before any mean / median.
Always show with / without for any flagged value.
Label every sentence O / E / C before submitting, and delete any C that is not supported.


AI use log for this file
 Used AI as coach / critic / classmate, not to produce my assessed answer.
 I pasted only my invented teaching-data statistics table, no personal or confidential data.
 I recomputed every number in 2_work.ipynb before accepting it.
 My final note in 1_attempt.md is my own draft, with O / E / C labels checked by me.