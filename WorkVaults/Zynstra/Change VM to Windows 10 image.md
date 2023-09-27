You can change a customer VM to Windows 10 by;  
1. ICP: On the DB change the following in the VM doc; (configuration, disk, 0, bootstrap; reference) "custom/ci_win10"  
This can help find your VM quicker;  
`function(a){if(a.additionalType=="zapp"){emit(a.vmid,{_id:a.vmid});}}`

1. Wait for changes to pass to the IES, up to 5 min
2. ICP or zhapcon: stop the customer VM
3. zhapcon: inject the new image; `vminject-adhoc.sh -f -l -a -v ${uuid}`
4. ICP or zhapcon: start VM