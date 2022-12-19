# Maderia
## Prototype 2

### User requirement specifications

1. The system must meet all the user requirement specifications mentioned for the first prototype, i.e, It must provide all the functionality the previous version provides.
2. Hotels should be able to provide their locations (the location of the hotel) during sign-up.
3. Users should be able to see a list of nearby hotels sorted with increasing distance from the location of the user.

### System requirement specifications
### General
1. This prototype should implement all system requirements for the first prototype unless those requirements are explicitly overridden in this document.

### The Sign-up process
1. The sign up page for hotels should provide 2 options for hotels to enter their location: one option should be to automatically detect the location of the device signing up (using the HTML geolocation API). The other option should be to display a map and let the client pick a point on the map. We let the client choose which method to use. The acquired location data should have the form (latitude, longitude). Getting the location data of the hotel will be handled with front-end logic.
2. The location data should then be sent along with the hotel name, email, etc. to the server for registration. (We CAN use 'URL variables' to pass the location data to the server but it is recommended that we use a more robust way to do it).
3. The back-end code, upon receiving data for registration, should record the location of the hotels in addition to the hotel name, email, etc.

### the nearby-hotels page handler (on the back-end)
1. There should be two request handlers (controllers) that help to render the nearby-hotels page: the first will be a simple controller that accepts GET requests for the page itself and responds with the html (actually, handlebars) template for the page. the second will be a controller to accept data requests and respond with JSON data. the request for this controller should use some AJAX like method (the front-end should fetch data from the back-end without reloading the page). The fetched data should contain a list of hotel objects, each hotel object consisting of the name of the hotel and the location of the hotel (in latitude and longitude). From this point on, we call this data "the nearbt-hotels data". The nearby-hotels data should be enough to render all parts of the nearby-hotels page on the front-end.
2. Preparing the nearby-hotels data (before sending it out through the associated controller) should be handled by a service method. This service should simply accept a location (of a user) (in the form of latitude and longitude) and a natural number 'n', then fetch all hotels from the database, calculate the displacement (as in physics) of each hotel location from the user location (using the distance formula), then sort the hotels with increasing order of their calculated distance from the user's location, and finally return the top 'n' closest hotels. The controller should be able two wrap this (returned) data in a convenient form and send it to the front-end.

### The nearby-hotels page (on the front-end)
1. The purpose of the nearby-hotels page is to show users what hotels are found nearby (on a map), along with their distance from the location of of the user
2. On the nearby-hotels page should have two main parts: one is a list of nearby hotels, each list item containing the name of a hotel and distance in KM of the hotel from the current location of the user. the second part should be a map, on which the locations of the hotels are marked with appropriate symbols.
3. There should be a one-to-one correspondence between the items in the list and the markers on the map. The list items in the first part should be SCROLLABLE  and SELECTABLE. selecting a list item (which represents a hotel) should move the map view and center the selected hotel, and give the hotel a slightly different marker on the map to make it stand out of the background.
