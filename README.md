# 1. What is Async Javascript?

![image](https://github.com/Mefuuuu/javascript-advanced/assets/133778142/f71f431b-9220-4919-951d-012e16e4161b)

# 2. HTTP Requests

```c
var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState === 4) {
       // Typical action to be performed when the document is ready:
       console.log('>>> check res: ', xhttp.responseText);
    }
};
xhttp.open("GET", "https://jsonplaceholder.typicode.com/todos/1", true);
xhttp.send();
```

# 3. Status Codes

![image](https://github.com/Mefuuuu/javascript-advanced/assets/133778142/5cef0b28-c414-4fb8-a498-f03a9f8f4a00)

# 4. Callback functions

```c
const callback = (error, data) => {
        if (error) {
            console.log('>>> calling callback with error: ', error)
        }
        if (data) {
            console.log('>>> calling callback with data: ', data)
        }
    }
```

# 5. Using JSON data

Để giao tiếp giữa sever và client

```c
JSON.parse()         //convert text to JSON
JSON.stringify()     //convert JSON to string
```

# 6. Callback Hell

![b8euo2n7twvgh3dbuatd](https://github.com/Mefuuuu/javascript-advanced/assets/133778142/3a496e8e-6ef2-456f-a35f-62c37ca737f1)

# 7. Promises

Giải quyết sự bất đồng bộ của JS
```c
    // Promise example

    const promiseExp = () => {

        return new Promise((resolve, reject) => {
            // resolve({name: 'Mefu', channel:'vinhky'});
            reject('something wrongs')
        });
    }

    promiseExp()
        .then(data => {             // .then with success
            console.log(data)
        })
        .catch(data => {            // .catch with wrongs
            console.log(data)
        });

```


# 8. Chaining Promises
# 9. The Fetch API
# 10. Async & Await
# 11. Throwing Errors
# 12. Destructuring assignment
