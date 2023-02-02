# Building a bridge database and news app

Using R, Datasette and Flask, I created a U.S. bridge explorer and a failing bridges news app. The [Datasette bridge explorer](https://bridge-inventory.glitch.me/) is designed for reporters and researchers interested in capturing key information about bridges across the U.S. The [Flask app](https://rinatorch.github.io/bridges/index.html) is a new application designed for readers and users to explore details of structurally failing bridges in the U.S. The source data from the 2022 National Bridge Inventory includes detailed information about all bridges in the U.S. 

## The Datasette app
The bridge inventory dataset is massive. In order for the database to be useful to reporters, I zeroed in on specific columns. I selected year built, location, facility carried, state, county and owner. Column values are coded, so I created a series of lookup tables and used base R to configure the column values to the code descriptions. This was important in improving the readability and usability of this data. The selected columns should allow a reporter covering a story about a bridge, whether a collapse or construction, to identify key details of a given bridge with a quick search. 

Datasette allows for ease of information-sharing and fact checking because the results of a search can be shared in a URL. This makes it easy to share the details of a given bridge or type of bridge. For example, users could share a result set of [all bridges owned by the army](https://bridge-inventory.glitch.me/data/bridges_cleaned?_sort=rowid&Owner__exact=Army) or the details of a specific [Maryland bridge built in 1809](https://bridge-inventory.glitch.me/data/bridges_cleaned?_sort=rowid&Year_Built__exact=1809&State__exact=Maryland) — the oldest one in the state.

I used [Glitch] to run this Datasette app. This strategy worked, but both Datasette and Glitch seem a bit overwhelmed by the size of this database.

## The Flask app

After discovering the bridge inventory's bridge condition ratings, I wanted to explore the bridges that were struggling the most. The bridge inventory rates the condition of several elements of a bridge. There are 10 condition levels. I was most interested in identifying bridges that had elements classified as "imminent failure," which is a step above failed bridges that are out of service. After doing some independent research on the elements of a bridge, I chose to look at deck, superstructure and substructure conditions. The inventory also included information on culverts, for example, but I was more interested in the structure of the bridge itself. Because I looked at conditions over three categories, some bridges included elements that were listed as out of service for some elements, but imminently failing in others. 

I used [Datatables](https://datatables.net/) to create the interactive table at the heart of this news app. It was important to make it searchable, sortable and paginated to make it easier to identify bridges with certain owners or in certain states. Sorting the bridges by year built can also be telling.

## Up next

This is just the beginning of what can be done with the U.S. National Bridge Inventory. A more powerful tool might be able to better serve the bridge explorer database. More reporting could yield a news application that maps the bridges and delves into the details of what it means when a bridge's substructure is out of service but its deck is not. Future analysis could also center on how conditions might vary based on the owner of each bridges. There is much more to investigate about the state of America's infrastructure.