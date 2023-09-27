Python wheels are a pre-built binary package format for [[Python]] modules and libraries. They are designed to make it easier to install and manage Python packages, by providing a convenient, single-file format that can be downloaded and installed without the need to compile the package from source code. They are designed to replace the older egg format and provide a number of benefits over eggs and other package formats, such as easier installation and better support for versioning and dependencies.

When you install a package provided in traditional .egg format the following steps are performed by the system.

1. The system downloads a TAR file (tarball).
2. The system builds a .whl file by calling  [setup.py](https://www.geeksforgeeks.org/what-is-setup-py-in-python/)
3. The system installs the actual package after having built the wheel.

This process of downloading and compiling the tar file makes the whole process cumbersome and time-consuming.

**What are the advantages of using Python Wheels?**

One of the key advantages of using wheels is that they allow Python modules to be installed and used without requiring a build process. This means that users can simply download a wheel package and install it using the pip command, without needing to compile the package from the source code or install any additional dependencies. This can significantly speed up the installation process for large or complex Python packages.