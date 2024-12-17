https://en.wikipedia.org/wiki/Region-based_memory_management

영역 이라는걸 만들고, 잦은 메모리 할당/해제 대신 큰 영역을 할당 or 해제하는 기법

rust 한국 디스코드를 보다가 https://news.hada.io/topic?id=17982 에 관한 부정적인 의견 (이 글에서 말하는 rust가 나쁘다는 게 실제론 해결 가능한 문제인데? 하는 식)이 달려서 추가로 더 공부해봄.

rust에서 RAII를 써서 메모리 할당이랑 해제(drop())이 빈번하게 발생할 수 있는 문제가 있다.

하지만 이건 arena를 사용해서 해결할 수 있다. (drop() 콜을 뭉친다고 표현하는 사람도 있었는데, 이게 arena를 말한건지 다른 방법을 말한건지는 모르겠다.)

그 방법으로 arena를 사용하면 된다. 영역 기반 메모리 관리의 축약 표현으로 보임.

rust에는 typed-arena라는 크레이트가 있는거 같음.

https://www.reddit.com/r/rust/comments/1etbfym/a_comparison_of_every_arena_in_rust/

이에 관해서 추천하는 자료

https://www.reddit.com/r/rust/comments/1etbfym/comment/lid68z4/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button


- https://www.gingerbill.org/series/memory-allocation-strategies/ << 이거는 나중에 정독해도 좋을듯? 메모리 관리 관점을 공부하기 좋아보임.
    - 사용자 단의 메모리 관리? 관점을 물어본다. 
- https://jacko.io/object_soup.html


추가: https://moosie.us/smart_blogs_and_talks << 어쩌다보니 본 어떤 사람의 블록인데, 꽤 재밌어보이는거 많음.


https://jacko.io/object_soup.html << 이거 재밌음. 
Rust에서 첨조 특히 양뱡항 참조 방식에 제약이 많아보니 ECS 패턴 같은 방식으로 해결하면 더 좋다는 내용.
ECS 패턴은 알고는 있었는데, 한번 찾아보면 좋을듯? 왜 멀티 스레드에 안전성이 더 높고 메모리 캐싱이 잘 되는지...
