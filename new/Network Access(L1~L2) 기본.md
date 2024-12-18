
OSI 기준 3계층이 아니라 1~2 계층을 다룸.

물리적인 변환 과정이나 그걸 Host에 전기적, 물리적 신호로 보내는거, 연결하는거 (NIC) 등을 다룸.

이더넷 같은게 여기 포함.

따라서 IP를 모름. 대신 Mac 주소를 통해서 통신한다.

그래서 서브 그룹 단위로는 안되고, 보낼 수 있는 전부 or 특정 MAC에 한번씩 만 가능함.

인프라, 백본 관련 내용은 별도로 분리하는게 좋을듯? 라우팅이나 MPLS이나 VLAN이나...

일단 책 내용 키워드 위주로 정리 -> 그 외 기타 자료로 추가 보완 -> 책 다시 보고 정리 -> 위치 나누기 등...

너무 딥하게는 하지 말고, 결론 위주로, 그런건 책 보면 되니까.


- 6.1 링크 계층 소개
    - 노드: 링크 계층 프로토콜을 실행하는 장치
    - 링크: 통신 경로상의 인접한 노드들을 연결하는 통신 채널, 데이터가 이동하는 경로 (데이터를 받고 다른 곳으로 넘겨주는 곳 hop? host? 사이사이마다 있음. 여러 링크를 통해서 트래픽이 host to host로 전달)
- 6.1.1 링크 계층이 제공하는 서비스 - 항상 지원하는 건 아님. 일부만?
    - 프레임화(framing)
        - 링크 계층 프레임에 캡슐화
    - 링크 접속(link access)
        - ?? 이해 잘 못함.
    - 신뢰적 전달 
        - TCP처럼 확인 응답과 재전송을 통해 신뢰적 전달. 단 누락이 잘 되는 무선에서만, 유선의 경우 제공 X
    - 오류 검출과 정정
        - 상위 계층의 오류 검출보다 일반적으로 더 복잡하며, 하드웨어로 구현된다.
        - 오류 정정은 어느 부분에서 에러가 발생했는지 정확하게 잡아낸다. - 이거 영어 표현 궁금함. 한글은 좀 비직관적인데.
- 6.1.2 링크 계층이 구현되는 위치
    - 호스트에서 대부분의 경우 링크 계층은 네트워크 인터페이스 컨트롤러(network interface controller - 요즘엔 card라고 더 많이 부르는듯?, NIC)로 알려진 네트워크 어댑터(network adapter) 에 구현된다.
    - NIC는 어떻게 통신하는가? 
        - 책: controller(물리 -> 전기 신호 변환) -(데이터버스를 통해서)> CPU(인터럽트 발생)
        - 따로 찾은거:  
            - 현대 OS는 다른 하드웨어를 다루는 것처럼 똑같이 다룬다. 
            - NIC는 이더넷 카드, 무선 LAN 어댑터 등 다양한 형태로 제공되며, 최근에는 NIC가 메인보드에 통합된 형태로도 많이 사용된다.
            - NIC는 하드웨어 기기이다. 이에 호환되는 드라이버가 있고, 드라이버는 OS 규칙에 맞게 인터럽트를 발생시킨다.
            - 즉 NIC -> 드라이버 -> 인터럽트 발생([MSI](https://en.wikipedia.org/wiki/Message_Signaled_Interrupts), [DMA](https://en.wikipedia.org/wiki/Direct_memory_access) 등 드라이버 구현따라 다름) -> CPU가 다른 인터럽트와 마찬가지로 동일하게 처리
            - USB to RJ45 어댑터 같이 노트북에 랜 끼우는것도 NIC의 일종으로 볼 수 있음.
            - NIC 하드웨어는 인터럽트만 외에도 링크 계층의 기능인 패킷 버퍼링(Buffering), 에러 검출(Error Detection), 흐름 제어(Flow Control) 
            - NIC가 하는 일
                - 네트워크 매체(예: 이더넷 케이블, 무선 신호)와의 물리적 상호작용. 
                - 물리적 <-> 전기적 신호 변환 
                - 물리적 인터페이스 (RJ45, Wi-Fi 어댑터) 제공
            - NIC 동작
                - (1) 물리적 신호를 프레임으로 변환
                - (2) 에러 검출 및 처리 
                - (3) 흐름 제어 및 버퍼링 수행. 
                - 이후 인터럽트를 발생시켜 OS에게 프레임 정보를 넘긴다.
            - ref: 
                - https://en.wikipedia.org/wiki/Network_interface_controller : 더 찾아봐야함. 부족한 부분도 많음.
                - https://www.geeksforgeeks.org/nic-full-form/ 
                - https://gist.github.com/bondit-sijunyang/e1154b3c908744ee64a721a3b9ecd5ef << AI 답변이긴 한데, 이런 부분은 꽤 정확하니까...



> 1, 2 계층 분리하는게 나을지도
> 요즘에는 1계층의 이더넷같은게 많이 나와서...
> 2계층이면 MAC, [LLC](https://en.wikipedia.org/wiki/Logical_link_control), NIC 같은 개념 정도?

- https://www.destroyallsoftware.com/compendium/network-protocols?share_key=97d3ba4c24d21147 << 여기 물리적 부분
- https://github.com/IT-Book-Organization/Computer-Networking_A-Top-Down-Approach/tree/main/Chapter_6/6.1%20%EB%A7%81%ED%81%AC%20%EA%B3%84%EC%B8%B5%20%EC%86%8C%EA%B0%9C