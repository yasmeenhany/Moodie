# Moodie

This is a web application where a user selects a mood from a list of moods provided on the web application, and according to the mood the web application will return a list of movie recommendations that fit for this mood. The application uses Firebase to store the mood to genre mappings and themoviedb api to get movies with the corresponding genres.

> A project for advanced computer lab course
## 1) Config
 1.1) Create a file named config.json inside the config folder.
 
 1.2) Copy the contents of config.json-example inside the file created at step 1.1.

## 2) Option 1: Run with Docker:

## 2.1) Docker RUN

``` bash
# Build the docker image
docker build -t moodie .

# run the docker image on port 8080
docker run -p 8080:8080 moodie
```

## 2.2) Docker Compose

```bash
# to start the docker container
docker-compose up
```
## 2) Option 2: Run Without Docker:

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build


For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
