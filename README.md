# electron-passing-data-demo

This demo illustrates how to pass data from the main process to a renderer process in an Electron app. 

Note, the main process runs the electron app underneath everything. A renderer is a web page and is the JS code youhave written that runs that html document. 

## Getting started

Download the files in this repo. Install the dependencies:

`npm install`

Then launch the Eelctron app with: 

`npm start`

The app should show the a Hello World message. Below is a button labeled test. Clicking the button fetches some data from main and displays it.

Data returned should be a number of random numbers set by the value in the field. 

## What is happening?

In index.html pressing the test button collects the value from the input field and sends that to the main process in main.js

`ipcRenderer.send('asynchronous-message', count)`

In main.js messages with the event name: 'asynchronous-message' are handled here:

```JS
ipcMain.on('asynchronous-message', (event, count) => {
  
})
```

main.js sends data back to the rendering process with this line: 

```JS
win.webContents.send('asynchronous-reply', data)
```

This reply from main.js is handled in index.html with: 

```JS
ipcRenderer.on('asynchronous-reply', (event, arg) => {

})
```