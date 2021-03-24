*NB: For the purpose of this archive all American states, incorporated territories, unincorporated territories, Native Tribes, or any other sub-national administrative division(s) will be referred to as a "state". All counties, parishes, boroughs, districts, atolls, independent cities, or any other Census recognized county equivalents will be referred to as a "county".*

### Scope
To download, and make publicly available each of the 3,242 American counties' police department websites for the purpose of archival and version control.


### Rationale
1. The only way to reach many county police department websites is via a search engine. Occasionally they do not even appear in search results.

2. **County websites have no standardized naming convention.** For example the Overton County Sheriff's Department in Tennessee has the URL `http://www.overtonsheriff.com/`, while the Alaska's Anchorage Borough Police Department's URL is `http://www.muni.org/departments/police/Pages/default.aspx`.

3. **There is no known catalogue for county police website URL's**. Some states do a decent job of cataloguing county police departments. California maintains `https://post.ca.gov/le-agencies`, though the vast majority of states do not maintain such a record.


### Goals
1. To maintain a comprehensive list of each county police department's website URL.

2. To develop a simple and known schema in order to allow accessing county websites iteratively. For example: instead of navigating to `http://bibbsheriff.us/`, a user could instead navigate to `http://pdap.io/alabama/bibb`.

3. To maintain version control of public police data. Data retention requirements for something like citations are so low that it is difficult to build a historical trend.

4. To lower bandwidth usage against local municipalities by creating a central place PDAP can point scrappers to.


### Implementation
County police websites will be organized via comma-separated values [RFC 4180](https://tools.ietf.org/html/rfc4180 "RFC 4180"). We will record at least 3 fields of information: the state, county, and website URL.
```bash
$STATE,$COUNTY,$WEBSITE
```
A program would recursively browse, download, and index each webpage. The program will function as though it were a real person clicking through the website (albeit, quickly); therefore it will obey any "rules" the website may have (such as a cookie cache, login requirements, polling requirements), and would only interact with web-facing content such that a visitor would.
