`open()` 
file: path to file (required)
mode: read, write or append, plus binary or text
encoding: encoding to use in text mode 



Files opened in Binary Mode return and manipulate their contents as bytes objects without any decoding. Binary mode reflects the raw data in the file.

A file opened in Text Mode treats its contents as if it contains text strings of the `str` type, the raw bytes having been first decoded, using a platform-dependent encoding or using the specified encoding if given. By default text mode files also engage support for Python's universal new lines. This causes translation between a portable single new line character in our program strings, `/n` in a platform-dependent new line representation of the raw bytes stored in the file system; for example carriage return, new line, `/r/n` on Windows

Default encoding
- System dependent, crucial to get the encoding correct
```Python
>>> import sys
>>> sys.getdefaultencoding()
'utf-8'
```
