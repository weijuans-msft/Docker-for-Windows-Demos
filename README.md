# Docker-for-Windows-Demos

## Demo 1
TBD


## Demo 2

Talk about the vision; mention D4W supports Kubernetes for Linux container


### Machine Setup:
- Host: Windows 10 April 2018 Update (Version 1803, build number 17134.1) on a physical PC
- D4W: private build

#### Prep steps:

Open Powershell as Admin
```powershell
PS C:\WINDOWS\system32> cd 'C:\Program Files\docker\Docker\resources\kubernetes\'
PS C:\Program Files\docker\Docker\resources\kubernetes> dir


    Directory: C:\Program Files\docker\Docker\resources\kubernetes


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/4/2018  10:15 AM                pki
-a----         5/4/2018  10:15 AM           1017 Dockerfile-kubemaster
-a----         5/4/2018  10:15 AM            204 Dockerfile-pause
-a----         5/4/2018  10:15 AM            511 hello-world.yaml
-a----         5/4/2018  10:15 AM            700 init.ps1
-a----         5/4/2018  10:15 AM            129 kubelet-config
-a----         5/4/2018  10:15 AM              0 resolv.conf
-a----         5/4/2018  10:15 AM           1924 start-kubemaster.sh
-a----         5/4/2018  10:15 AM           3014 start.ps1
-a----         5/4/2018  10:15 AM             50 stop.ps1

```

```powershell
PS C:\Program Files\docker\Docker\resources\kubernetes> .\stop.ps1

PS C:\Program Files\docker\Docker\resources\kubernetes> .\init.ps1

PS C:\Program Files\docker\Docker\resources\kubernetes> .\start.ps1
```

Confirm D4W is running for Windows Containers
 ```powershell
 PS C:\WINDOWS\system32> docker version
Client:
 Version:      18.05.0-ce-dev
 API version:  1.37
 Go version:   go1.9.5
 Git commit:   adaf908
 Built:        Mon Apr 16 14:49:54 2018
 OS/Arch:      windows/amd64
 Experimental: false
 Orchestrator: swarm

Server:
 Engine:
  Version:      18.05.0-ce-dev
  API version:  1.37 (minimum version 1.24)
  Go version:   go1.10.1
  Git commit:   adaf908
  Built:        Mon Apr 16 15:05:59 2018
  OS/Arch:      windows/amd64
  Experimental: true
PS C:\WINDOWS\system32> winver
```
 
### Demo Steps:

```powershell
PS C:\Program Files\docker\Docker\resources\kubernetes> docker images
REPOSITORY                                 TAG                  IMAGE ID            CREATED             SIZE
lcow-kubermaster                           latest               68824657d1f7        About an hour ago   863MB
<none>                                     <none>               e3c97482e7ca        About an hour ago   268MB
apprenda/pause                             1                    946cd5c9abf9        4 hours ago         1.11GB
debian                                     jessie               4eb8376dc2a3        6 days ago          197MB
microsoft/nanoserver                       latest               353592ac9faa        3 weeks ago         1.11GB
gcr.io/google-containers/hyperkube-amd64   v1.10.0              79f28a9f288b        5 weeks ago         776MB
gcr.io/google-containers/etcd-amd64        3.0.17               243830dae7dd        14 months ago       188MB
gcr.io/google-containers/kube2sky          1.15                 f7c155731ff4        2 years ago         35.1MB
gcr.io/google-containers/skydns            2015-10-13-8c72f8c   718809956625        2 years ago         64MB
PS C:\Program Files\docker\Docker\resources\kubernetes> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                          NAMES
2f82318b72d9        lcow-kubermaster    "/bin/sh -c /start-k…"   2 minutes ago       Up 2 minutes        0.0.0.0:8080->8080/tcp, 0.0.0.0:5353->53/tcp   kubemaster
 
PS C:\Program Files\docker\Docker\resources\kubernetes> kubectl version
Client Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.0", GitCommit:"fc32d2f3698e36b93322a3465f63a14e9f0eaead", GitTreeState:"clean", BuildDate:"2018-03-26T16:55:54Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.0", GitCommit:"fc32d2f3698e36b93322a3465f63a14e9f0eaead", GitTreeState:"clean", BuildDate:"2018-03-26T16:44:10Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"linux/amd64"}
PS C:\Program Files\docker\Docker\resources\kubernetes>


PS C:\Program Files\docker\Docker\resources\kubernetes> kubectl get all
NAME         TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   192.168.0.1   <none>        443/TCP   5m

```
OK next will show how what we can do between D4W + Kube + Windows Container.

Ideally....

But...


```powershell
PS C:\Program Files\docker\Docker\resources\kubernetes> kubectl run build2018 --replicas=5 --image=microsoft/nanoserver --command ping localhost
```
