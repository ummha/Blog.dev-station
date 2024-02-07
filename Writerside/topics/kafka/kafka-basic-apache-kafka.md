# 아파치 카프카(Apache Kafka)란?

Apache Kafka는 실시간으로 기록 스트림을 게시, 구독, 저장 및 처리할 수 있는 분산형 데이터 스트리밍 또는 이벤트 스트리밍 플랫폼입니다. 여러 소스에서 데이터 
스트림을 처리하고 여러 사용자에게 전달하도록 설계되었습니다. 간단히 말해 A지점에서 B지점까지 이동하는 것뿐만 아니라 A지점에서 Z지점을 비롯해 필요한 모든 
곳에서 대규모 데이터를 동시에 이동할 수 있습니다.

Apache Kafka는 전통적인 엔터프라이즈 메시징 시스템의 대안입니다. 하루에 1조 4천억 건의 메시지를 처리하기 위해 LinkedIn이 개발한 내부 시스템으로 
시작했으나, 현재 이는 다양한 기업의 요구 사항을 지원하는 애플리케이션을 갖춘 오픈소스 데이터 스트리밍 솔루션이 되었습니다.

![kafka-apache-kafka](kafka-apache-kafka.png "apache kafka") {border-effect="rounded"}

## Event

Event는 비즈니스에서 일어나는 모든 일(데이터)를 의미합니다. 예를 들어 웹사이트에서 무언가를 클릭하는 것, 청구서 발행, 송금, 배송 물건의 위치 정보, 
택시의 GPS 정보, 센서의 온도/압력 데이터 등 Event란 비즈니스에서 일어난 모든 데이터를 의미합니다. 주로 메시징 시스템(Messaging System)에서 중간 
매개체 역할로 사용하거나 IOT 디바이스로부터 데이터 수집, 애플리케이션에서 발생하는 로그 수집, Realtime Event Stream Processing(Fraud Detection, 이상 감지 등)와
DB 동기화(MSA 기반의 분리된 DB간 동기화)를 위해 사용되거나, 실시간 ETL(Extract, Transform, Load)에서도 활용되고 Spark, Flink, Storm, 
Hadoop과 같은 빅데이터 기술과 함께 사용됩니다.

따라서, Event는 빅데이터의 특징을 가집니다. 비즈니스 모든 영역에서 광범위하게 발생하며 대용량의 데이터(Big Data)가 발생되기 때문에 
Event Stream은 연속적인 많은 이벤트들의 흐름을 의미합니다.

## Apache Kafaka 주요 특징 3가지

1. 이벤트 스트림을 안전하게 전송합니다. (Publish & Subscribe)
2. 이벤트 스트림을 디스크에 저장합니다. (Write to Disk)
3. 이벤트 스트림을 분석 및 처리합니다. (Processing & Analysis)

