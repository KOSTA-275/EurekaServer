![EurekaServer](https://github.com/user-attachments/assets/ac75783c-e525-49e7-8806-b214b2139f32)

# 클라이언트 등록
모든 마이크로서비스의 서버와 GateWay Server는 Eureka Client를 등록 하여야 합니다.


# 모니터링 서버
Eureka Server는 등록된 Eureka Client들을 모니터링하는 서버이고 
30초 주기마다 Eureka Client들은 서버 상태를 Eureka Server에 보고합니다.

# 필수 의존성
빌드도구 : Gradle
<br>
유레카 서버
<br>
dependencies {
	implementation 'org.springframework.cloud:spring-cloud-starter-netflix-eureka-server'
}
<br>
유레카 클라이언트
<br>
dependencies {
	implementation 'org.springframework.cloud:spring-cloud-starter-netflix-eureka-client'
}

# 사용 이유

GateWay Server는 들어온 요청을 알맞은 마이크로서비스 서버로 라우팅해주는 역할을 합니다.

이때 요청이 많아지면 Gateway 서버는 부하를 백엔드 서비스로 전달하게 되는데

클라우드 서비스에서 스케일 아웃을 통해 백엔드 서버의 인스턴스를 늘려 부하를 분산시킬수도 있습니다.

하지만 이때 늘려버린 인스턴스의 엔드포인트를 GateWay Server는 모르게 되고 라우팅을 할 수 없게 됩니다.

Eureka Server에서 이 Eureka Client를 Client Name 리스트로 가지고 있고 그걸 Eureka Client로 등록된 GateWay Server에 알려주기 위함입니다.
