# Full Stack Todo List

Este ejercicio está dividido en dos fases:

1. Back-End: CRear un API de TODO list o lista de tareas.

2. Front-End: Crear una app HTML/CSS/JS.

![Exercise diagram](https://github.com/breatheco-de/full-stack-todo-list/blob/master/diagram.png?raw=true)

Si ya hiciste el front-end o back-end en algún ejercicio previo ( o algo similar) puedes copiar y pegar tu código dentro de este boilerplate y adaptarlo para que funcione, aprenderás mucho haciéndolo.

## 🌱  Cómo iniciar el proyecto

No clones este repositorio. El primer paso para comenzar a codificar es clonar el [vanillajs + flask boilerplate](https://tinyurl.com/yfj4grel):

a) Si usas Gitpod (recomendado) puedes clonar el boilerplate [haciendo clic aquí](https://tinyurl.com/yfj4grel).

b) Si trabajas localmente, escribe el siguiente comando en tu terminal: 
```sh
$ git clone https://tinyurl.com/yfj4grel
```

💡 Importante: Recuerda actualizar el `remote` del proyecto con el de tu repositorio usando `git remote set-url origin <your new url>`, y luego guardar tu código en tu nuevo repositorio usando `add`, `commit` y `push`.

## 📝 Instrucciones para el Back-end 

Añade los endpoints para crear una tarea, eliminarla y obtener (get) todas las tareas. Implementa los siguientes endpoints.

`[GET] /todos` Obtén la lista de todo's o tareas. 
`[POST] /todos` Añade un todo o tarea a lista.  
`[DELETE] /todos/<int:position>` Borra un todo o tarea, según su posición.
  
## 📝 Instrucciones para el Front-end 

Crea tu App HTML/CSS/JS que le permita a cualquier usuario manejar una todo list o lista de tareas. 
- Listar todos los todos o tareas.

- Agregar un todo o tarea

- Eliminar todo o tarea cuando se haga clic en el icono de la basura.

## Pasos sugeridos para completar este proyecto.

### Muestra/Render los todos o tareas

1. Crea el diseño HTML/CSS para la todo list o lista de tareas, puedes tomar [prestado este código](https://codepen.io/alesanchezr/pen/zYrOPbM) si quieres, pero tendrás que entenderlo para poder usarlo correctamente. Tu lista de todos o tareas debe verse similar a esta: 

![Todo List Zoomed Out](https://github.com/breatheco-de/full-stack-todo-list/blob/master/todo-zoom-out.png?raw=true)

🤘🏼 Nota: Si te sientes seguro, puedes crear tu propio diseño. 

2. Una vez terminado el HTML y CSS intenta crear una función `function addTodo(title)` dentro de tu archivo `src/front/js/index.js` que reciva el título de la tarea y le añada un nuevo item a la lista de todos o tareas. Te recomendamos usar la función del DOM [appendChild](https://www.w3schools.com/jsref/met_node_appendchild.asp) para crear un nuevo item dentro de la lista de todos o tareas, puedes llamar a la función tu mismo para ver si funciona.

⚠️ Importante: Cada tarea debe tener un icono de la basura que se muestra cuando haces "hover" en la tarea o todo. 

3. Usando la [Fetch API](https://content.breatheco.de/lesson/the-fetch-javascript-api) en tu archivo `src/front/js/index.js` escribe un FETCH dentro de window.onload para obtener todos los todos o tareas de la API: `GET /todos`.

Recuerda que de acuerdo a la fetch API, fetch debe recibir dos funciones, una para el `.then()` y una para el `.catch()`. Esas funciones serán llamadas dependiendo de si la solicitud fue exitosa o falló.

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

4. Una vez que fetch get all haya terminado, deberías mostrar las tareas o todos en HTML eliminando los items dentro de la lista y llamando la función `addTodo` cuantas veces sea necesario.

### Eliminar un todo o tarea

5. Para implementar delete: En tu archivo `src/front/js/index.js`, crea una función llamada `deleteTask` que será llamada cada que se haga clic en algún icono de la basura. 

![Single Task](https://github.com/breatheco-de/full-stack-todo-list/blob/master/delete-task.png?raw=true)

5.1 Se llama a la función con onClick en el icono de la basura.

5.2 La función recibe un parámetro `e` que contiene la información del evento, siendo `e.target` el icono de la basura al cual se le hizo clic. 

5.3 Usando la fetchAPI, la función debe hacer una solicitud DELETE a tu API: `DELETE /todo/<int:position>`

### Añadir un todo

Esta función se activa después de que el usuario escribe el título de la tarea en el `<input>` ubicado en la parte superior de la lista, y luego el usuario hace clic en el botón `agregar` al lado de la entrada o input.

6. Agrega un listener onCLick al botón añadir que llama a una nueva función `createTodo`.

6.1 En tu `src / front / js / index.js` declara una función` createTodo` que reciba `e` como parámetro con la información del evento.

6.2 Usa la función document.querySelector para seleccionar la entrada del DOM y obtener su valor (el valor de entrada será lo que el usuario haya escrito como título de la tarea).

6.3 Almacena ese valor en una variable.

6.4 Utiliza la fetch API para crear un `POST / todo` y agrega el título de la tarea como el body de la solicitud con el tipo de contenido json.

6.5 Espera a que vuelva la respuesta usando el `.then ()` y `.catch ()` disponibles.

6.6 Si la respuesta llega al .then,  verifica el código de estado.

6.7 Si el código de estado es 200, llama a la función `addTodo` que declaraste en el segundo paso, esa función agregará la tarea a la lista de elementos HTML.

## 😎 ¿Te sientes seguro?

- Implementa un método para marcar los todos como hechos, agrega un segundo botón al lado de la papelera para marcar la tarea como leída, cuando la tarea esté marcada como leída, puedes usar la propiedad CSS line-through.
 
- Implementa un método para actualizar el título de todo o tarea, tendrás que agregar un nuevo endpoint en tu API para `PUT / todo / <int: position>` y una función javascript `updateTodo` en tu` index.js` que se llama luego se edita un TODO o tareas. Puedes agregar un ícono de lápiz que cuando el usuario haga clic en él, reemplaza el elemento del todo o tarea con una entrada de texto que el usuario puede escribir en él.

