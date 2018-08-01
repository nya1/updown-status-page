# updown-status-page

> Free general updown.io status page for all your public checks

Demo: [example](https://status.1link.io/)


## How it works

Fetches updown.io's API via the read only key and populates the page, hosting is provided by Netlify (free).
Page is written with Vue.js.

## Deploy your own public page

 * [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/nya1/updown-status-page)
 
   * This will automatically create your own updown-status-page repository and setup netlify build commands

 * Go to your repository and edit `page_config.json` with your details (read only key, website url, logo url etc.)

Every Github commit will trigger a new deploy of your status page


## TODO

 * Automatically update checks every x minutes ? (based on the lowest checks.period)

 * Improve layout for mobile

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
