Creating a docker-compose for "Food Trucks"
2 minute read
Food Trucks is a two-tier web application:

Data about food trucks in SF (San Francisco) is stored in ElasticSearch.
A web application shows this data based on Python/Flask.

This application needs `python2`, `pip` and `npm`.
Note that `python2` is supported only up to Alpine version 3.11!
 FYI:
- Elasticsearch is a distributed search and analytics engine.
- Pip is Python's pacakge manager.
- NPM is Node.js' package manager.


Build the Flask application with a "fat" Docker image.

Start with an empty Alpine image, install all tools you need.
Run the build command for the application, then set the Entrypoint to execute it.
Build the Flask application with a "thin" Docker image.

Use a multistage Dockerfile to minimize the content of the image.
After building, compare image sizes between the "fat" and "thin" builds.
Create docker-compose.yaml to start the system.

Add an Nginx based reverse proxy as part of your docker-compose.yaml.
Serve all static files (including index.html) directly from Nginx.
Update your Flask image so that it does not contain the static files.
Note: For the final static files step, you may need to build them with Docker, and then manually retrieve them and store them separately (on the host) for serving with Nginx.