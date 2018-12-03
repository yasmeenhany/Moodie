# moodie

> A project for advanced computer lab course

##Docker RUN

``` bash
# Build the docker container
docker build -t moodie .

# run the docker container on port 8080
docker run -p 8080:8080 moodie
```

##Docker compose

```bash
# to start the docker container
docker-compose up
```

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
