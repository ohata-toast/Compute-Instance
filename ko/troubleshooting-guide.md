## Compute > Instance > 문제 해결 가이드

TOAST를 사용하면서 겪을 수 있는 다양한 문제들을 해결하는 방법을 설명합니다.

<h3>현재 TOAST에서 기본 제공하는 OS 버전 이외의 버전을 사용하고 싶습니다. 개인 이미지를 업로드해서 사용할 수는 없나요?</h3>

TOAST에서 제공하는 OS 버전만 이용할 수 있습니다. 개인 이미지 업로드는 지원하지 않습니다.
개인화된 OS 이미지를 사용하시려면 TOAST에서 제공하는 이미지로 인스턴스를 생성하신 후, 이미지 생성 기능을 이용하시기 바랍니다.
<br>

<h3>인스턴스에 접속하면 "Permissions 0644 for '/Users/username/.ssh/your-key.pem' are too open." 에러가 뜨며 접속이 되지 않습니다.</h3>

인스턴스 접속에 사용하는 키페어의 개인 키(PEM 키)의 권한이 맞지 않아서 생기는 문제입니다.
아래와 같이 개인 키 파일의 권한을 조정합니다.

    $ chmod 600 your-key.pem

<br>

<h3>CentOS 인스턴스에서 root 권한을 어떻게 얻나요?</h3>

CentOS 인스턴스에서 root 권한을 얻기 위해서는 아래와 같이 `sudo` 명령을 이용합니다.

    $ sudo su

<br>

<h3>개인 이미지를 만들어서 인스턴스를 생성하고 부팅했는데 mount 에러가 납니다.</h3>

두 개 이상의 블록 스토리지를 사용하는 인스턴스로 이미지를 생성하고, 해당 이미지로 인스턴스를 만들어 부팅하는 경우에 위와 같은 문제가 발생합니다.

두 개 이상의 블록 스토리지를 사용하는 인스턴스는 기본 디스크 외의 다른 디스크를 `/etc/fstab` 파일에 설정합니다. 이미지 생성 시에 이 파일 역시 복제 되므로 새로운 인스턴스가 부팅될 때 `/etc/fstab` 파일이 참조하는 블록 스토리지가 없어서 mount 에러가 생깁니다.

이 문제를 해소하려면, `/etc/fstab` 파일에서 기본 디스크를 제외한 블록 스토리지 설정을 주석 처리하고 이미지를 생성해야 합니다.
<br>

<h3>ssh 접속이 너무 느립니다.</h3>

인스턴스가 속한 보안 그룹의 송신 부분에서 DNS를 막은 경우 발생합니다. DNS 송신을 할 수 있도록 보안 그룹을 조정합니다.
<br>

<h3>"could not resolve the host" 메세지가 뜨며 yum 등을 사용할 수 없습니다.</h3>

인스턴스가 속한 보안 그룹의 송신 부분에서 DNS를 막은 경우 발생합니다. DNS 송신을 할 수 있도록 보안 그룹을 조정합니다.
<br>
