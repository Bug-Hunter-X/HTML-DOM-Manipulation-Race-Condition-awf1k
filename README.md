# Uncommon HTML Bug: DOM Manipulation Race Condition

This repository demonstrates a subtle race condition that can occur when JavaScript attempts to manipulate the DOM (Document Object Model) before the browser has fully parsed and rendered the HTML.

## The Bug
The `bug.html` file contains a simple HTML page with a div element and a script. The script tries to hide the div by setting its display style to "none" but this might fail due to timing issues.  If the script executes before the browser has completed parsing the HTML, `document.getElementById("myDiv")` will return null, resulting in an error or unexpected behavior.

## The Solution
The solution (`bugSolution.html`) demonstrates the correct approach which is to use the DOMContentLoaded event to execute the JavaScript code. The DOMContentLoaded event is fired when the initial HTML document has been completely loaded and parsed, but without waiting for stylesheets, images, and subframes to finish loading.