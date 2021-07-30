# Ansible for the Absolute Beginners Course

## Ansible

### Introduction

Ansible을 사용하는 이유는 다음과 같은 작업들을 쉽고 효율적으로 하기 위함이다. Shell Script를 이용하여 다음 작업들을 수행할 수도 있지만, Ansible이 더 배우기 쉽고 간단하고 자동화를 위한 여러 가지 기능을 제공하기 때문이다.

- Provisioning
- Configuration Management
- Continuous Delivery
- Application Deployment
- Security Compliance

### Install Ansible

- CentOS / RHEL

    `yum install epel-release` 로 EPEL Repository 추가

    `yum install ansible` 설치

- Debian / Ubuntu

    `apt install ansible`

설치 후 `ansible --version`으로 설치된 버전 확인

`inventory.txt` 파일에 Client 또는 그룹을 지정하여 사용할 수 있다.

```
# inventory.txt
target1 ansible_host=192.168.0.17 ansible_ssh_pass=password
```

`ansible target1 -m ping -i inventory.txt` 명령을 실행하게 되면 target1 으로 ping 모듈을 사용하고 해당 결과를 반환하게 된다.

만약 ansible은 ssh를 이용하여 명령을 실행하므로 host의 key file이 등록되지 않은 경우에는 에러가 발생할 수 있다. 이 부분은 `/etc/ansible/ansible.cfg` 파일의 `host_key_checking = False` 부분의 주석을 해제해주면 된다. 그러나 이 방법은 안전하지 않을 수 있기 때문에 권장하지 않는다.
