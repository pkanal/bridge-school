## FP Exercises

### Pure functions
For each of the following functions decide whether they are pure functions or not and explain why briefly.

3. ```javascript
  function(x, y) {
    console.log(x + y);
    return x + y;
  }
```

1. ```javascript
  function(x, y) {
    return x + y;
  }
```

2. ```javascript
  function(x, y) {
    return x + y + Math.random();
  }
```

4. ```javascript
  function(x, y) {
    const rand = Math.random();

    if(rand > 0.5) {
      throw 'This random number is greater than 0.5';
    }

    return x + y;
  }
```
