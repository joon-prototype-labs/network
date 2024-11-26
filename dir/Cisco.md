Cisco 관련 내용인데, 정리 안하기엔 좀 아쉬운것들 


### Cisco IOS

Cisco IOS에 대한 주요 내용을 간단히 요약하면:

1. IOS의 발전
- 라우터용 OS로 시작해서 스위치, 방화벽 등 대부분의 Cisco 장비에 확장 적용
- 모놀리식 커널 구조로, 안정성은 입증되었으나 한 프로세스 충돌 시 전체 영향
  - 따라서 일부 기기에는 IOS 대신 마이크로 커널을 탑재한 다른 OS를 사용하기도 함

2. 장치 연결 방식
- 일반적으로 SSH 사용 (원격 관리)
- 초기 설정은 물리적 연결 필요 (콘솔 케이블 사용)

3. 구성(Configuration) 관리
- Running 구성: RAM에 저장, 즉시 적용, 휘발성
- Startup 구성: NVRAM에 저정, 재시작 시 적용, 비휘발성
- 변경사항 유지를 위해서는 Running 구성을 Startup 구성으로 복사 필요
  - 재부팅 만으로 설정 복구가 가능해서, 설정을 만지다가 발생하는 여러 문제를 쉽게 해결할 수 있도록 의도된 설계

### 기타 용어

Cisco Packet Tracer: 소프트웨어는 네트워크 환경을 시뮬레이션하는 도구로, 실제 라우터나 스위치 조작이 아님.

Cisco 문제 해결 방법론: https://github.com/chijoon-study/B-major-study/blob/main/CCNA/section_13/ysj/note.md