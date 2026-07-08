> [!Caution]
> _This project does not have a proper maintenance schedule. try at your own discretion._

To rebase an existing atomic Fedora installation to the latest build:  
1. First rebase to the unsigned image, to get the proper signing keys and policies installed:
```
rpm-ostree rebase ostree-unverified-registry:ghcr.io/sniperhayam/os:latest
```
2. Reboot to complete the rebase:
```
systemctl reboot
``` 
3. Then rebase to the signed image, like so:
```
rpm-ostree rebase ostree-image-signed:docker://ghcr.io/sniperhayam/os:latest
```  
4. reboot again to complete the installation  
```
systemctl reboot
```
   
<!-- **ISO**   -->
<!-- If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here. These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.](#anchor-1 "#anchor-1")   -->
**Verification**  
You can verify the signature by downloading the cosign.pub file from this repo and running the following command in the same directory as cosign:
```
cosign verify --key cosign.pub ghcr.io/sniperhayam/os
```

ROAD MAP :
  - Port hardened_malloc from Graphene OS
  - Add MOK enrollment module
  - Restrict SELinux to always enforcing at run time & more !
