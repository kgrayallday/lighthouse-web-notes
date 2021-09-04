# Week 3 Day 2 Notes - CRUD with Express

### Implement CRUD over HTTP with Express

## What is CRUD?
Ways in which a client can interact with some resource (data)
  - Create
  - Read 
  - Update 
  - Delete

  ## BREAD

  - Browse (see all items in a resource) /GET
  - Read /GET
  - Edit /POST
  - Add /POST
  - Delete /POST

creating file server.js
npm init
install express and morgan (npm i)
go into server and set up "const express = require('express);
also set up const morgan = require('morgan');
specify a port "const port = 8080;"
create an object/instance of express "cosnt app = express();"

now we want to ues morgan: "app.use(morgan('dev'))"

(this is a lot of code to write without being tested so... 

```
app.listen(port, () => {
  console.log(`server is now listening on port ${port}`
});
```
if we run the server now we will see morgan is giving us feedback under console.log

Note on Arrays: whenever order is required Arrays are great. 

we will be creating an Object in this case, example used was skateboards

create /skateboard dir as so:
```
app.get('/skateboards', (req, res) => {
  const templateVars = { skateboards : skateboards } // shorthand just { skateboards }
  res.render('skateboards', templateVars)
})
```
res.render will look for templates, we will give res.render the first argument of 'skateboards' (unrelated to to the path in app.get, it just makes sense).
second argument will be an object of keys (think mad-libs with nouns adjectives etc.) to fill in our template. 

if we run our server now we will get an error regarding engine not set, we will need to specify an engine for express to use 

```
app.use('view engine', 'ejs');
```
EJS will look for a dir called "views" if you don't have this already you will have to create one

### alligator tags (EJS)
<%= %> = runs code and displays it in browser
<% %> without = is used just for logic but does not output anything

### templateVars
```
const templateVars = {skateboards: skateboards}
```

now we want to return a single skateboard 
```
app.get('skateboards/:id', req.params)
console.log('req.params', req.params)
const id = req.params.id                // get single id from params?
const skateboard = skateboards[id]      // we are grabbing an individual skateboard
const templateVars = { skateboard };    // create a template to show an individual something

res.render('skateboard', templateVars)
// res.send('almost there!') // did this get removed?
```
show a single skateboard in html: 
<div>
  <h2> color <%= skateboard.color %></h2>
  <h2> color <%= skateboard.length %></h2>
  <h2> color <%= skateboard.broken %></h2>
</div>

now if we pass in skateboard id into path 8080/skateboard/efgh

what is we pass in an id that does not exist? we get an error "cannot find color of undefined"

so we need to handle this (today we will do a check 

```
app.get('skateboards/:id', req.params)
console.log('req.params', req.params)
const id = req.params.id               
const skateboard = skateboards[id]     
if(!skateboard){
  res.redirect(/skateboards) // if id does not exist redirect them to the main page (or you could do an error page)
  return
}
const templateVars = { skateboard }; 

res.render('skateboard', templateVars)
```

## POSTS
we want to edit a single item. edit a skateboard
"body" data that the client is sending to the server

We want to edit 
app.post('/skateboards/:id', (req, res) => {
  const id = req.params.id
  console.log('req.body', skateboard)

  res.redirect('/skateboards')
}

in HTML one of the ways we send a post request is by creating a 'form'
  we will need two things
  1) method='POST'
  2) action='/skateboards/'

  edit templateVars to have skateboardId: id

```
app.get('skateboards/:id', req.params)
console.log('req.params', req.params)
const id = req.params.id               
const skateboard = skateboards[id]     
if(!skateboard){
  res.redirect(/skateboards) 
  return
}
const templateVars = { skateboard, skateboardId: id }; // added here skatebaord id to give us access to the id in url

res.render('skateboard', templateVars)
```
for form action= "/skateboards/<%= skateboardId %>

express has a built in method to replace body-parses. it is urlEncoded()

app.post('skateboards/:id', (req, res) => {
  const id = req.params.id
  const color - req.body.color;
  skateboards[id].color = color

  res.redirect('/skateboards')
})

## now we want to add a skateboard 
so we will adda  post and we want to work with path /skateboards (it will signify we are adding a new skateboard)
```
app.post('/skateboards', (req, res) => {
  console.log(req.body', re
  res.redirect('/skateboards')
}
```

Form will need 
  1) method='POST'
  2) action="/skateboards"
  3) correct names on all labels corresponding to object properties

Now we just need to add object to our "database" (which is actually just an object in memory for now)
in app.post:
const new skateboard
const newid 
skateboard[id] = newSkateboard;

## now we want to delete a skateboard
we will use post ut our path /skateboards/:id is already used so we will need to use /skateboards/:id/delete

```
app.post('/skateboards/:id/delete', (req, res) => {
  const id = req.params.id   // we know we are getting the params from our id 

  delete skateboards[id];

})
```
action="/skateboards/<%= skateboardId %>/delete"

## The Response (something something) Convention
  - you always want to receive the response, do something and then reply?

## Render vs Redirect
why do we use redirect instead of render?
  if re-rendering we would need 
  keeps logic separate
