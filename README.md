# Building a U.S. bridge explorer

Using R and Datasette, I created a U.S. bridge explorer, designed for reporters and researchers interested in capturing key information about bridges across the U.S. The data comes from the National Bridge Inventory. This database is constructed based on the U.S. Bridge Inventory.

The source data from the 2022 National Bridge Inventory includes detailed information about all bridges in the U.S. This database zeroes in only on the critical details of each bridge, including its owner, year built and location, to cut through the noise of the massive database. Variables in the original dataset are coded. The data has been cleaned with lookup tables in R to allow for easy identification of bridge details.

The Datasette site structure allows users to share a single row with a URL, to ease fact-checking and information sharing.