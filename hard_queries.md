# Hard Queries

## Or, What I Did When The SQL Cookbook Ran Out

These are my notes from some of the tougher querying ideas I've learned on the
Data Services team.

## Points to Line Segments / Trip Summaries

We had a table of events over time associated with a parent record,
e.g. `parent_id, point_data, created_at`. What we wanted was a summarization
table saying "for each day, this record started with this event and ended on
this event". (A good example of this might be a salesman checking in with
lat,lng on a road trip where we want to know where the salesman started and
ended each day, or for a document workflow keeping track of what state the
document started and ended in for each day.) (Caveat: The problem with
summarization is you lose detail, but that's because the entire point of
summarization is to get rid of detail.)

How we built the report: We used two CTEs with window functions, both
partitioning by date, and ordered by created_at but in opposite directions. Then
we grabbed the first row from each window.

## Looping Through A JSON Array / Exploding An Array Into Rows

Think fp here: Recursive CTEs are a thing, and we can select elements from a
recursive CTE with level=0 as the parent row, then level2=level+1 as the child
rows.
