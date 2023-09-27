Closing a file is important as you are informing the underlying operating system that you're done working with the file. If you don't close a file, it is possible to lose data. There may be pending writes buffered up which might not get written completely. Furthermore if you're opening lots of files, your system may run out of resources. 


We want a mechanism to pair open() and close(). Python does this by implementing a specific control flow structure called `with-blocks` that can be used with any object that supports the [[context-manager protocol]]  e.g files.

This means we no longer need to call close explicitly because the `with` construct will call it for us when and by whatever means execution exits the block.