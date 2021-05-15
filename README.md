# buildozer_setup
Repo that contains description how to make buildozer work. Works on 15.05.2021. buildozer.spec file was enriched with libff requirement.

## Requirements
This repo was created and tested on Python 3.6.13.

## Buildozer Setup
First run following commands in order to install dependencies (it may contain large redundance, but who cares).:

```bash
sudo apt-get install openjdk-8-jdk -y
sudo apt update
sudo apt install -y git zip unzip openjdk-8-jdk python3-pip autoconf libtool pkg-config zlib1g-dev libncurses5-dev libncursesw5-dev libtinfo5 cmake libffi-dev libssl-dev
sudo apt install libffi-dev
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt-get install build-essential python-dev python-setuptools python-pip python-smbus -y
sudo apt-get install libncursesw5-dev libgdbm-dev libc6-dev -y
sudo apt-get install zlib1g-dev libsqlite3-dev tk-dev -y
sudo apt-get install libssl-dev openssl -y
sudo apt-get install libffi-dev -y
```

Secondly run following commands in order to prepare virtual environment:

```bash
python3.6 -m virtualenv venv
source ./venv/bin/activate
pip install kivy
pip install buildozer
pip install cython
pip install --upgrade Cython==0.29.19
```

Thirdly run following commands in order to download working sdkmanager and install API target 27 and build-tools with version > 25:
```bash
export PATH=/home/[your_username]/.buildozer/android/platform/android-sdk/tools:/home/[your_username]/.buildozer/android/platform/android-sdk/tools/bin:$PATH

wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip
unzip sdk-tools-linux-3859397.zip
mv tools home/krzysztof/.buildozer/android/platform/android-sdk/
sdkmanager "platforms;android-27" "build-tools;24.0.2"
buildozer android clean
sdkmanager "platforms;android-27" "build-tools;25.0.2"
```
where you need to replace [your_username] with your actual username!

## Test
Run following command:
```bash
buildozer android debug
```

