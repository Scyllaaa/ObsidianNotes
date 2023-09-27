- Common on UNIX systems to have a special comment called a shebang
- This begins with the usual hash, as for any other comment, followed by any other comment
- This allows the program loader to identify which interpreter should be used to run the program
-  They also allow for documentation of whether the script is written for Python2 or Python3.
- The exact details of the shebang depend on where python is on the system.
- The script must be marked as an executable in order for the shebang to have any effect
- Typical python3 shebang's use the UNIX env program to locate Python 3 on the path environment variable, which importantly is compatible with Python virtual environments
		#!/usr/bin/env python