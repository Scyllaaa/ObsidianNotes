The main entry control script is called `vmclone` located on [[zhapcon]]. This script is responsible for creating, removing, starting and stopping a clone VM. It is also responsible for keeping track of clones by the means of using configuration files. Some of the functions of `vmclone` act as a wrapper to the Python script `xen_clone`.

The `vmclone` script requires a mode argument. All mode options can be identified by running `vmclone --help`. Additional arguments for each mode can be identified by running `vmclone [mode] --help` where `[mode]` is an actual mode.

Some basic `vmclone` command examples:

- List all clones on the server:
    
    ```
    vmclone list
    ```
    

- Create an offline clone of zapp-00 called `myclone` and start it:
    
    ```
    vmclone create --vm zapp-00 --clone-name myclone --start
    ```
    
- Remove all inactive clones on the server:
    
    ```
    vmclone remove --all-clones
    ```
    
- Mark the clone name `myclone` as inactive:
    
    ```
    vmclone set --clone-name myclone --mark-inactive
    ```
    
- Start the VM with clone name `myclone`:
    
    ```
    vmclone start --clone-name myclone
    ```
    
- Force stop the VM with clone name `myclone`:
    
    ```
    vmclone stop --clone-name myclone --force
    ```
    
This script is also responsible for setting the network and peripheral lockdown values into a configuration file, however it it not responsible for applying these lockdowns (see Monitor Scripts).