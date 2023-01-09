# Maderia
## Parallel prototype 3
In the context of this document, the word "user" means a person who wants to see hotels and book rooms, "hotel" is just a hotel that has (or wants to have) an account in our system, and "client" is a general term used to refer to both users and hotels.

This document is a little different from previous specifications. In this document, care has been taken to avoid putting design constraints on what's to be implemented and instead, the interactions and functionalities the system shall provide are stressed. There could be multiple ways to implement these interactions and functionalities. The project management team, thus, should come up with possible designs and discuss on which one to implement (before implementation starts).

### User requirement specifications

1. The system must meet all the user requirement specifications mentioned for the second prototype, i.e, It must provide all the functionality the previous version provides.
2. Clients shall be able to see photos of hotels (which get uploaded by the hotels themselves)
3. Logged in users shall be able to write reviews about hotels
4. Logged in users shall be able to give n integer rating (out of 5) to a hotel.
4. Clients shall be able to see the reviews users have written about hotels and ratings given to those hotels.

### System requirement specifications
### General
1. The system shall have a hotel-detail page. This page shall feature a single hotel and display images of the hotel as well us reviews of the hotel written by customers.
2. On the hotel-detail page, the system should provide a way for registered users to write a review about that particular hotel and give a rating to that hotel.
3. The system should allow only one review and one rating by a particular user to a particular hotel. A user should not be able to write multiple reviews about a hotel or give multiple ratings. Once a user writes a review for and rates a hotel, subsequent reviews and ratings should update the previous ones.
4. Hotels shall be able to add new pictures to and remove them from their account. The hotel-profile page shall allow hotels to do this. The pictures shall be visible to clients on the hotel-detail page when clients see details of the hotel.
5. The front page shall display the top 20 rated hotels and a picture for each hotel (actually, one of the pictures of the hotel). clicking on one of the hotels shall open the hotel-detail page (featuring that hotel the client clicked)
