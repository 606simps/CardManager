# CardManager
Web Apis for Create/Shuffle/Cut/Deal a deck of cards

HowTo Use

**/api/card/create** -> create a new deck of card with a unique id generated by the service, return null if fail  
**/api/card/{id}/create** -> create a new deck of card with a user given id, return null if fail  
**/api/card/{id}** -> use the user given id to access the deck, return null if fail  
**/api/card/{id}/returndeck** -> use the user given id to access the deck, return null if fail  
**/api/card/{id}/shuffle** -> shuffle cards with user given id, return null if fail  
**/api/card/{id}/cut** -> cut cards with user given id with random offset, return null if fail  
**/api/card/{id}/cut?offset={offset}** -> cut cards with user given id and with user given offset, return null if fail  
**/api/card/{id}/pop** -> pop one card off the deck with user given id, return -1 if fail  

Service design

Cards are defined to be numbers from 0 to 51.  
Decks are stored in a Redis service, could be configured at AppSettings with key = "CacheConnection".  
Expiration time of the deck could be configured at AppSettings with key = "ExpirationTime".  
The expiration time of each deck refreshes if being **accessed/shuffled/cut/popped**.  
