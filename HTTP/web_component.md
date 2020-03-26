## 8. 웹의 구성요소

---

### 프록시 (Proxy)

클라이언트와 서버 사이에 위치한 HTTP 중개자

웹 보안, 어플리케이션 통합, 성능 최적화를 위한 구성요소
사용자를 대신하여 서버에 접근
모든 웹 트랙픽 중 신뢰할 만 한 중개자 역할을 함

`Client ↔ Proxy ↔ Server`

### 캐시 (Cache)

많이 찾는 웹 페이지를 클라이언트 가까이에 보관하는 HTTP 창고

성능 향상을 위해 자주 찾는 문서의 사본을 저장해 둠

`Client ↔ Proxy (Proxy Cache) ↔ Server`

### 게이트 웨어 (Gateway)

다른 어플리케이션과 연결되는 특별한 웹서버

HTTP 트래픽을 다른 프로토콜로 변환 하기 위해 사용 됨

`HTTP Client ↔ HTTP/FTP Gateway ↔ FTP Server`

### 터널 (Tunnel)

단순히 HTTP 통신을 전달하기만 하는 특별한 프록시

- SSL

    [[정보보안] SSL(Secure Socket Layer) 이란](https://12bme.tistory.com/80)