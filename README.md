# README for DATA 512 A1 Project

## Goal
The goal of this project is to create a data visualization showing monthly traffic of English Wikipedia, from January 2008 to August 2021, using data pulled from two Wikimedia REST API endpoints.

## Source data
Source data for this project is pulled from The Wikimedia Foundation REST API, terms of use for which can be found [here](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions).

By using this API, you agree to Wikimedia's Terms of Use and Privacy Policy. Unless otherwise specified in the endpoint documentation below, content accessed via these APIs is licensed under the [CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) and [GFDL](https://www.gnu.org/copyleft/fdl.html) licenses, and you irrevocably agree to release modifications or additions made through this API under these licenses.

## API documentation
The Legacy Pagecounts API provides access to desktop and mobile traffic data from December 2007 through July 2016.
* [Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)
* [Endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)

The Pageviews API provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.
* [Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)
* [Endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)

## Column descriptions for en-wikipedia_traffic_200712-202108.csv
* __year__: year in which the views occurred, YYYY (string) format
* __month__: month in which the views occurred, MM (string) format
* __pagecount_all_views__: sum of desktop + mobile view count pulled from Legacy Pagecounts API
* __pagecount_desktop_views__: desktop view count pulled from Legacy Pagecounts API
* __pagecount_mobile_views__: mobile view count pulled from Legacy Pagecounts API
* __pageview_all_views__: sum of desktop + mobile (web + app) view count pulled from Pageviews API
* __pageview_desktop_views__: desktop view count pulled from Pageviews API
* __pageview_mobile_views__: mobile view count pulled from Pageviews API (sum of mobile web + mobile app views)

## Known issues & other considerations
* The Legacy Pagecount API only provides data from December 2007 to July 2016, while the Pageviews API provides data from July 2015 to the present. Data overlaps between the two from July 2015 to July 2016. 
* Data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not - this leads to systematically lower view counts in the Pageview data.
* The last month of Pagecount data (July 2016) looks like it's only partial data, as it has far lower views than the preceding months. For completeness, I haven't removed it, but it looks like an anomaly in the graph.
