---
layout: default
title: Release notes
description: Latest release notes for the Firebolt data warehouse.
parent: General reference
nav_order: 1
has_toc: false
has_children: false
---

# Release notes

Firebolt continuously releases updates so that you can benefit from the latest and most stable service. These updates might happen daily, but we aggregate release notes to cover a longer time period for easier reference. The most recent release notes from the latest version are below. 

<!--- See the [Release notes archive](../release-notes/release-notes-archive.md) for earlier-version release notes. -->

{: .note}
Firebolt might roll out releases in phases. New features and changes may not yet be available to all accounts on the release date shown.

## DB version 3.29
**October 2023**

* [New features](#new-features)
* [Enhancements, changes, and new integrations](#enhancements-changes-and-new-integrations)

### New features

<!--- FIR-25082 ---> **EXPLAIN ANALYZE now available for detailed query metrics**

You can now use the [EXPLAIN command](../../sql-reference/commands/explain.md) to execute `EXPLAIN (ANALYZE) <select statement>` and get detailed metrics about how much time is spent on each operator in the query plan, and how much data it processes. The query plan shown there is the physical query plan, which you can inspect using `EXPLAIN (PHYSICAL) <select statement>` without executing the query. It shows how query processing is distributed over the nodes of an engine.


### Enhancements, changes and new integrations

<!--- FIR-25636 ---> **PERCENTILE_CONT and PERCENTILE_DISC now return PG-compliant results**

[PERCENTILE_CONT](../../sql_reference/functions-reference/window/percentile-cont-window.md) for decimal input now returns DOUBLE instead of DECIMAL 

<!--- FIR-24362 ---> **Virtual column 'source_file_timestamp' uses new data-type**

The virtual column `source_file_timstamp` has been migrated from the data type `DateTime/Timestamp` (legacy timestamp type without time zone) to the type `TimestampTz` (new timestamp type with time zone).

Despite the increased resolution, the data is still in second precision as AWS S3 provides them only as unix seconds

You must now use `source_file_timestamp - now()` instead of `date_diff('second', source_file_timestamp, now())`

<!--- FIR-10514 ---> **New function added**

A new function [ARRAY_TO_STRING](../../sql_reference/functions-reference/array/array-to-string.md) has been added as an alias to [ARRAY_JOIN](../../sql_reference/functions-reference/array/array-join.md)


