#### Week 3 Day 4
# Security 

### Passwords
 - must not be stored in plain text (duh)
 - salt password > (hash function) > salt | result
 - Hashing only works in one direction 
 - each hashing iteration double the time it takes to hash the content
 
 ### Cookies
  - plain text cookies (con: can be easily edited)
  - stored on client(user) computer
  - solution is to use Encryption

### Encryption
  - unlike hashing encryption is a two way street
  - cookie-session, 

### Hash
  - different output strings for each hash 
  - when storing a hash password, we have to compare the stored hash to the hash generated at the time of attempted login.
  - you're really checking if two hashes came from the same source
  - popular took : bcrypt

### HTTPS

### REST
  - Representational State Transfer
  - you have data on one computer and you want to send it to another
  - convention on how to do so 
  - REST API uses http verb and end point: 
    - get '/quotes'
    - get '/quotes/:id'
    - get '/quotes/new'
  - POST and GET are just conventions you could use either to do anything. 

### Middle Ware
  - you could use middle ware to access PATCH and DELETE via POST or GET 
  - such as Method Override - to follow convention - to make code more self documenting
  - Middle ware will run on all the end points - on every request that comes in



  