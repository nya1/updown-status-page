# updown-status-page

> Free general updown.io status page for all your public checks

![example](https://i.imgur.com/ONrj9QP.png)


## How it works

Fetches updown.io's API via the read only key and populates the page, hosting is provided by Netlify (free).
Page is written with Vue.js.

## Deploy your own public page

 * Fork this repository

 * Edit `page_config.json` and enter your details (read only key, website url, logo url etc.)

 * Deploy to Netlify


## Build Setup (only for development)

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

## TODO

 * Automatically update checks every x minutes (based on the lowest checks.period)

 * Add footer (twitter, email and homepage link)

 * Improve layout for mobile
 
 * Better spacing between checks
