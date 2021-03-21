# Video Streaming. (NodeJs, Stream API)

## A basic sample webpage built for streaming video. Video is fetched as a service call from backend and will implement the regular video streaming method
## Video is loaded for the first time interval and then starts playing. While watching the next time interval is loaded and the process continuous.

- Front End code is just a video player tag with a source link.
- Backend is NodeJs implementing the built in stream api module and will pass the streamed video data.

- git clone
- npm install
- npm start
- open browser in `localhost:3000`

## Working of the streaming request

`- When a request is made, we get the file size and send the first few chunks of the video in the else statement.`
<br />

`- When we start watching the video (by accessing the route via localhost:3000/video or from the front end), subsequent requests are made,`
<br />

`  this time with the range in the header so that we know the starting point of our next chunk.`
<br />

`- Read the file again to create another stream, passing along the new value for the start and the end`
<br />rea

`  (which will most likely be the current part that came in the request header and the file size of the video).`
<br />

`- We set our 206 header response to send only part of our newly made stream by applying the formula we talked about earlier.`