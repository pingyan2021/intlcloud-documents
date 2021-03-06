### 액세스 모니터링의 대역폭 데이터는 어떻게 계산됩니까?
각 CDN 노드는 트래픽 데이터를 실시간으로 수집하여 센터에 보고되어 도메인 이름의 총 트래픽 데이터를 계산합니다. 기간에 따라, 트래픽/시간이 사용되고 디스플레이를 위해 대역폭 데이터로 변환됩니다.
**예시**
- 1분 동안 생성된 총 트래픽은 6MB이고 해당 대역폭은 (6 * 8)/60 = 0.8Mbps입니다.
- 대역폭 결제 시 5분 입상도 데이터 결산을 사용하고 해당 대역폭 값 = 5분 입상도 총 트래픽÷ 300초

### 트래픽 모니터링과 로그 컴퓨팅 트래픽이 맞지 않는 이유는 무엇입니까?
가속 도메인 이름 로그에 기록된 다운 스트림 바이트 통계에서 트래픽 데이터는 응용 계층 데이터입니다. 실제 네트워크 전송에서 생성된 네트워크 트래픽은 순수한 응용 계층 트래픽보다 5%-15% 더 많습니다.
- TCP/IP 헤더 소비: TCP/IP 프로토콜을 기반으로 하는 HTTP 요청 각 패킷의 최대 크기는 1500바이트이며 TCP 및 IP 프로토콜을 위한 40 바이트의 헤더를 포함합니다. 또, 응용 계층은 통계가 불가능하지만 이 부분은 약 3%인 것으로 계산됩니다.
- TTCP 재전송: 정상적인 네트워크 전송 중에는 전송된 네트워크 패킷 3%-10%가 인터넷에서 삭제됩니다. 삭제된 후에 재전송이 진행되며 이 부분의 데이터 응용 계층도 통계가 불가능하지만 비율은 약 3%-7%입니다.

업계 표준으로 요금 트래픽은 일반적으로 응용 계층 트래픽과 위의 비용을 기반으로 하며 Tencent Cloud CDN은 10%를 차지하므로 모니터링 트래픽은 로그 계산 트래픽의 약 110%입니다.

### 트래픽 명중율은 어떻게 계산합니까?
기본적으로 CDN은 L2 캐시(엣지 레이어, 중간 레이어)를 설정하며, CDN의 임의의 한 레이어에서 명중하기만 하면 요청에 응답하고 도달 CDN 노드로 계산됩니다.
트래픽 명중율 = (총 다운 스트림 트래픽-원본 가져오기 트래픽)/총 다운 스트림 트래픽

### 낮은 트래픽 명중율을 처리하는 방법은 무엇입니까?
- 캐시 제거가 진행 여부 확인: 캐시 제거는 노드에서 지정된 콘텐츠를 지우고 짧은 시간 내 명중율이 감소합니다.
- 원본 서버에 새로운 리소스가 존재 여부 확인:. 원본 서버에 많은 새로운 리소스가 있어 CDN 노드 원본 가져오기가 발생하여 트래픽 명중율이 감소합니다.
- 원본 서버가 비정상 여부 확인: 원본 서버가 장애가 발생하고 5XX 또는 4XX일 때, 트래픽 명중율에 영향을 줄 수 있습니다.
- 캐시 만료 정책이 정상 설정 여부 확인: 콘솔 캐시 구성의 캐시 만료 설정 섹션 확인이 필요합니다. 캐시 만료 규칙의 우선순위는 위에서 아래로 (낮은 순서에서 높은 순서로), 즉 낮은 캐시 정책은 상위 캐시 정책을 덮어 씁니다.
- Range 원본 가져오기 활성화 여부: 콘솔 원본 가져오기 구성에서  "Range 원본 가져오기"를 확인하십시오. Range 원본 가져오기가 꺼져 있으면 가져오기 시 요청에 따라 파일을 가져오는 게 아니라 전체 파일을 가져오게 됩니다. 또, 원본 가져오기 트래픽을 증가시키기 때문에 트래픽 명중율에 영향을 줍니다.
- 필터링 파라미터 사용 여부 확인: 콘솔 액세스 구성에서 필터링 파라미터 확인을 하여야 합니다. 필터링 파라미터를 사용하지 않으면 전체 경로가 캐시됩니다. 동일한 리소스의 파라미터가 요청되면 캐시 할 수 없으므로 트래픽 명중율에 영향을 줍니다.

### 상태 코드 통계는 생성 된 모든 상태 코드를 계산합니까?

CDN 통계 분석 새 버전이 온라인 상태가 되면 원본 서버에서 생성된 상태 코드가 있는 해당 모니터링 곡선이 생성되어 비정상적인 문제를 해결할 수 있습니다.

### 지역 및 ISP 통계 데이터는 어떻게 계산합니까?
지역 및 ISP 통계 데이터는 Client IP 정보를 사용하여 액세스 로그에서 계산되며 순수한 로그 계산이 사용되므로 "모든 지역" 및 "모든 ISP"를 누적하여 사용되는 과금 데이터가 사용되지만 약간의 차이가 있습니다. 자세한 내용은 위의 두 번째 질문을 참조하십시오.




