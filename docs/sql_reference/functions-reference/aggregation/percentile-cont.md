---
layout: default
title: PERCENTILE_CONT
description: Reference material for PERCENTILE_CONT aggregate function
grand_parent: SQL functions
parent: Aggregation functions
great_grand_parent: SQL reference
---

# PERCENTILE_CONT

Calculates a percentile, assuming a continuous distribution of values of the input expression defined. Results are interpolated, rather than matching any of the specific column values. 

`PERCENTILE\_CONT` is available as a [window function](../window/index.md). 
See also [PERCENTILE\_DISC](./percentile-disc.md), which returns a percentile equal to a specific column value.


## Syntax
{: .no_toc}

```sql
PERCENTILE_CONT( <value> ) WITHIN GROUP ( ORDER BY <expression> [ { ASC | DESC } ] )
```

## Parameters 
{: .no_toc}

| Parameter | Description                                     | Supported input types | 
| :--------- | :----------------------------------------------- | :---------|
| `<value>`   | Percentile value for the function | `DOUBLE PRECISION`/`REAL` literal between 0.0 and 1.0 |
| `<expression>`  | Expression used for the `ORDER BY` clause | `NUMERIC` | 

## Return Types 
`DOUBLE PRECISION`
This function ignores `NULL` values.

## Example
{: .no_toc}

The example below calculates the median percentile value based on continuous distribution of student grade levels. 

```sql
SELECT
	grade_level,
	PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY test_score) AS percentile
FROM
	class_test
GROUP BY grade_level;
```

**Returns**:

```sql
' +-------------+------------+
' | grade_level | percentile | 
' +------------+-------------+
' | 9           |        79.5 |
' | 10          |          78 |
' | 11          |          74 |
' | 12          |          93 |
' +-------------+------------+
```
