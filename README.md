# Node.js Server Hanging on Large Requests

This repository demonstrates a common issue in Node.js where a server can hang when receiving large requests.  The problem stems from a lack of proper handling of the request's 'end' event.

## Problem

The `server.js` file contains a basic HTTP server that attempts to parse JSON from incoming requests.  Without the fix, if a large JSON payload is sent, the server will appear to hang because it doesn't know when the entire request body has been received.

## Solution

The `serverSolution.js` file provides the solution.  By adding an event listener to the 'end' event of the request, the server ensures that the JSON parsing and response are handled only after the entire request body has been received.