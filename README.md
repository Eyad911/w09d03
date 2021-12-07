

# About The Project:

 We taking everything we have learned into one web application, setting up the front end and back end with mongo db 

 **Here are the requirements:**
1. **Backend**
 - Bild our server
 - Connect our server with DataBase (mongo)
 - Start make our Schemas
 - Create our Controllers
 - Test All your Routs
 2. **Frontend**
 - Create React App
 - Create our Components
 - Create our Reducers
 - Test The web app
 


# Functionalities in the website:

1. Register 
2. LogIn
3. **Todo List:**
- Add new Task
- Read new Task
- Edit Task
- Delete Task (Soft Delete)


# Tools used:
**Frontend**
1. **React**: To add Functionalities to my project.
2. **Trello**: Project management tool to orgnize the time 
and work.

**Backend**
1. Postman: To test our Routers



# Library That I Use:

```js
    axios: "^0.24.0",
    react: "^17.0.2",
    react-dom: "^17.0.2",
    react-router-dom: "^6.0.2",
    
    react-redux: "^7.2.6",
    redux: "^4.1.2",
    redux-devtools-extension: "^2.13.9",

```


# Components in the website:

1. Register 
```js
const signUp = async () => {
    const result = await axios.post(`${BASE_URL}/signUp`, {
      email,
      password,
      role,
    });
    console.log(result.data);
    navigate("/login")
  };
```
2. LogIn
```js
const logInB = async()=>{
    const result = await axios.post(`${BASE_URL}/login`,{
       email,
       password,
    
    });
    const data = {
      user: result.data.result,
      token: result.data.token,
    };
    dispatch(login(data));
    
    localStorage.setItem("token", result.data.token);

     navigate('/tasks')
}
```
3. Tasks:

- Get Tasks
```js
const getTask = async () => {
    const result = await axios.get(`${BASE_URL}/gettasks`, {
      headers: {
        Authorization: `Bearer ${local}`,
      },
    });
    dispatch(readTask({ task: result.data }));
    setTasks(result.data);
  };
```
- Add Tasks
```js
const addTask = async () => {
    await axios.post(
      `${BASE_URL}/task`,
      {
        task: task,
      },
      {
        headers: {
          Authorization: `Bearer ${local}`,
        },
      }
    );
    dispatch(createTask({ task }));
    getTask(local);
  };
```
- Edit Tasks
```js
const updateTask = async (id) => {
    await axios.put(
      `${BASE_URL}/edittask/${id}`,
      {
        task: task,
      },
      {
        headers: {
          Authorization: `Bearer ${local}`,
        },
      }
    );
    getTask(local);
  };
```
- Delete Tasks
```js
const deleteTask = async (id) => {
    await axios.delete(`${BASE_URL}/delete/${id}`, {
      headers: {
        Authorization: `Bearer ${local}`,
      },
    });
    getTask(local);
  };
```




# Links:

1. Link of Trello board => https://trello.com/b/tKZzEVbO/project-2

2. My github Page => https://github.com/Eyad911





