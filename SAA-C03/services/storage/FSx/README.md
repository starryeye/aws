## FSx

- 고성능(low latency, high performance) 파일 스토리지 서비스

- 유형
    - FSx for Lustre
        - 고성능 병렬 파일 시스템이다.
            - 머신러닝, 빅데이터 분석 용도
        - S3 연동 가능
        - Lustre 자체 프로토콜만 지원
    - FSx for NetApp ONTAP
        - 다양한 OS(windows, mac os, linux) 호환
        - Linux 기반 파일공유 프로토콜인 NFS 지원
        - Windows 기반 파일공유 프로토콜인 SMB 지원
        - capacity pool tiering 정책 제공
            - 자주 사용하지 않는 데이터를 자동으로 저비용 스토리지로 이동하는 기능
            - SSD(Storage tier) → Capacity Pool(S3 기반)로 이동
        - iSCSI 지원 (block storage 제공)
          - block(단일 디스크) storage 는 strong consistency 을 만들기에 유리한 구조이다.
    - FSx for Windows File Server
        - SMB 지원
    - FSx for OpenZFS
        - NFS 지원