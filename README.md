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
  // We calculate the number of milliseconds(The difference between the deadline and the current date, everything is                                                          calculated in milliseconds
  
        const t = Date.parse(endtime) - Date.parse(new Date());

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

### Creating a new function `setClock()`, which will substitute values in the HTML code:

```JavaScript
  const setClock = (selector, endtime) => {
  // getting the elements from page
  
        const timer = document.querySelector(selector),
              seconds = timer.querySelector('#seconds'),
              minutes = timer.querySelector('#minutes'),
              hours = timer.querySelector('#hours'),
              days = timer.querySelector('#days'),
              timeInterval = setInterval(updateClock, 1000); //Creating function, which will substitute values every second

        function updateClock() {
        // getting in variable functions`s value (object with data)
            const t = getTimesPart(endtime); 
            
//The following paragraph describes the function addZero()

            seconds.textContent = addZero(t.seconds);
            minutes.textContent = addZero(t.minutes);
            hours.textContent = addZero(t.hours);
            days.textContent = addZero(t.days);

// We check if the difference is less than 0, then we stop the interval and set the timer to 0 
            if (t.total < 0) {
                seconds.textContent = '00';
                minutes.textContent = '00';
                hours.textContent = '00';
                days.textContent = '00';
    
                clearInterval(timeInterval);
            }
        }

// Calling the function
        setClock(id, deadline);
    };
```

### Auxiliary function `addZero()`:

```JavaScript
// If the input value is less than 10 (seconds, minutes, hours, or days), the function returns a string with 0 before the input value, otherwise it returns just the input value
      function addZero(num) {
        if (num < 10) {
            return '0' + num;
        } else {
            return num;
        }
    }
```


