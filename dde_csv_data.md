---

copyright:
  years: 2018
lastupdated: "2018-06-12"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Resolving problems when using data from CSV files in {{site.data.keyword.dynamdashbemb_short}}
{: #resolving_problems_datafromcsvfiles}

You import a data asset based on a comma-separated values (CSV) file that contains dates or times, however the visualization results in {{site.data.keyword.dynamdashbemb_full}} are not what you expected.

## What's happening
{: #whatishappening}

When you create a visualization in a dashboard that displays dates or that is filtered by dates, the results are not what you expect. For example, you have a data asset that contains one row of data for each month. However, a visualization displays only dates from January for each year. Or, you have data from one month, but the visualization displays dates for a year. The following image explains the situation.

![UnexpectedresultwhenusingdatesinCSVfile](images/csvfile_explained.svg "Unexpected result when using dates in CSV file")

## Why it's happening
{: #whyitishappening}

The problems that you see might be caused by the format of the dates in your data, if the source for your data was a CSV file. For example, you have the following dates: 
-	1-1-2015
-	1-2-2015
-	1-3-2015
-	1-4-2015
-	1-5-2015
-	1-6-2015

When your data is imported, {{site.data.keyword.dynamdashbemb_short}} tries to determine the appropriate format to use for dates. However, you might get unexpected results. The first number in each date might be interpreted either as January or as the day, leading to different results. The date 1-2-2015 is interpreted as either January 2 or February 1.

To determine whether the format of dates is the potential cause of the problem, open your original CSV data file and review the format of the dates.

## How to fix it
{: #howtofixit}

If you have dates that represent a day, month, and year, change the format to be one that is supported by {{site.data.keyword.dynamdashbemb_short}}. Several formats are supported, but some can be ambiguous, as shown in the example above. If you format the dates in the yyyy-mm-dd format (ISO 8601), the dates are always interpreted correctly.

{{site.data.keyword.dynamdashbemb_short}} supports the ISO 8601 standard formats for dates (yyyy-mm-dd) and times. For more information about the standard, please see https://www.iso.org/iso-8601-date-and-time-format.html.


### Supported date formats
{: #supporteddateformats}
    M/d/yy
    MMM d, y
    MMMM d, y
    dd-MM-yy
    dd-MMM-yy
    yyyy-MM-dd

### Supported time formats
{: #supportedtimeformats}
    h:mm a
    h:mm:ss a
    h:mm:ss a z
    HH:mm
    HH:mm z
    HH:mm:ss
    HH:mm:ss.SS
    HH:mm:ss z
    HH:mm:ss.SS z

After you change your original data asset, open the dashboard again.
