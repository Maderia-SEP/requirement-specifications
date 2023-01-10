# Maderia
## Parallel prototype 4
In the context of this document, the word "user" means a person who wants to see hotels and book rooms, "hotel" is just a hotel that has (or wants to have) an account in our system, and "client" is a general term used to refer to both users and hotels.

Again, in the context of this document, the terms "reservation" and "occupancy" should be clearly defined as follows: if a room is occupied, that means there already is a person using that room and the room is not empity. If a room is reserved, that means a user has chosen the room for a potential occupancy and the user is on his way to the hotel. Ubless the user arrives at the hotel on time, the reservation shall expire. If a room is neither reserved nor occupied, then this means it's free and can be reserved by a user. A room can be in one of 3 (three) these exclusive states : free, reserved or occupied.

This document is a little different from previous specifications. In this document, care has been taken to avoid putting design constraints on what's to be implemented and instead, the interactions and functionalities the system shall provide are stressed. There could be multiple ways to implement these interactions and functionalities. The project management team, thus, should come up with possible designs and discuss on which one to implement (before implementation starts).

### User requirement specifications

1. The system must meet all the user requirement specifications mentioned for the second prototype, i.e, It must provide all the functionality the previous version provides.
2.  Logged-in hotels shall be able to add room types to their account and change the number of rooms under each room type.
3. Clients shall be able to see if there are available rooms in a hotel.
4.  Logged-in users shall be able to reserve rooms in a hotel.
5.  Logged-in users shall be able to see the status of their reservations.
6.  Logged-in users shall be able to cancel their active reservations.
7.  Logged-in hotels shall be able to see the reservation and occupancy status of their rooms.
8.  Logged-in hotels shall be able to promote reservations into occupation. (if the user who reserved the room comes up on time and pays)

### System requirement specifications
1. The web-app shall have a "room-management" page that's accesible only by logged-in hotels. This page shall display the different room types the hotel provides, how many rooms of each room type there are, how many of these rooms are reserved and how many of these rooms are occupied.
2. the "room-management" page should also allow hotels to change the number of rooms the hotel has (under each room type)
3. the system shall not allow a hotel to lower the number of rooms under a certain room type below the number of the currently reserved + occupied rooms under that room type
4. the web-app shall have a "hotel-detail" page that shows the different room types in a hotel and whether or not a room is available under each room. if a room is available under a certain room type, this page shall allow a user to reserve an available room.
5. The web-app shall have a "user-reservations" page that only logged-in users can access. This page shall display (for each reservation of the user) the status of the reservation (active/expired) and the time left till the reservation expires (in hours and minutes)
6. The "user-reservation" page shall also allow the user to cancel an active reservation.
7. The web-app shall have a "reservation-management" page that only logged-in hotels can access. This page shall display all active reservations for and occupancies of rooms in that hotel. (This does not include free rooms)
8. the "reservation-management" page shall allow a hotel to promote a particular reservation into an occupancy. (this happens when the user comes on time and pays).
9. ocupancies should be recorded with their own expiry times. The expiry time should be provided by the hotel while promoting the reservation to occupancy. (we assume the hotel asks (in person) the occupant how many days the occupation lasts) When the occupancy (inavitably) hits the expiry time, the state of the room shall switch to 'free'. (we assume that the user/occupant has left the room)
10. If the reservation hits the expiry time without being promoted into occupancy, the state of the room shall switch to 'free'