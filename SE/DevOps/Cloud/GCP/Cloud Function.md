- Serverless paradigm
- Handles incoming requests by assigning them to instances of your function.
- 2 generation 1st gen, 2nd gen
[Tips & Tricks  |  Cloud Functions Documentation  |  Google Cloud](https://cloud.google.com/functions/docs/bestpractices/tips)
### 1st gen
- Use the typical serverless functions architecture
- One function instance can handle one request at specific point in time
### 2nd gen
- New version built on top of Cloud Run and Eventarc
- 1 function instance handle multiple requests at the same time

### Deploy Google Function
- GCP Console (UI)
- gcloud (cli)
- git (Terraform)
- Gcloud CLI
    ```jsx
    // deploy function 
    gcloud functions deploy hello-node-function \\
      --gen2 \\
      --runtime=nodejs20 \\
      --region=REGION \\  REGION = us-west1
      --source=. \\
      --entry-point=helloGET \\
      --trigger-http \\
      --allow-unauthenticated
    
    // describe function 
    gcloud functions describe hello-node-function \\
        --region=REGION
    
    // visit URL 
    curl FUNCTION_URL
    
    // delete 
    gcloud functions delete nodejs-http-function --gen2 --region REGION
    
    // call API
    curl -m 70 -X POST URI \\
        -H "Authorization: Bearer $(gcloud auth print-identity-token)" \\
        -H "Content-Type: application/json" \\
        -d '{}'
    ```

A new function instance is started in two cases:
- When you deploy your function.
- When a new function instance is automatically created to scale up to the load, or occasionally to replace an existing instance.

Starting a new function instance involves loading the runtime and your code.
Requests that include function instance startup, called _**cold starts**_, can be slower than requests routed to existing function instances. If your function receives steady load, however, then the number of cold starts is typically negligible unless your function frequently crashes and requires restarting of the function environment.
### Function scope versus global scope
A single function invocation results in execution of only the body of the function declared as the entry point. The global scope of your function source code is only executed on cold starts, and not on instances that have already been initialized

```jsx
const functions = require('@google-cloud/functions-framework');

// TODO(developer): Define your own computations
const {lightComputation, heavyComputation} = require('./computations');

// Global (instance-wide) scope
// This computation runs once (at instance cold-start)
const instanceVar = heavyComputation();

/**
 * HTTP function that declares a variable.
 *
 * @param {Object} req request context.
 * @param {Object} res response context.
 */
functions.http('scopeDemo', (req, res) => {
  // Per-function scope
  // This computation runs every time this function is called
  const functionVar = lightComputation();

  res.send(`Per instance: ${instanceVar}, per function: ${functionVar}`);
});
```

- You can assume that for each function instance, the global scope has been executed exactly once before your function code is invoke (gọi)
- Therefore, you should always signal the end of your function execution correctly and avoid running any code beyond it. See HTTP Functions, Background Functions, and CloudEvent Functions for guidance.
- Các tác vụ nền không nên được tạo trong phạm vi toàn cục trong quá trình khởi tạo, vì chúng sẽ thực thi ngoài khoảng thời gian của yêu cầu.

### Execution guarantees
- Các hàm thường được gọi 1 lần cho mỗi sự kiện đến
- Không đảm bảo 1 lệnh được gọi duy nhất trong mọi TH do có sự khác biệt trong tình huống lỗi
- The maximum or minimum number of times your function could be invoked for a single event depends on the type of your function:
    - HTTP functions are invoked at most once. This is because of the synchronous nature of HTTP calls
    - Event-driven functions are invoked at least once. This is because of the asynchronous nature of events, in which there is no caller that waits for the response.