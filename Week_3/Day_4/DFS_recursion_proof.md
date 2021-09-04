### Proof for Depth First Search Recursion Problem (Counting Subordinates)

```javascript
  get totalEmployees() {
    let totalEmployees = 0;

    if(this.subordinates){ // if there are subordinates
      totalEmployees += this.subordinates.length; // add number of subordinates to total
    }

    // call this method on all current subordinates
    for(const sub of this.subordinates) {
      // set numOfSubs holder variable to nested subs total
      const numberOfSubs = sub.totalEmployees;
      // and add that nested subs total to grand total
      totalEmployees += numberOfSubs;
    } 

    return totalEmployees;
  }
```