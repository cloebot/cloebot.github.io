---
layout: post
title: WSL (Window Subsystem for Linux) 란 무엇이고 어떻게 가능한것일까?
subtitle: 그리고 그외 설치방법
tags: [wsl, window, linux]
comments: true
---

윈도우에서 네이티브 리눅스를 허용하면 **WSL(Windows Subsystem for Linux)** 를 통해 우분투 배쉬를 이용할 수 있게 되었다.

# 기존에 가상머신 리눅스랑은 어떻게 다를까?

결론부터 말하자면 WSL 는 윈도우에 하나의 레이어를 추가해서 System call을 번역해주는것이다. 굳이 말하자면 VM 이랑 비슷하다기 보다는 기존에 있는 CygWin 같은 툴이 비교대상 이라고 할 수 있다. 가상머신이 아니기 때문에 메모리를 따로 나눌 필요가 없고 실행속도도 빠르다. 하지만 진짜 리눅스를 돌리는 것이 아니라 리눅스의 APIs와 라이브러리를 가능 하게 만드는 것이기 때문에 어떤 리눅스 프로그램은 이용할 수 없을 수도 있다.

윈도우에서 리눅스롤 이용할 수 있는 방법은 세가지이고 다른점은 이와같다.

- **듀얼부팅 (Dual booting)** – 실제로 메모리에 두가지 os를 설치 하는것. Full speed, full feature 지만. 한번에 한가지 os 만 쓸수있다. 다른 os 로 바꾸려면 껐다가 다시 로딩해야한다
- **VM** – 두가지 os를 실행을 같이 시킬수있고 Linux의 모든 기능을 이용할수 있다. 하지만 가상 머신이기 때문에 속도는 느리다.
- **WSL** – 속도는 듀얼부팅처럼 빠르고 윈도우의 파일시스템을 공유할 수 있어서 연동이 쉽지만. 진짜 리눅스가 아니기때문에 리눅스의 full feature를 이용할 수 없다.
세가지 방법다 장단점이 있기때문에 무엇을 선택 할지는 내가 리눅스를 어떤 목적으로 쓸것인지에 달려있다.

# 윈도우에서 리눅스를 돌리는게 가능한이유는 뭘까?

윈도우의 초기 서브 시스템은 폐기 되었지만 윈도우 NT 커털은 새로운 하위 시스템 환경을 허용하도록 설계되었다. 이로써 Linux 용 윈도우 서브 시스템을 개발할 수 있는 것이다.

WSL는 윈도우 하위 시스템에 있는 리눅스 바이너리들을 이용해 가상 리눅스 커널을 윈도우 NT 커널위에 돌리게 해준다. 따라서, WSL 를 이용하면 리눅스 binaries 가 있는 Pico os 에서 윈도우 커널을 부를 수 있게 된다. 그러면 그 시스템에있는 드라이버들이 리눅스 명령을 NT APIs 으로 변역해준다. 이렇게 같은 커널을 간접적으로 공유하면서 WSL는 리눅스의 파일시스템을 모두 지원하고 윈도우의 파일들도 모두 접근이 가능하다.

![image of wsl structure](/img/wsl-structure.png)

# 설치방법

구글에 설치방법은 매우 다양하게 나와있다. 내가 참고한 링크는:

https://itsfoss.com/install-bash-on-windows/

https://docs.microsoft.com/en-us/windows/wsl/install-win10

참고 사항은 첫번째 링크의 첫번째 방법은 윈도우를 꼭 특정 업데이트 해야만 이용할 수 있지만 설치가 쉽고 두번째는 옛날 업데이트의 윈도우에서도 설치 할수 있는 방법이다.

# 참고 원문:  https://blogs.msdn.microsoft.com/wsl/2016/04/22/windows-subsystem-for-linux-overview/
