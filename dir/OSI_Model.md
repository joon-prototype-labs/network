OSI Model 관련 내용


### 4계층
https://github.com/chijoon-study/B-major-study/blob/main/CCNA/section_05/ysj/note.md - TCP, UDP

- **주요 역할**: Host 간 데이터 전송, Session Multiplexing
- **Port를 통한 통신**:
  - Port 기반 세션 관리
  - Host당 다중 세션 지원
  - Stateful 방화벽 식별 기능

- TCP vs UDP 비교
- **TCP 특징**:
    - 신뢰성 보장
        - 순서 보장
        - 세그먼트 누락 감지
        - 흐름 제어
    - 연결 기반 (3-Way/4-Way Handshake)
    - 20 Byte 헤더

- **UDP 특징**:
    - Best effort 방식
    - 비연결성
    - 신뢰성 없음
    - 8 Byte 헤더
    - 낮은 오버헤드

- 사용 상황
    - TCP: 신뢰성 중요
    - UDP: 실시간 처리 중요
    - 혼합 사용 가능 (예: DNS)

- TCP 연결 특성
    - 세그먼트 단위 3-way handshake
    - 연결 정보 교환 (syn, MSS 등)
    - TCB에 상대방 정보 저장
    - 보안성 ≠ 연결성


### 3계층 
https://github.com/chijoon-study/B-major-study/blob/main/CCNA/section_06/ysj/note.md   
https://github.com/chijoon-study/B-major-study/blob/main/CCNA/section_07/ysj/note.md    
https://github.com/chijoon-study/B-major-study/blob/main/CCNA/section_08/ysj/note.md    

- (추가로 다루는 내용)
    - 멀티케스트 동작 원리
    - 서브넷 내부, 서브넷 간의 통신, 서브넷의 이점 등

- **주요 역할**: 패킷 라우팅, 서비스 품질 관리
- **프로토콜**: IP (IPv4, IPv6), ICMP, IPSec
- **특징**: Connectionless

- 트래픽 유형
    - **Unicast**: 단일 호스트 전송
    - **Broadcast**: 모든 호스트 전송
    - **Multicast**: 그룹 전송 (효율적 분배)

- IP 클래스
    - **구분**: A, B, C (일반용), D (멀티캐스트), E (연구용)
    - **구조**: Network 부분 + Host 부분
    - **특수 주소**: 
    - 0.0.0.0/8: 현재 네트워크
    - 127.0.0.0/8: 루프백

- CIDR & 서브네팅
    - **CIDR**: Classless 주소 체계
    - 장점: 유연한 할당, 경로 요약 가능
    - **서브네팅**: 
    - 큰 네트워크를 작은 단위로 분할
    - 계산: 2^서브넷비트 (서브넷 수)
    - 호스트 수: 2^호스트비트 - 2

- 주요 개념
    - **VLSM**: 가변 길이 서브넷 - != FLSM
    - **Private IP**: 내부용 IP 주소
    - **NAT**: 사설IP-공인IP 변환
    - **IPv6**: IPv4 대체 프로토콜 (확장성)
        - 별개의 프로토콜임.
   
### 2계층
https://github.com/chijoon-study/B-major-study/blob/main/CCNA/section_10/ysj/note.md

- PDU (Protocol Data Unit)
    - **계층별 명칭**:
    - Data (응용)
    - Segment (전송)
    - Packet (네트워크)
    - Frame (데이터링크)
    - **특징**: 실제로는 하나의 PDU만 전송됨

- Layer 2 주요 특징
    - **주요 기능**:
    - 프레임의 비트 인코딩
    - 오류 감지/수정
    - 물리층 연결 준비

- 이더넷 (Ethernet)
    - **용도**: LAN 통신
    - **구성요소**:
    - 출발지 MAC 주소
    - 목적지 MAC 주소
    - 데이터

- MAC 주소
    - **구조**: 48비트
    - 앞 24비트: OUI (제조사)
    - 뒤 24비트: 고유 식별자
    - **특징**: 
    - 논리적 주소 지정 없음
    - 그룹화/관리 어려움
    - 네트워크 장비 식별용

- IP 사용 이유: MAC의 논리적 주소 지정 부재로 인한 대규모 인프라 관리의 어려움 해결


### 1계층
https://github.com/chijoon-study/B-major-study/blob/main/CCNA/section_09/ysj/note.md

- 주요 역할
- **비트스트림 전달**: 
  - 데이터 → 전기/광/라디오 신호 변환
  - 실제 물리적 전송 담당
- **하드웨어 제어**: 
  - 물리적 연결 관리
  - 전기/기계적 수준 제어
- TODO: 무선 기능 정리 추가

### 연결 매체 종류
1. **구리 케이블**
   - UTP (Unshielded Twisted Pair)
   - RJ-45 커넥터
   - 유형:
     - 직선 케이블: PC-스위치 연결용
     - 교차 케이블: 동종 장비 연결용
     - Auto MDI-X: 자동 신호 재구성

2. **광섬유 케이블**
   - 단일 모드: 장거리/고대역폭
   - 다중 모드: 중거리/저비용
   - 트랜스시버 필요: 광신호↔전기신호 변환

### PoE (Power over Ethernet)
- **기능**: 이더넷으로 전원 공급
- **용도**: IP 전화, 무선 AP
- **구성**:
  - PoE 스위치
  - 파워 인젝터 (외부 전원 연결용)