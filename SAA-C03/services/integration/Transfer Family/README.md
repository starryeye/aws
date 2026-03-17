## AWS Transfer Family

- FTP / SFTP / FTPS 프로토콜을 지원하는 managed file transfer service
  - S3/EFS 를 FTP 서버처럼 쓸 수 있게 해주는 서비스
  - 파일 전송을 위한 서버(FTP 서버)를 AWS가 대신 운영

- 지원 프로토콜
  - FTP (File Transfer Protocol)
  - SFTP (SSH 기반, 보안)
  - FTPS (SSL 기반)

- S3 또는 EFS를 스토리지로 사용
  - 클라이언트는 FTP/SFTP 로 접속
  - 실제 파일은 S3/EFS 에 저장됨

- 특징
  - 서버 관리 불필요 (fully managed)
  - IAM 기반 인증 가능
  - CloudWatch 로 로그/모니터링 가능

- 구조
  - Client → (FTP/SFTP) → Transfer Family → S3/EFS