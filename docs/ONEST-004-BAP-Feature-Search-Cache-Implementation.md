### Problem:
When user searches for an intent, BAP should make search call to get the catalogues from all the providers and it should wait till the providers response and collate the catalouge and show to the user. This is a time consuming process and gives bad experience to the user.

### Solution:

Cache the search results(catalouge). Make the search call based on different intent criterias in periodic intervals and store the catalouge. When next time user searches, return the catalouge or item details from the cache.

