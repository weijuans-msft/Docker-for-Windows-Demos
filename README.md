# Docker-for-Windows-Demos

Demo 1
TBD


Demo 2

Machine Setup:
- Host: Windows 10 April 2018 Update (Version 1803, build number 17134.1) on a physical PC
- D4W: private build

Demo Steps:

Open Powershell as Admin

Go to this folder: C:\program files\docker\docker\resources\kubernetes, and run the following 3 scripts:
	 ./stop.p1 to shutdown master and kubelet
	 ./init.ps1 to rebuild images
	 ./start.ps1 to start master and kubelet (we will see kubelet output in a console and to get master logs do 'docker logs kubemaster')
   
 Run "docker version" to ensure it is running for Windows Containers
 
 
 


