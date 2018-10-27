1. Sending HTTP requests options
  - React is just a JavaScript UI library that doesn't come with HTTPModule, unlike Angular. Options:
    1. Fetch API - a native way, already implemented in all modern browser
    2. jQuery AJAX
    3. Axios - popular library, npm i axios@0.18


2. cdm - where to call server() for initialization

3. CRUD operations: async/await

    1. GET:
          const response = await axios.get('https://jsonplaceholer.typicode.com/posts'); //store it in apiEndpoint var
          response.data holds the info;

    2. POST:
          axios.post(apiEndpoint, obj); //response.data

    3. UPDATE:
          axios.put(apiEndpoint + '/' + post.id, obj): update all properties, send with entire object
          axios.patch(apiEndpoint..., {title: obj.title}): update one or more properties, send with selected properties

    4. DELETE:
          axios.delete(apiEndpoint + '/' + post.id);

4. Optimistic vs Pessimistic Updates
  - Optimistic: Assuming the ops always succeed. Make a copy of the old state. Change the UI immediately then make server calls. If server call fails, revert the UI
  - Pessimistic: Only proceed to change the UI if server call succeeded


5. Expected vs Unexpected Errors
  - Expected errors: API endpoint predict and report - display a specific error message.
    ex. (404: not found, 400: bad request) - client errors
  - Unexpected errors: technically should not happen under normal circumstances. We need to log them, display generic and friendly error message to the user
    ex. network/server/db down

6. Inteceptor in Axios: intercept req/res. Takes two function parameters, one called when success, one when error occurs. Or pass in null if you dont want to do anything
    axios.interceptors.request.use(success, error)
    axios.interceptors.response.use(success, error)

    - error function will be executed and the control will be passed to catch block

7. Toast Message
    - npm i react-toastify@4.1     
      import { ToastContainer }  from 'react-toastify';    //app.js
      import 'react-toastify/dist/ReactToastify.css';
      <ToastContainer />

    - import { toast } from 'react-toastify';
      - use is as an object
        toast.error('Error message');
        toast.success();
        toast.info();
      - or call it as a function. Because in JavaScript, functions are objects
        toast('Message');

8. Logging Service - Sentry.io & Raven
    - npm i raven-js@3.26.4
      import Raven from 'raven-js';    //index.js
      Raven.config(...)                //from sentry website

    - import Raven from 'raven-js';
      Raven.captureException(error);




  - [[]] double brackets is internal property cannot get with .
  - we get the posts from server, also storing it in the state as an array. Maintaining the consistency between state and server in every CRUD options
  - request: option will appear whenever the backend and db server are not at same domain
  - crud operations -> update ui
  - index.js: high level module, responsible for bootstraping application. Manager
