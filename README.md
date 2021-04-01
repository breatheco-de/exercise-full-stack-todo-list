# Full Stack Todo List

This exercise is divided in two main phases: 

1. Back-End: Building a todo list API.
2. Front-End: Creating a HTML/CSS/JS app.

![Exercise diagram](https://github.com/breatheco-de/full-stack-todo-list/blob/master/diagram.png?raw=true)

If you already did the front-end or the back-end phase in a previous exercises (or something similar) you can copy & paste your code into this boilerplate and adapt it to make it work, you will still learn a lot by doing that.

## 🌱  How to start this project

Do not clone this repository.

The first step to start coding is cloning the [vanillajs + flask boilerplate](https://tinyurl.com/yfj4grel) on your local computer or opening it using gitpod.

a) If using Gitpod (recommended) you can clone the boilerplate by [clicking here](https://tinyurl.com/yfj4grel).

b) If working locally type the following command from your command line: 
```sh
$ git clone https://tinyurl.com/yfj4grel
```

💡 Important: Remember to create a new repository, update the remote (`git remote set-url origin <your new url>`), and upload the code to your new repository using `add`, `commit` and `push`.

## 📝 Back-end Instructions

Add the endpoints to create one task, delete one task and get all tasks. Implements the Following Endpoints.

`[GET] /todos` Get the list of todo's.  
`[POST] /todos` Add a new todo to the list.  
`[DELETE] /todos/<int:position>` Delete a single todo, given it's position.  
  
## 📝 Front-end Instructions

Create a HTML/CSS/JS app that allows any user to manage a todo list: 
- List all the todos.
- Add a new todo.
- Delete a todo when clicking on the todo trash icon.

## 🤗 Suggested steps to complete this project

### Show/Render the todos

1. Create the HTML/CSS design for the todo list, you can [borrow this code](https://codepen.io/alesanchezr/pen/zYrOPbM) if you like, but you will have to understand it perfectly to be able to use it properly. You todo list needs to look similar to this:

![Todo List Zoomed Out](https://github.com/breatheco-de/full-stack-todo-list/blob/master/todo-zoom-out.png?raw=true)

🤘🏼 Note: You can create your own design if you are feeling confident.

2. Once you finished the HTML and CSS try creating a `function addTodo(title)` inside of your `src/front/js/index.js` that receives the task title and appends a new item to the list of todos. It's recommended to use the DOM [appendChild function](https://www.w3schools.com/jsref/met_node_appendchild.asp) to create the new item inside the list of todos, you can try calling the function yourself and see if it works.

⚠️ Important: Each task must contain a trash icon that shows when the task is hovered.

3. Using the [Fetch API](https://content.breatheco.de/lesson/the-fetch-javascript-api) on your `src/front/js/index.js` write a fetch call inside the window.onload to get all the todos from the API: `GET /todos`.

Remember that according to the fetch API, the fetch function must receive two functions, one for the `.then()` and one for the `.catch()`. Those functions will be called depending on the request successfull completition or failure

```js
fetch('url', options)
  .then(response => {
    if(response.status == 200) return response.json();
  })
  .then(response => {
    // successfully completed, you should call the addTodo function here.
  })
  .catch(error => console.log("Error fetching todos:", error));
```

4. Once the fetch to get all the todos is finished you should render the todos in HTML by deleting all the items inside the list and calling the function `addTodo` as many times as needed.

### Delete one todo

5. To implement the delete feature: On your `src/front/js/index.js`, create a function called `deleteTask` that will be called when any trash icon is clicked.

![Single Task](https://github.com/breatheco-de/full-stack-todo-list/blob/master/delete-task.png?raw=true)

5.1 The function gets called onClick on the trash can icon.
5.2 The function receives one parameter `e` that contains the event information with `e.target` being the trash can that was clicked.
5.3 Using the fetchAPI the function must do a DELETE request to your API: `DELETE /todo/<int:position>`

### Add one Todo

This feature is triggered after the user types the title of the todo into the `<input>` located at the top of the list, and then the user clicks on the `add` button beside the input.

6. Add an onClick listener to the add button that calls a new function `createTodo`.
6.1 On your `src/front/js/index.js` declare a function `createTodo` that recives `e` as a parameter with the event information.
6.2 Use the document.querySelector function to select the input from the DOM and get it's value (the input value will be whatever the user typed as the todo title).
6.3 Store that value in a variable.
6.4 Use the fetch API to to create a `POST /todo` and add the task title as the body of the request with content-type json.
6.5 Wait for the response to come back by using the `.then()` and `.catch()` available.
6.6 If the response lands on the .then check for the status code.
6.7 If the status code is 200 call the function `addTodo` that you declared on the second step, that function will append the todo into the list of HTML items.


## 😎 Feeling confident?

- Implement a method to mark the todos as done, add a second button beside the trash can to mark the task as read, when the task is marked as read you can use the line-through CSS property.
- Implement a method to update the todo title, you will have to add a new edpoing on your API for `PUT /todo/<int:position>` and a `updateTodo` javascript function on your `index.js` that gets called then a TODO is edited. You can add a pencil icon that when the user clicks on it it replaces the todo element with a text input that the user can write on it.
