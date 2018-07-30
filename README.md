# updown-status-page

> Free general updown.io status page for all your public checks

![example](https://i.imgur.com/ONrj9QP.png)


## How it works

Fetches updown.io's API via the read only key and populates the page, hosting is provided by Netlify (free).
Page is written with Vue.js.

## Deploy your own public page

 * Fork and deploy to Netlify: [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/nya1/updown-status-page)

 * Go to your repository and edit `page_config.json` with your details (read only key, website url, logo url etc.)

Every Github commit will trigger a new deploy of your status page


## TODO

 * Automatically update checks every x minutes (based on the lowest checks.period)

 * Add footer (twitter, email and homepage link)

 * Improve layout for mobile
 
 * Better spacing between checks


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
