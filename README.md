Eureka Server는 마이크로서비스 서버들을 모니터링하는 서버입니다.

모든 마이크로서비스의 서버는 Eureka Client를 등록 하여야 합니다.
GateWay Server 또한 Eureka Client에 등록 해주어야 합니다.
그 이유는
GateWay Server는 들어온 요청을 알맞은 마이크로서비스 서버로 라우팅해주는 역할을 합니다.
이때 요청이 많아지면 Gateway 서버는 부하를 백엔드 서비스로 전달하게 되는데
백엔드 서비스의 인스턴스가 부족하면 클라우드 서비스에서 스케일 아웃을 통해 백엔드 서버의 인스턴스를 늘려 부하를 분산시킬수도 있습니다.(설정을 통해)
하지만 이때 늘려버린 인스턴스의 엔드포인트를 GateWay Server는 모르게 되고 라우팅을 할 수 없게 됩니다.
Eureka Server에서 이 Eureka Client를 Client Name 리스트로 가지고 있고 그걸 Eureka Client로 등록된 GateWay Server에 알려주기 위함입니다.
