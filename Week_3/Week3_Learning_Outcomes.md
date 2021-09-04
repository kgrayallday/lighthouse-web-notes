# Week 3 Learning Outcomes 
## Web Servers
  - HTTP and Nodes require('http');
  - an IP is like a Hotel 🏢 and a Port is like the hotel room #
  - Response Codes
    - Information 100 - 199
    - Success 200 - 299
      - 200 **OK**
    - Redirects 300 = 399
    - Client Errors 400 - 499
    - Server Errors 500 - 599
      - 400 **Bad Request**
      - 401 **Unauthorized**
      - 403 **Forbidden**
      - 404 **Not Found**
  - Learned Express and about package.json
    - require('express');
    - app.get('/url-route', (req, res) => { res.send('msg to client'); });
    - app.post('/url-route', )
  - Templates, Template Engines & Embedded JavaScript (EJS)
    - Beloathed Alligator tags <%= %>, <% %>
    - Route paramaters " : " ex. /urls/:shortURL
  - CRUD and BREAD
  - Nodemon (utility monitors code change and auto re-up server)
  - Cookies and saving users data and setting permissions
  - Security: Encryption(two-way) vs Hashing(one-way)
    - bcrypt
    - cookie-session


## Data Structures
  - can explain what data structures are
  - can explain what a tree is
  - can explain why trees are useful
    - useful when we have hierarchical data structures
  - can use a tree to organize data
  - can explain what tree traversal is
    - like looping through an array we go through the nodes
  - can explain the difference between breadth first and depth first search
    - Breadth First - starts with the first node and checks the nodes closest to it then moves through children and children of children 
    - Depth First - accomplished the same as Breadth First but follows the path to the leaf node first and then visits siblings before moving back up, 
  - can use depth first search to search for an object in a tree
  - can traverse through a tree to find information
  - can implement recursive tree traversal functions

#### Tree Trversal Code Example
```javascript
class Node {

  constructor(data) {
    this.data = data;
    this.parent = null;
    this.children = [];
  }

  depthFirstTraversal() {

    console.log(this); // 1

    for (const childNode of this.children) {
      childNode.depthFirstTraversal(); // 2
    }
  }
}
```
1) Visit the current node. In this case, we're just printing out the data.
2) Loop through every child of the current node and repeat the first step with that node.

I used this code:
```javascript
  employeesThatMakeOver(amount) {

    let employees = []; 
    // 1 Create a new employees array to hold every employee
    //   that makes over thespecified amount.

    if (this.salary > amount) {
      employees.push(this);
    }
    // 2 If the current employee makes over that amount,
    //   add them to the array.

    for (const subordinate of this.subordinates) {
      const subordinatesThatMakeOver = subordinate.employeesThatMakeOver(amount); 
      employees = employees.concat(subordinatesThatMakeOver);
    }
    // 3 Call this method on all of the current employee's subordinates 
    //   and combine their results with the current results.

    return employees;
  }
```
### To figure out this code:

```javascript
  class Employee {

    // ... prev code here

    get totalEmployees() {

      let totalEmployees = 0; // 1

      // Use depth first traversal to calculate the total employees

      return totalEmployees;

    }
  }
```
See answer is [here](Day_4/DFS_recursion_proof.md)