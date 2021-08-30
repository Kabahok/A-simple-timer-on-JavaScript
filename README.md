# `A simple timer on JavaScript`

### Let's start with the basic settings:
We creat a variable, in which the arrow function was placed and 2 arguments were passed:

```JavaScript
  const timer = (id, deadline) => {}
```

We immediately import the function to use it in the assembly (if you are working with a modular structure):

```JavaScript
  import default timer;
```

### Creating a new function `getTimesPart()`, that will calculate seconds, minutes, hours and days:

```JavaScript
  const getTimesPart = (endtime) => {
        const t = Date.parse(endtime) - Date.parse(new Date()); // We calculate the number of milliseconds(The difference between the deadline and the current date, everything is                                                                    calculated in milliseconds)

        const seconds = Math.floor((t / 1000) % 60),
              minutes = Math.floor((t/1000/60) % 60),
              hours = Math.floor((t/(1000 * 60 * 60)) % 24),
              days = Math.floor((t / (1000 * 60 * 60 * 24)));

        return {              // Returning an object with data
            'total': t,
            'seconds': seconds,
            'minutes': minutes,
            'hours': hours,
            'days': days
        }
    };
```
