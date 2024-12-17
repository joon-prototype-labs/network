# 네트워크 참조 모델의 이해

## 1. 서론

OSI 7계층 모델은 이론적인 참조 모델로, 네트워크 통신을 이해하고 설명하기 위한 개념적인 모델이다.

TCP/IP는 실제 사용되는 프로토콜 모음(Protocol Suite)으로, TCP/IP 모델은 TCP/IP 프로코톨을 계층별로 구분한 모델이다.

> [NOTE] Suite는 Set의 격식있는 표현으로 "집합"정도로 해석 가능하다.

**한줄 요약: "OSI는 개념적인 모델이고 TCP/IP는 실질적인 프로토콜 집합으로 구성된 모델이다."**

## 2. OSI 모델

### 2.1 개요

OSI(Open Systems Interconnection) 모델은 ISO(국제표준화기구, International Organization for Standardization)에서 개발한 모델이다.

각 계층은 특정 작업을 처리하는 책임을 가진다. 

본인 계층의 위와 아래의 계층과만 통신할 수 있는 엄격한 계층화를 준수해야 한다.

### 2.2 계층 구조의 특징

OSI 모델은 하위 계층(1~3)과 상위 계층(4~7)으로 나눌 수 있으며, 각각의 관심사가 다르다:
- 하위 계층(1~3): 물리적인 데이터 전송, 전송하는 것 자체에 중점
- 상위 계층(4~7): 신뢰성 검사, 에러 검출 및 복구, 응용 프로그램 간 통신 서비스 제공

### 2.3 OSI 7 Layer 설명

- L1(Physical): 비트 단위의 물리적 데이터 전송 (Hub, 케이블)
- L2(Data Link): MAC 주소 기반의 물리적 통신 (Switch, NIC, ARP)
- L3(Network): IP 주소 기반의 논리적 통신과 라우팅 (Router, IP)
- L4(Transport): 포트 기반의 프로세스 간 (신뢰성이 있을 수도 있는) 통신 (TCP/UDP)
- L5(Session): 애플리케이션 간의 세션 연결 관리 
- L6(Presentation): 데이터 형식 변환, 암호화, 압축 
- L7(Application): 사용자 레벨의 애플리케이션 프로토콜 

(실제 5~7계층은 구분이 모호하므로 특정 프로코톨을 적지 않음)

## 3. TCP/IP 모델

### 3.1 개요

TCP/IP는 인터넷과 네트워크에서 사용하는 프로토콜 스택의 집합이다. 

TCP와 IP를 기반으로 하는 프로토콜이 많아서 이런 이름이 붙었으며, TCP, IP 프로토콜과는 별개이다.

### 3.2 특징
- 4계층으로 구성된 실용적 모델
- 인터넷의 실제 구현 표준
- 이론보다는 실용성에 중점

> **[NOTE] TCP/IP는 5계층이다?**    
> 
> 전통적으로는 4계층이나, TCP/IP Updated Model을 사용해서 5개 layer를 가진다는 주장이 있다.     
> TCP/IP Updated Model은 기존의 네트워크 인터페이스 계층을 데이터 링크, 물리 계층으로 분리한다.   
> 
> 이에 관한 2가지 상반되는 의견을 보자.   
> 1. 4계층: [RFC 1122](https://datatracker.ietf.org/doc/html/rfc1122)에서는 4개의 계층으로 소개하고, 그 이후 갱신되지 않았다.     
> 2. 5계층: [구글에서 만든 영상](https://youtu.be/2qRcOfj5tbA?si=aiEmy0afdDLliERX)에서는 5계층 버전으로 설명한다. 즉, 공식적인 표준은 아니나 현실 세계에 더 적합한 모델로 보는 사람들이 많다.   
>
> 따라서 TCP/IP가 어떤 계층이라고 명확하게 말하기는 어려워 보인다. 표준(RFC1122)과 사실상 표준(de facto standard) 중 어떤것이 실무자의 입장에서 올바른지는 판단하기 어렵다.   
> (이더넷의 발전과 표준화로 인해서 네트워크 인터페이스 계층을 데이터 링크, 물리 계층으로 분리하여 보게 되는것으로 보인다. - 출처 명확하지 않음.)    
> 결론적으로, 둘 다 알아야 한다고 생각한다.

### 3.3 계층 구조
1. 응용 계층(Application): OSI의 5-7계층 통합
2. 전송 계층(Transport): TCP, UDP 프로토콜
3. 인터넷 계층(Internet): IP 프로토콜
4. 네트워크 접근 계층(Network Access): 물리적 네트워크 연결

## 4. 실제 네트워크에서의 적용

### 4.1 실제 구현의 특징
- 대부분의 현대 네트워크는 TCP/IP와 이더넷으로 구현
    - AppleTalk, IPX/SPX 같이 다른 Protocol Suite도 있었으나, TCP/IP가 표준이 되면서 더 이상 쓰이지 않게 됨.
- 프로토콜이 특정 계층에 엄격히 속하지 않는 경우도 존재
- RDMA (Remote Direct Memory Access, RFC 5040)와 같이, 기존 네트워크 모델의 계층을 무시하는 프로토콜도 있음.

### 4.2 두 모델의 관계
- OSI 모델: 네트워크 통신의 이론적, 교육적 목적
- TCP/IP 모델: 실제 인터넷 구현에 초점
- 실무에서는 TCP/IP 모델을 기반으로 하되, OSI 모델의 개념적 프레임워크를 참조하는 방식으로 활용
    - RFC 문서에서 OSI 모델을 예시로 드는 경우도 있음. (RFC 1122, RFC 3439)


# Related Pages

- TODO: 앞으로 추가할 OSI, TCP 관련 더 구체적인 페이지
- TODO: 네트워크의 역사

# References

- [Cloudflare - OSI Model](https://www.cloudflare.com/ko-kr/learning/ddos/glossary/open-systems-interconnection-model-osi/)
- [Wikipedia - OSI Model](https://en.wikipedia.org/wiki/OSI_model)
- [Wikipedia - TCI/IP(Internet Protocol Suite)](https://en.wikipedia.org/wiki/Internet_protocol_suite)
- [RFC 1122](https://datatracker.ietf.org/doc/html/rfc1122)
- [RFC 1180](https://datatracker.ietf.org/doc/html/rfc1180): Tutorial of TCP/IP protocol suite
- 컴퓨터 네트워크 햐향식 접근 1장
- [이전에 내가 정리한 네트워크 노트](https://github.com/YangSiJun528/memory/blob/master/notes/Computer%20Science/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC%20%EA%B8%B0%EC%B4%88%20%EA%B0%9C%EB%85%90.md)