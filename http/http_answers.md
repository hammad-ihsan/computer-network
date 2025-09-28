# HTTP Analysis

## Q1. What is the name of website?
The website accessed is identified by the **Host header** in the GET request:  
`web.simmons.edu`  

---

## Q2. Find the packet that contains the first GET request.
The first GET request appears in **Packet No. 1**:  


---

## Q3. Describe all headers and their values in this GET request.
The headers in the GET request are:

**GET /~grovesd/comm244/notes/week2/links HTTP/1.1**
**Host:** web.simmons.edu
**User-Agent:** Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/XYZ Safari/537.36
**Accept:** text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
**Accept-Encoding:** gzip, deflate, br
**Accept-Language:** en-US,en;q=0.5
**Connection:** keep-alive
 

---

## Q4. Identify the status code in the first server response.
The first response from the server contains the status code:  
**200 OK**

---

## Q5. How many HTTP response messages are exchanged in total?
By filtering with `http.response` in Wireshark, we observe multiple response messages.  
- First response: `200 OK (text/html)`  
- Second response: `200 OK (text/css)`
- Third response: `200 OK (application/javascript)`  
- Fourth response: `200 OK (PNG)`
- Fifth response: `200 OK (JPEG JFIF image)`
- Sixth response: `200 OK (PNG)`
- Seventh response: `404 Not Found (text/html)`

**Total responses observed: 7**

---

## Q6. Determine whether the connection is persistent or not.
The connection is **persistent**, because:
- The request includes the header `Connection: keep-alive`.  
- Multiple HTTP responses (HTML + CSS) were exchanged over the same TCP connection without reconnecting.  

**Conclusion:** The HTTP connection is persistent.
