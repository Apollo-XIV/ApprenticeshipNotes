This brief describes the Architecture and Layout of the application. This is not an exhaustive document, but should hopefully provide plenty of clarification on what exactly we'll be doing. There is also some example code that should help explain.

# Architecture
"Architecture" describes the logical layout of the WebApp, this means, what are the individual parts of the service and how do they fit together, what relationships do they have, how does they communicate.

A monolith architecture tends to be outdated (there is exception to this! just not necessarily important right now). A monolith is where all parts of a service and/or webapp are hosted on the same server. A more modern approach is the three-tier architecture. This is where the system is seperated into three layers:
- Presentation Layer
- Logic Layer
- Data Layer
The presentation layer is how the end-user views the app itself. It can be in charge of many things, but primarily its responsibility is rendering web-pages and routing a client.

The Logic layer acts as an abstraction for the data layer beneath it, this is typically in the form of an **API**. An API is a set of URIs that when a request is made to them runs a function and maybe returns a value. The logic layer is interposed between the Presentation and Data layer as they Logic layer can provide a predetermined set of routes for accessing the data in the database, as well as doing authentication on any users trying to access the data. This means the Presentation layer can make requests to the Data Layer *through* the Logic Layer.

For a, perhaps, more easy to understand comparison, if our webapp was a restaurant then our presentation layer might be the customer. The kitchen is our data layer, and then our logic layer is the waiting staff. The "waiter" acts as a buffer and makes sure the "customer" doesn't go into the kitchen themselves and start cooking random ingredients (in this example, that'd be like giving the end-user direct access to the database, to query how they please, giving essentially no data-security).

Lastly, is the Data-Layer. This is where we store any data for our service. This can be in a structured form such as a relational database, or a more loosely structured database such as a NoSql database (like mongodb).

Now, you have a relatively accurate understanding of *what* 3-tier architecture is, now lets look at *why?* We have two primary reasons for 3-tier architectures:
- **Scaling.** Scaling may seem an unnecessary concern for a project of our size, however, as aspiring DevOps engineers considering scaling should always be *somewhere* on our list of priorities. By dividing the codebase up into pieces we can scale each part independently, scaling to their own individual demands.
- **Seperation of Concerns.** This means organising your code by not just what it does but what its related to. This essentially means just keeping things tidy and organised, i.e., a frontend server should only be running frontend services, and not have scraps of code from other parts of the project lying around. This makes a service not only easier to develop, but easier to use and anticipate.

This is the traditional configuration of services. In our case, to make our lives easier, we're using a Backend-as-a-Service (BaaS). This essentially combines those last two layers into one. It provides a common set of commands and functions that can be used to interract with the backend which makes development simpler and easier. We'll look more at what this means later.

For our architecture we will likely have two VMs, on which we'll likely be running up to three containers each:
- ***VM1***: Frontend Client - Nextjs 13. This is the server users will be directed to, it's where they can view resources, use the app itself, and more. This server will also need a reverse proxy for HTTPS, which will be provided through another docker container. We can use docker compose to create these two containers on the machine and have them talk to each other.
- ***VM2*** (Optional: use the hosted version of the software instead, reducing complexity):  Database & Backend - Supabase.

# Examples
Let's look at how these ideas actually work in practice.

## Full Data-journey
For our first example, lets think about a user visiting the website to see what courses we have available.
```
-> user types DevNexus.com into a searchbar
-> their PC queries a DNS server (cloudflare) which then redirects the traffic to our Frontend server which runs NextJS.
-> once we have the request on the frontend server, NextJS looks at the path of the URL and decides how to route it. It checks the associated file that renders that particular route, and runs the code within before sending it to the client (This is called server-side rendering).
-> Before the page is sent, it needs to find out what courses are currently on offer. To do this it sends a request to the backend API via a URL, or, more simply, via a preconfigured SDK like supabase's.
-> The request is sent to Supabase, that then takes the request and makes sure it's credible, checking it came from the right place, the user has appropriate permissions, and so on, before querying the database and returning the data to the client.
-> In this case, the client is the frontend server, however, it can also be the user if the webapp makes any requests later on.
```

With NextJS, our javascript will run on both the server and user's computer, however, with an API we know for a fact it will only ever run on the server. This means we don't have to worry about user performance or any other external variables, only whether they have an internet connection. 


## Sample Code
With Supabase, what does our code actually look like? Below is the code to query the database for all available courses, via the supabase SDK.
```javascript
import {supabase} from '@assets/modules/supabase';

const allCourses = await supabase.from('courses').select();
```

This code imports a client object which avoids us repeating the same code in every function. Then, we can simply call functions on the client to get different results. In this case, just like in an SQL statement, we are selecting all the records from the table 'courses' (select all because the parameters were left blank).

## Customising Supabase
Having a backend service premade is great until you need to change something. For example, how would we add our own custom backend API routes? It's easier than you think! To do this we simply create a "serverless function" or "edge function". Writing an edge function is almost identical to writing a regular function in javascript. Calling these functions is even easier. Let's say we have a delete account button on the client, and in our backend we've created an edge function called "deleteUser". To call this function we simply do:
```javascript
import {supabase} from '@assets/modules/supabase';

supabase.functions.invoke("deleteUser").then({
	console.log("Function completed runnning");
});
```

This might look a little suspicious, how on earth will my backend function know which user to delete! Well, one of the amazing things about the supabase cli is that as part of calling the function, when the actual HTTP request is sent, authorisation headers are attached meaning without having to tell it to, Supabase knows who's asking for their account to be deleted and can check whether that's something they're allowed to do.
