# SQL Code Explaination

## Homepage w/dates

### Full Code
```sql
SELECT DATE(timestamp,&#39;Canada/Eastern&#39;) date, link_location, link_name, destination_url, COUNT(*) as
link_clicks
FROM `extreme-hull-204419.staples_services.link_clicked`
WHERE DATE(timestamp,&#39;Canada/Eastern&#39;) BETWEEN &#39;2024-01-27&#39; AND &#39;2024-02-27&#39;
AND context_page_path = &quot;/&quot;
AND (context_page_url NOT LIKE &quot;%dev%&quot; AND context_page_url NOT LIKE &quot;%staging%&quot;)
AND (link_location NOT LIKE &quot;%store locator%&quot; AND link_location NOT LIKE &quot;%search results%&quot;)
GROUP BY 1,2,3,4
ORDER BY DATE ASC, link_clicks DESC
```
### SELECT
 ```SQL
SELECT 
  DATE(timestamp,'Canada/Eastern') date, 
  link_location, 
  link_name, 
  destination_url, 
  COUNT(*) as link_clicks
```
**This selects five columns:**
 - The timestamp converted to a date in the Canada/Eastern timezone
 - The link_location
 - The link_name
 - The destination_url
 - A count of rows, aliased as link_clicks

### FROM
```SQL
FROM `extreme-hull-204419.staples_services.link_clicked`
```
This specifies the table we are looking for. \
For this case: extreme-hull-204419 -> staples_services -> link_clicked

### WHERE
```SQL
WHERE DATE(timestamp,'Canada/Eastern') BETWEEN '2024-01-27' AND '2024-02-27'
AND context_page_path = "/"
AND (context_page_url NOT LIKE "%dev%" AND context_page_url NOT LIKE "%staging%")
AND (link_location NOT LIKE "%store locator%" AND link_location NOT LIKE "%search results%")
```
**Filter the Data**
 - from 2024-01-27 to 2024-02-27
 - context_page_path = "/" *("/" usually means home page)*
 - "NOT LIKE "%dev%"" means fields do not contain "dev"
 
 ### GOURP BY
 ```sql
 GROUP BY 1,2,3,4
 ```
 - refer to the first four columns in the "SELECT" section

 ### ORDER BY
 ```SQL
 ORDER BY DATE ASC, link_clicks DESC
 ```
 - means order by date in ascending order, then by number of clicks in descending order
