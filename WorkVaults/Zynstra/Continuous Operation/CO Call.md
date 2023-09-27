- What was the initial issue that called for the development of CO / Continuous Fuel?
- Can you take me through the process when working with a client to create custom VM payloads using CO?
	- Good examples?
	- What is the perspective of an Operator when using these payloads?
	- Configuration options? Example config file?
- Could you point me towards any metrics that i could use? e.g the cost of downtime while upgrading a VMs?

Answers
+ PFJ only has CO, started just for PJF, update fuel in a continuous way, update windows and reboot "please don't turn off screen", fuel services would be down
+ Lost 'millions' of dollars every window update cycle, asked for a way to apply update but continue to,
+ Same logic applied to the POS \
+ Than for numbers
+ Not a problem for other places, circle k don't do windows updates, they ignore updates, commitment of cost because we have to put in integration into customers payload, with PowerShell.
+ PowerShell in AdvEng is a framework that we use, instead of blank hooks, Karl will put in
+ Repo is framework for running hooks, unchanged, but the hooks themselves are seriously authored, Jon K will be able to tell significant changes to hooks
+ E.g continuous POS, he would use the cutover hook, reintegrating step 
+ Fuel cutover drive, Sequel database, POS will have different files to cutover, cutover mechanism is the same
+ Final hook that does the copy to and from the cutover from, we have a number of different hooks in powershell file, can run commands scripts copy single and recursive file.


Perspective of an Operator
- Within Pilots workflow, sysadmins, will remote run the 'Start CO' process.
- This different between POS and Fuel, 
	- On Fuel they might use the ZCC or RDP to remote onto the desktop
	- On POS they are tied onto automated process, 
	- They have a linebreak, operator taking break, they log out of the POS (application) not windows.

Tang Guing

Matt Leonard for VM diagnostics - Operate on VM in then current state. Wills devliery team
Used for in place upgrade form going from windows 11 to windows 10.


Is there a presentation? / Previous Powerpoints