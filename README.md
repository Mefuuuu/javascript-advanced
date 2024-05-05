# 1. What is Async Javascript?

![image](https://github.com/Mefuuuu/javascript-advanced/assets/133778142/f71f431b-9220-4919-951d-012e16e4161b)

# 2. HTTP Requests ( Tạo Request Với JavaScript Thuần)

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

# 3. Status Codes (Trạng Thái Của Request)

![image](https://github.com/Mefuuuu/javascript-advanced/assets/133778142/5cef0b28-c414-4fb8-a498-f03a9f8f4a00)

# 4. Callback functions (Khi Cần Thì Gọi Lại)

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

# 5. Using JSON data (Đọc File JSON Với Javascript Thuần "Chủng")

Để giao tiếp giữa sever và client

```c
JSON.parse()         //convert text to JSON
JSON.stringify()     //convert JSON to string
```

# 6. Callback Hell

![b8euo2n7twvgh3dbuatd](https://github.com/Mefuuuu/javascript-advanced/assets/133778142/3a496e8e-6ef2-456f-a35f-62c37ca737f1)

# 7. Promises (Lời Hứa Để Giải Quyết Callback)

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


# 8. Chaining Promises (Promise Lồng Trong Promies)

Tránh lặp như Callback Hell

```c
getTodos(1)
        .then(data => {
            console.log('>> get data: ', data)
            return getTodos(2)

        })
        .then(data2 => {
            console.log('>>get data2: ', data2)
            return getTodos(3)

        })
        .then(data3 => {
            console.log('>> get data3: ', data3)
        })
        .catch(err => {
            console.log('>>>', err)
        })
```

# 9. The Fetch API (GET Data Từ API Siêu Đơn Giản)

Có thể thay cho XMLHttpRequest để gọi API

```c
    fetch('https://jsonplaceholder.typicode.com/todos/1')
        .then(Response => {
            return Response.json()
        })
        .then(data => {
            console.log('>>> check fetch data: ', data)
        })
```

# 10. Async & Await (Xử Lý Bất Đồng Bộ Sao Dễ Vậy)

ES7

Async - khai báo một hàm bất đồng bộ
Await - tạm dừng việc thực hiện các hàm async.

```c
const getNewToDo = async (id) => {
        let response = await fetch(`https://jsonplaceholder.typicode.com/todos/${id}`);
        let data = await response.json();
        return data;
    }

    getNewToDo(2).then(data => {
        console.log('>> check get data: ', data)
    })
```

# 11. Throwing Errors (Xử Lý Lỗi Với Javascript)

Convert json không ra kết quả lúc đó cần xử lý lỗi

```c
const getNewToDo = async (id) => {
        let response = await fetch(`https://jsonplaceholder.typicode.com/todos/${id}`);
        if (response && response.status !== 200) {
            throw new Error('Something wrongs with status code: ' + response.status)
            // reject
        }
        let data = await response.json();
        return data; //resolve
    }
```

hoặc dùng Error message

```c
...
    getNewToDo('asd12')
        .then(data => {
            console.log('>> check get data: ', data)
        })
        .catch(err => {
            console.log('>>> check error: ', err.message)
        })
```

hoặc dùng Try and Catch

```c
    const getNewToDo = async (id) => {
        try {
            let response = await fetch(`https://jsonplaceholder.typicode.com/todos/${id}`);
            if (response && response.status !== 200) {
                throw new Error('Something wrongs with status code: ' + response.status)
                // reject
            }
            let data = await response.json();
            return data; //resolve
        } catch (e) {
            console.log('>>> check catch error', e.message)
        }
    }

    getNewToDo('asd12')
        .then(data => {
            console.log('>> check get data: ', data)
        })

```

# 12. Destructuring assignment (Toán Tử 3 Dấu Chấm - Giản Lược Hóa Cùng Destructuring Assignment)

... như là 1 phép tính cộng

```c
let a, b, rest;
[a, b] = [10, 20];

console.log(a);
// Expected output: 10

console.log(b);
// Expected output: 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest);
// Expected output: Array [30, 40, 50]
```

Cách viết biến ngắn gọn:

```c
    let state = {
        name: 'Mefu',
        address: 'hcm',
        channel: 'vinhky'
    }

    let { name, address, channel } = state;

    console.log('check key: ', name, address, channel)
// Expected output: >>> check data arr1:  {name: 'Mefu', address: 'hcm', channel: 'vinhky'}
```

```c
    let arr = ['Mefu', 'vinhky1'];
    let [name, channel] = arr;
    console.log('>>> check key: ', name, channel)
// Expected output: >>> check key:  Mefu vinhky1
```
