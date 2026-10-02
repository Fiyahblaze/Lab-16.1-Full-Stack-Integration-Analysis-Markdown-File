Mark Down
Cors Error Explained - A cors error is something that happens when react gets blocked by the browser from reading a response from different servers, that usually happens because your server didnt provide the right or required permission. origins in react include protocol, hostname, and port. so if your running your mern app on localhost:3001 and express on localhost:3000 even if their on the same computer their ports make them two different origins so you will get a cors errors.
solution 1- A development proxy server, make react send request from the development server then which it will forward them to express.
solution 2- Add some cors middleware in express. to allow request from the devlopment server this should allow direct communication. 

Environment Management Explained - Hardcoding api url's is when you put a fixed server address directly into your react code. It's bad practice because its hard to maintain the address used because the local development address and the address after deployment is usually different.
Environments configuration make all the values seperate in the application logic
.env defines the REACT_APP_API_URL file and the application will read process.env.REACT_APP_API_URL.
vite does the same Vite using VITE_API_URL and the application reads imports import.meta.env.VITE_API_URL.
On the Express server, the dotenv package loads .env values into process.env

Data Fetching Trade-offs- To me Axios is for more complicated projects but one key advantage of Axios versus the native fetch API is its built-in interceptors. Interceptors let developers apply shared behavior before requests are sent or when responses return. so you could use Axios on small projects too its just the features become more useful as the application grows
For example, if your application has alot of pages that need protecting, you could use a request interceptor to attach a login token to API requests, and then a response interceptor could handle expired login errors consistently. This will reduce repeating your code and makes request behavior easier to maintain across a very complex application.
But you could also do the same thing with a custom wrapper around fetch.
so trade-offs on both are Axios adds a dependency and fetch is already built in the browser.