---
title: "GitHub 서버"
date: 2019-03-19 00:38:28 -0400
categories: github
---

#GitHub Server - SSH

##SSH 공개키 만들기
Git 서버들은 SSH 공개키로 인증한다.
공개키를 만들기 전에 키가 있는지 먼저 확인한다. 사용자의 SSH 키들은 기본적으로 사용자의 `~/.ssh`디렉토리에 저장한다.
```
$ cd ~/.ssh
$ ls
id_rsa id_rsa.pub known_hosts
```
`~.pub` 파일은 공개키고 나머지는 개인키다. 만약 이 파일이 없거나 `.ssh` 디렉토리도 없으면 `ssh-keygen`이라는 프로그램으로 키를 생성해야 한다. `ssh-keygen`프로그램은 리눅스나 Mac의 SSH 패키지에 포함되어 있고 윈도우는 MSysGit 패키지 안에 들어있다.

키를 저장할 경로를 입력하고 암호를 두 번 입력한다. 이때 암호를 비워두면 키를 사용할 때 암호를 묻지 않는다.
사용자는 그 다음에 자신의 공개키를 Git 서버 관리자에게 보내야 한다. 사용자는 `.pub` 파일의 내용을 복사하여 메일을 보내기만 하면 된다. 공개키를 보려면 `$ cat ~/.ssh/id_rsa.pub`를 입력한다.

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQChgkBvvRTOwW/W/BkClU8fh4XcGEaDp74wuSGkIY3DUPJWIce/JMWAjR0125xkE7w9X2CFdqdYNg0pikZDZJaxUyA4bCrWgWszCY0RNQiPN0dxadh6oWxhPGrKUvet4xllMhJjP3Hc8n0Kw1VlamL3SYjF5rnOHM0do/GucfFc4cspue9lfjhxmDVTlqeEBA//0F8t9s7usTNw721HArTtDprVzRQRiV4WYKJPEp3c5Vz6Z2onHh0V7WsrRFXAoFFB6HWBBjP54ike885BgykE5yjXxEmXR7L+8JNKs0R1XzCK2S/09mdqFasfkOdbsjJv/EIHoPuIaAbMiYyA7MMB 김나경@LG

```

출처: 
