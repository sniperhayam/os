> [!Caution]
> _This project does not have a proper maintenance schedule yet. try at your own discretion._

To rebase an existing atomic Fedora installation to the latest build:  
1. First rebase to the unsigned image, to get the proper signing keys and policies installed:
```
rpm-ostree rebase ostree-unverified-registry:ghcr.io/hayam-ahamed/os:latest
```
2. Reboot to complete the rebase:
```
systemctl reboot
``` 
3. Then rebase to the signed image, like so:
```
rpm-ostree rebase ostree-image-signed:docker://ghcr.io/hayam-ahamed/os:latest
```  
4. reboot again to complete the installation  
```
systemctl reboot
```
5. Verify 
You should verify the signature by downloading the [cosign.pub](https://github.com/hayam-ahamed/os/edit/main/cosign.pub) file from this repo and running the following command in the same directory as cosign to ensure the installation wasn't tampered by anyone:
```
cosign verify --key cosign.pub ghcr.io/hayam-ahamed/os
```
