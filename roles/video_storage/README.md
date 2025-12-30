Role Name: video_storage
=========

이 role은 영상 파일 저장을 위한 NFS 서버를 구축한다.
CentOS 기반 서버에 NFS 서비스를 설치하고, 영상 데이터 디렉토리를 생성한 뒤
내부망에 위치한 여러 클라이언트 서버들이 해당 디렉토리를 마운트할 수 있도록 설정한다.

본 role은 서버 역할만 담당하며,
클라이언트 마운트 설정은 video_storage_client role에서 수행한다.

Requirements
------------

- OS: CentOS 7 / Rocky Linux / AlmaLinux 계열
- Ansible Control Node에서 SSH 키 기반 접속 가능
- 대상 서버에 sudo 권한을 가진 사용자 존재 (ex: ansible)
- 내부 네트워크 통신 가능 (ex: 192.168.30.0/24)

Role Variables
--------------

defaults/main.yml
nfs_export_dir: /data/video		(NFS로 공유할 영상 저장 디렉토리)
nfs_network: 192.168.30.0/24		(접근을 허용할 내부 네트워크)
nfs_owner: vs				(디렉토리 소유 사용자)
nfs_group: vs				(디렉토리 소유 그룹)

vars/main.yml (예시)
nfs_packages:				(설치한 NFS 관련 패키지)
  - nfs-utils

Dependencies
------------

이 role은 직접적인 Galaxy dependency는 없지만, 실제 운영 환경에서는 아래 role들과 함께 사용되는 것을 권장한다.

- common
  기본 패키지
  시간 동기화
  SSH 설정
- ssh_bootstrap
  SSH 키 배포
  비밀번호 없는 접근 구

Example Inventory
-----------------

[storage]
video_storage ansible_host=192.168.30.20 ansible_user=ansible

Example Playbook
----------------

- name: video Storage Server 구축
  hosts: stroage
  become: true
  roles:
    - video_storage

License
-------

MIT

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
