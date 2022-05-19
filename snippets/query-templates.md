### Circ Totals

Count up all circ transactions by date, broken out by transaction type

    SELECT
    t.transaction_gmt::DATE AS "date"
    ,COUNT(t.id) FILTER(WHERE t.op_code = 'o') AS checkouts
    ,COUNT(t.id) FILTER(WHERE t.op_code = 'i') AS checkins
    ,COUNT(t.id) FILTER(WHERE t.op_code = 'r') AS renewals
    ,COUNT(t.id) FILTER(WHERE t.op_code = 'f') AS filled_holds
    ,COUNT(t.id) FILTER(WHERE t.op_code ~ 'n|h') AS holds_placed
    ,COUNT(t.id) FILTER(WHERE t.op_code = 'u') AS use_count
    ,COUNT(t.id) FILTER(WHERE t.op_code = 'b') AS bookings

    FROM
    sierra_view.circ_trans t

    GROUP BY 1
    ORDER BY 1
    
#### Output    
| date | checkouts | checkins | renewals | filled_holds | holds_placed | use_count | bookings |
| ---- | --------- | -------- | -------- | ------------ | ------------ | --------- | -------- |
| 2022-04-13 | 9127 | 8178 | 709 | 2676 | 2588 | 26 | 0|
| 2022-04-14 | 25134 | 25525 | 22776 | 7854 | 6483 | 101 | 0|
| 2022-04-15 | 23171 | 21945 | 4960 | 6491 | 5395 | 36 | 0|
| 2022-04-16 | 24459 | 24423 | 1402 | 5598 | 5379 | 49 | 0|
| 2022-04-17 | 1081 |1965 | 32527 | 123 | 4253 | 0 | 0|
| 2022-04-18 | 24 |626 | 16987 | 6 | 4971 | 0 | 0|
| 2022-04-19 | 35486 | 41039 | 16250 | 6327 | 7588 | 196 | 0|
| 2022-04-20 | 26919 | 29142 | 13980 | 6114 | 5013 | 125 | 0|
