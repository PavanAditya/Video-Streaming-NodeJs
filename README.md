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
`  this time with the range in the header so that we know the starting point of our next chunk.`
<br />

`- Read the file again to create another stream, passing along the new value for the start and the end`
`  (which will most likely be the current part that came in the request header and the file size of the video).`
<br />

`- We set our 206 header response to send only part of our newly made stream by applying the formula we talked about earlier.`
<br />

`- Forb every request, the creteReadStream method will read it and will create(divide) the video into chunks of data packs and will be sent to the client in a stream.`
<br />

`- If the video is paused at the frontend, the chunks sending will also get paused as the memory buffer is full with the current cunks and that is not being cleard`
<br />

`- When the frontend starts consuming the video chunks the memory buffer will get cleared at the backend and will release the next chunks of information.`
<br />

`- This effect of pausing of chunks sent is called back-pressure. Memory buffer exerts back-pressure onto the chunk sending streamline and will make it hold the chunk reading part until the memory buffer is cleared and ready to accept new chunk values.`