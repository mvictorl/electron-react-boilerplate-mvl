## Project was build by instruction of [with blog](https://medium.com/@devesu/how-to-build-a-react-based-electron-app-d0f27413f17f)

In the project directory, you can run:

`# yarn start`

or

`# npm start`

React side of app runs  in the development mode and\
available at [http://localhost:3000](http://localhost:3000) without output in the browser.

To re-run closed Electron window just execute in terminal:

`# electron .`
___
## Summary of create this boilerplate 

1. Create React app by create-react-app:

    `# npx create-react-app <your_app_name>`

1. Install necessary packages for development:

    `yarn add cross-env electron-is-dev`

    or `npm install --save cross-env electron-is-dev`,
   
    and

    `yarn add --dev concurrently electron electron-builder wait-on` 

    or `npm install concurrently electron electron-builder wait-on`

1. Create standard Electron `main.js` file inside `electron` folder  project directory:

1. Take change in `package.json` and add below information:
    
    ```json
    "description": "<your project description>",
    "author": "<author of app>",
    "build": {
        "appId": "<com.your_app>"
    },
    "main": "public/electron.js",
    "homepage": "./",
    ```
   
    and update **scripts** element like below:
    
    ```json
    "scripts": {
        "react-start": "react-scripts start",
        "react-build": "react-scripts build",
        "react-test": "react-scripts test --env=jsdom",
        "react-eject": "react-scripts eject",
        "electron-build": "electron-builder",
        "release": "yarn react-build && electron-builder --publish=always",
        "build": "yarn react-build && yarn electron-build",
        "start": "concurrently \"cross-env BROWSER=none yarn react-start\" \"wait-on http://localhost:3000 && electron .\""
    },
    ```

_That's all!_
