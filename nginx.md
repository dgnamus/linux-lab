It's an HTTP server that can also serve as a proxy server. 
What can a proxy server do?

- It can do load balancing
- It can do caching so that a website doesn't have to be retrieved from the server + database every time
- It can serve as a single entry point, protecting the servers from outside traffic. Instead of having to ensure safety of each and every server, we concern ourselves with the entrypoint
- Can compress the response. For example, Netflix sends over chunks (streaming) of compressed video

We configure it to do what we want it to do in nginx.conf file. For example, we can specify as a good practice to redirect all HTTP requests on port 80 to HTTPS on port 443. 

Nginx is also used as an K8 Ingress controller on Kubernetes to manage traffic, but this is the internal load balancer inside the Kubernetes cluster, we need to use a separate one as an entry point from the internet (like dedicated load balancers from AWS or Azure).
