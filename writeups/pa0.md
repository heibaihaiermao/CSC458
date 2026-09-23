# Programming Assignment 0 Writeup

**Name:** Yucan Miao

**UTORid:** miaoyuca

**People/resources credited:** python socket documentation, prompting LLM to "everything I need to program this script"

**Approximate time spent:** 2 hours

## Mandatory questions

1. In an HTTP/1.1 request, what byte sequence separates one header line from the next, and what marks the end of the complete header block?

   **Answer:** \r\n seperates each header line. There is an additional blank line in the end of header block, which is shown as \r\n\r\n

2. Why must `get_url()` keep calling `recv()` until it returns `b""` instead of making exactly one `recv()` call?

   **Answer:** TCP provides connection and ensures all data will arrive in order eventually, however it doesn't guarantee that all of the data will arrive in one go, nor does it promise to break off each chunk at bytes corresponding to human's natural reading habit. Hence we need to receive the end of response indicator to know all of the data has been tranmitted.

3. What does the `Connection: close` request header accomplish in this assignment? How does it help the client know that the response is complete?

   **Answer:** Connection: close tells the HTTP/1.1 server that the client wants the TCP connection to be closed after the response. The client can therefore use the server's TCP connection close as the indication that the response is complete. Once all remaining response bytes have been received, recv() returns b"", allowing get_url() to stop receiving.

4. In Python, why does the starter program write the response with `sys.stdout.buffer.write(...)` instead of decoding every response as UTF-8 text first?

   **Answer:** Because HTTP response may also contains binary data such as image, this avoid decoding errors or modification to the original data.

## Optional feedback

- I had unexpected difficulty with:
- I think this assignment could be improved by:
- I was surprised by:
- I am still unsure about:
