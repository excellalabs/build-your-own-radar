[![Build Status](https://travis-ci.org/excellalabs/build-your-own-radar.svg?branch=master)](https://travis-ci.org/thoughtworks/build-your-own-radar)

A library that generates an interactive radar, inspired by [thoughtworks.com/radar](http://thoughtworks.com/radar).

## Demo

You can see this in action at [https://radar.labsincubator.com](https://radar.labsincubator.com). If you plug in [this data](https://docs.google.com/spreadsheets/d/1nodW2q6Is-A-Cw7h7d3drneVHuRMP-zhPYEU0o1_Qqg/edit#gid=0) you'll see [this visualization](http://radar.labsincubator.com/?sheetId=https%3A%2F%2Fdocs.google.com%2Fspreadsheets%2Fd%2F1nodW2q6Is-A-Cw7h7d3drneVHuRMP-zhPYEU0o1_Qqg%2Fedit%23gid%3D0). 

## How To Use

The easiest way to use the app out of the box is to provide a *public* Google Sheet ID from which all the data will be fetched. You can enter that ID into the input field on the first page of the application, and your radar will be generated. The data must conform to the format below for the radar to be generated correctly.

### Setting up your data

You need to make your data public in a form we can digest.

Create a Google Sheet. Give it at least the below column headers, and put in the content that you want:

| name          | ring   | quadrant               | isNew | description                                             |
|---------------|--------|------------------------|-------|---------------------------------------------------------|
| Composer      | adopt  | tools                  | TRUE  | Although the idea of dependency management ...          |
| Canary builds | trial  | techniques             | FALSE | Many projects have external code dependencies ...       |
| Apache Kylin  | assess | platforms              | TRUE  | Apache Kylin is an open source analytics solution ...   |
| JSF           | hold   | languages & frameworks | FALSE | We continue to see teams run into trouble using JSF ... |

### Sharing the sheet

* In Google sheets, go to 'File', choose 'Publish to the web...' and then click 'Publish'.
* Close the 'Publish to the web' dialog.
* Copy the URL of your editable sheet from the browser (Don't worry, this does not share the editable version). 

The URL will be similar to [https://docs.google.com/spreadsheets/d/1waDG0_W3-yNiAaUfxcZhTKvl7AUCgXwQw8mdPjCz86U/edit](https://docs.google.com/spreadsheets/d/1waDG0_W3-yNiAaUfxcZhTKvl7AUCgXwQw8mdPjCz86U/edit). In theory we are only interested in the part between '/d/' and '/edit' but you can use the whole URL if you want.

### Building the radar

Paste the URL in the input field on the [radar homepage](https://radar.labsincubator.com).

That's it!

Note: the quadrants of the radar, and the order of the rings inside the radar will be drawn in the order they appear in your Google Sheet.

### More complex usage

To create the data representation, you can use the Google Sheet [factory](/src/util/factory.js), or you can also insert all your data straight into the code.

The app uses [Tabletop.js](https://github.com/jsoma/tabletop) to fetch the data from a Google Sheet, so refer to their documentation for more advanced interaction.  The input from the Google Sheet is sanitized by whitelisting HTML tags with [sanitize-html](https://github.com/punkave/sanitize-html).

The application uses [webpack](https://webpack.github.io/) to package dependencies and minify all .js and .scss files.

## Contribute

If you are interested, please contribute to ThoughtWorks' [original repository](https://github.com/thoughtworks/build-your-own-radar).

### Don't want to install node? Run with one line docker

     $ docker run -p 8080:8080 -v $PWD:/app -w /app -it node:7.3.0 /bin/sh -c 'npm install && npm run dev'

After building it will start on localhost:8080
