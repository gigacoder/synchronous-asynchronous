# Javascript synchronous-asynchronous explained with examples
JavaScript itself is synchronous and single-threaded language. but you can write code in such a manner that function execution take a long time and can be interleaved with other operations.

First, let us use a analogy to understand Synchronous and Asynchronous.

**Synchronous -** You are in a Bus stop. When bus arrived, people will enter in a bus one by one. You cannot get into the bus until everybody in front of you gets in. and the same concept applies to the people standing behind you. This is Synchronous.

Executing something **synchronously** means, you wait for the task to finish before moving on to another task. Or we can say, two synchronous threads must be aware of one another, and one must execute in some way that is dependent on the other.


**Asynchronous -** Take household chores as an example. You put clothes to get washed and dry in a washer and dryer. Then you bake pizza in a oven. Meanwhile you are cutting veggies for salad. In this situation, couple of tasks are getting done at the same time. When the task is done. It will simply report back. This is asynchronous.

Executing something **asynchronously** means, you can move on to another task without waiting for the first task to get finished. The result of each task will be handled once the result is available. Or in other words, Asynchronous means two threads are totally independent, run parallely and neither one comes in each other way at the time of execution.

![synchronous-asynchronous-javascript](https://cloud.githubusercontent.com/assets/10238874/24230796/2143129e-0f3e-11e7-8205-02abf87a3557.png)

Try this code 

```
// synchronous
console.log('First Task');
console.log('Second Task');
console.log('Third Task');
```
**Output will be :-**

First Task

Second Task

Third Task

The output will be First Task, Second Task, Third Task. As javascript execute one function at a time and will wait for the function to be done before moving to the “Second Task”

Now try this code. I am using **setTimeOut method** here. The function will be processed in the background, while your program is doing other things.
```
// asynchronous
console.log('First Task');
setTimeout(function(){
   console.log('Second Task');
}, 2000); 
console.log('Third Task');
```
**Output will be :-**

First Task

Third Task

Second Task

The **setTimeout()** method calls a function or evaluates an expression after a specified number of milliseconds. The setTimeout() method is asynchronous as it breaks the synchronous flow. This trick is used to execute the code after stacked events and fix timing-related problems.

**AJAX (Asynchronous JavaScript and XML)** requests are by default asynchronous, The XMLHttpRequest object is used to exchange data with a server behind the scenes. When the browser makes server requests. The response could take a little time. So you set up a function that will wait for the response to be sent back by the server, and react to it once the response is available. This whole process does not comes in the way of other functions.


![ajax-asynchronous](https://cloud.githubusercontent.com/assets/10238874/24230934/f3be36fe-0f3e-11e7-9a34-b79713cd33cb.png)

```
 var xhttp;
      if (window.XMLHttpRequest) {
        // code for modern browsers
        xhttp = new XMLHttpRequest();
      } else {
        // code for old browsers (IE6, IE5)
        xhttp = new ActiveXObject("Microsoft.XMLHTTP");
      }
      xhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
          document.getElementById("ajax_demo").innerHTML = this.responseText;
        }
      };
      xhttp.open("GET", "fruits.txt", true);
      xhttp.send();
      xhttp.onload = function(){
        document.write(this.response);
      };
```

