> _Heads Up: This project does not have a proper maintenance schedule. try at your own discretion._

To rebase an existing atomic Fedora installation to the latest build:  
- First rebase to the unsigned image, to get the proper signing keys and policies installed:  
- rpm-ostree rebase ostree-unverified-registry:ghcr.io/sniperhayam/os:latest  
   
- Reboot to complete the rebase:  
- systemctl reboot  
   
- Then rebase to the signed image, like so:  
- rpm-ostree rebase ostree-image-signed:docker://ghcr.io/sniperhayam/os:latest  
   
- Reboot again to complete the installation  
- systemctl reboot  
   
<!-- **ISO**   -->
<!-- If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here. These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.](#anchor-1 "#anchor-1")   -->
**Verification**  
These images are signed with [Sigstore's ](https://www.sigstore.dev/ "https://www.sigstore.dev/")[cosign. You can verify the signature by downloading the cosign.pub file from this repo and running the following command:](https://github.com/sigstore/cosign "https://github.com/sigstore/cosign")  
cosign verify --key cosign.pub ghcr.io/sniperhayam/os  
   
