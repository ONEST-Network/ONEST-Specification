### Problem:
When user searches for an intent, BAP should make search call to get the catalogues from all the providers and it should wait till the providers response and collate the catalogue and show to the user. This is a time consuming process and gives bad experience to the user.

### Solution:

Cache the search results(catalogue). Make the search call based on different intent criteria's in periodic intervals and store the catalogue. When next time user searches, return the catalogue or item details from the cache.

Suggested cache interval: 1hr