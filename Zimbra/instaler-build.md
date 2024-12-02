```bash
apt update

apt install software-properties-common openjdk-8-jdk ant ant-optional ant-contrib ruby git maven build-essential debhelper

cd .ssh/

ssh-keygen -t ed25519 -C "GitHub_Email_Registered"

cat id_ed25519.pub // output copy to GitHub

ssh -T git@github.com

mkdir installer-build

cd installer-build/

wget [https://github.com/Zimbra/zm-build/archive/refs/tags/10.1.1.tar.gz](https://github.com/Zimbra/zm-build/archive/refs/tags/10.1.1.tar.gz)

tar -xvf 10.1.1.tar.gz

mv zm-build-10.1.1 zm-build

cd zm-build/

ENV_CACHE_CLEAR_FLAG=true ./build.pl --ant-options -DskipTests=true --git-default-tag=10.1.1,10.1.0 --build-release-no=10.1.1 --build-type=FOSS --build-release=LIBERTY --build-release-candidate=GA --build-thirdparty-server=files.zimbra.com --no-interactive

cp installer-build/.staging/UBUNTU20_64-LIBERTY-1011-20241104123541-FOSS-1002/zm-build/zcs-10.1.1_GA_1002.UBUNTU20_64.20241104123541.tgz /root/
```
