# Git Book 가이드

## 연동 시 발생한 이슈
👉 ssh 문제
여러개의 계정을 ssh 키로 관리하고 있었는데 오랜만에 nanuya 계정에 접속했더니 아래와 같은 오류가 발생했다.

```shell
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:~~~~~.
Please contact your system administrator.
Add correct host key in /Users/godo/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/godo/.ssh/known_hosts:2
Host key for github.com has changed and you have requested strict checking.
Host key verification failed.
```

해결(?) 방법이라고 하긴 애매한 임시방안
```
$ cd ~/.ssh
$ rm known_hosts
```
이전에 접속했던 기록을 삭제해버림..

```
$ssh -T nanu-github.com
```
으로 다시 계정 등록함
