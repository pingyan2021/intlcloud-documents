## 부가 서비스 요금

부가 서비스란 IM, 릴레이 라이브 방송, 클라우드 녹화, 클라우드 혼합 스트리밍 트랜스 코딩, 음란물 감지 화면 캡처 등을 말하며, 해당 기능들은 IM, LVB, VOD 등 기타 Tencent Cloud 제품과 결합해야만 이용할 수 있습니다. 모든 부가 서비스는 별도의 과금 규정이 있으며, 관련 요금은 상응하는 클라우드 서비스에서 정산됩니다.
**IM은 기본적으로 무료 TRTC 체험 버전이 활성화되며, 다른 부가 서비스 기능은 모두 기본적으로 비활성화되어 있습니다. 활성화 후 사용하지 않는 경우 요금이 부과되지 않습니다.**


##IM 관련 요금

동일한 제품 내에서 동시에 TRTC와 IM 서비스를 편리하게 통합할 수 있습니다. TRTC 애플리케이션 생성 시 시스템이 자동으로 TRTC 애플리케이션과 관련된 SDKAppID의 IM 애플리케이션을 생성하며, IM 서비스에서는 1:1 채팅, 그룹 채팅, 정보 푸시, 자료 관계 체인 호스팅, 계정 인증 등 IM 기능을 제공합니다.

| 부가 서비스 항목       | 과금 제품                                                     | 과금 상세 내용                                                     |
| :----------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| IM 기능 | [IM](https://intl.cloud.tencent.com/document/product/1047) | IM의 TRTC 체험 버전은 영구 무료, 실제 수요에 따라 각각의 IM 버전 구매 가능 |

>?TRTC 애플리케이션과 IM 애플리케이션의 SDKAppID가 동일한 경우, 두 서비스의 계정과 인증을 중복 사용할 수 있습니다.

## 릴레이 라이브 방송 관련 요금

릴레이 라이브 방송 기능은 기본적으로 비활성화 상태입니다. 기능 소개 및 사용 방법은 [CDN 릴레이 라이브 방송](https://intl.cloud.tencent.com/document/product/647/34617)을 참조하십시오.

| 부가 서비스 항목       | 과금 제품   | 과금 상세 내용                                                     |
| :----------- | :--------- | :----------------------------------------------------------- |
| CDN 릴레이 라이브 방송 | LVB | **트래픽** 또는 **대역폭**에 따라 과금, 실제 수요에 따라 적합한 과금 방식 선택 가능, 기본적으로 트래픽에 따라 과금 |

## 클라우드 녹화 관련 요금

클라우드 녹화 기능은 기본적으로 비활성화 상태입니다. 기능 소개 및 사용 방법은 [클라우드 녹화](https://intl.cloud.tencent.com/document/product/647/35152)를 참조하십시오.

| 부가 서비스 항목       | 과금 제품                                                     | 과금 상세 내용                                                     |
| :------------------------- | :--------- | :----------------------------------------------------------- |
| 라이브 방송 녹화                   | LVB | **당월 라이브 방송 녹화 동시 피크 채널 수**에 따라 과금    |
| 비디오 파일 저장               | VOD | **녹화 파일을 저장하는 VOD 플랫폼의 저장 용량**에 따라 과금 |
|녹화된 비디오 파일 재생 또는 다운로드 | VOD | **다운스트림 가속 트래픽**에 따라 과금                   |

>?클라우드 녹화 기능 사용으로 인해 녹화 비용 청구 시, 트래픽/대역폭 비용은 중복으로 청구되지 않습니다.

## 클라우드 혼합 스트리밍 트랜스 코딩 관련 요금

클라우드 혼합 스트리밍 트랜스 코딩 기능은 기본적으로 비활성화 상태입니다. 기능 소개 및 사용 방법은 [클라우드 혼합 스트리밍 트랜스 코딩](https://intl.cloud.tencent.com/document/product/647/34618)을 참조하십시오. 해당 기능을 사용할 경우 LVB를 활성화해야 하며, 비즈니스 수요에 따라 LVB 콘솔에서 트랜스 코딩 설정 이 필요합니다.

| 부가 서비스 항목           | 과금 제품                                                 | 과금 상세 내용                                                     |
| :--------------- | :------------------------------------------------------- | :----------------------------------------------------------- |
| 클라우드 혼합 스트리밍 트랜스 코딩 기능 | [LVB](https://intl.cloud.tencent.com/document/product/267) | **각각의 코딩 방식과 해상도별 클라우드 혼합 스트리밍 트랜스 코딩 시간**에 따라 과금 |

## 음란물 감지 화면 캡처 관련 요금

음란물 감지 화면 캡처 기능은 기본적으로 비활성화 상태입니다. 기능 소개 및 사용 방법은 [음란물 감지 화면 캡처](https://intl.cloud.tencent.com/document/product/267/31072)를 참조하십시오.

| 부가 서비스 항목   | 과금 제품                                                 | 과금 상세 내용                                  |
| :------- | :------------------------------------------------------- | :---------------------------------------- |
| 라이브 방송 화면 캡처 | [LVB](https://intl.cloud.tencent.com/document/product/267) | **화면 캡처 수량**에 따라 과금    |
| 스마트 음란물 감지 | [LVB](https://intl.cloud.tencent.com/document/product/267) | **음란물 감지 이미지 수량**에 따라 과금 |
