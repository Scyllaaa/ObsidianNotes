copy the ``.b64` into the RDP desktop

1. get a command line up  
2. . cd to the desktop 
3. Issue: `certutil -decode rhys.b64 rhys.zip`
4. unpack the zip  
5. open the .pass file and copy the text (make sure you do not include the return/next line in the file only the text)  
6. use the settings of the browser to import the cert. 

## Wiki Page 
Just the bit under **Certificates**  
and using the base64 method to transfer the file is the easiest  
[https://wiki.corp.zynstra.com/books/retail-support-icp/page/mp-new-user-creation](https://wiki.corp.zynstra.com/books/retail-support-icp/page/mp-new-user-creation)