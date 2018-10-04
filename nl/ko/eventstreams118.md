---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 파티션 리더십
{: #partition_leadership }

각 파티션에는 파티션의 리더 역할을 하는 클러스터의 서버 하나와 팔로워의 역할을 하는 다른 서버들이 있습니다. 파티션에 대한 모든 생성 및 이용 요청은 리더에 의해 처리됩니다. 팔로워는 리더에 대한 최신 정보를 알기 위해 리더의 파티션 데이터를 복제합니다. 팔로워가 파티션 리더의 최신 정보를 계속 확인하는 경우 팔로워의 복제본이 동기화됩니다. 

메시지가 파티션 리더에게 전송되는 경우 이용자가 바로 해당 메시지를 사용할 수는 없습니다. 리더는 파티션에 메시지의 레코드를 추가하며 여기에 해당 파티션의 다음 오프셋 숫자를 지정합니다. 동기화 복제본에 대한 모든 팔로워가 레코드를 복제하고 이 복제본에 레코드를 썼다고 확인하면 레코드가 *커미트*됩니다. 이용자는 메시지를 사용할 수 있습니다.

파티션의 리더가 실패하면 동기화 복제본을 가진 팔로워 중 하나가 자동으로 파티션 리더가 됩니다. 실제로 모든 서버는 일부 파티션의 리더이면서 다른 파티션의 팔로워입니다. 파티션의 리더십은 동적이며 서버가 생기거나 없어질 때마다 변경됩니다.

애플리케이션은 파티션 리더십의 변경을 처리하기 위해 특정 조치를 수행하지 않아도 됩니다. 클러스터가 안정되는 동안 대기 시간은 늘어나지만, Kafka 클라이언트 라이브러리는 자동으로 새 리더에 다시 연결됩니다.