---
layout: post
title: 엘라스틱서치[Elastic Search] - 설치와 실행 #1
description: >
  ## 엘라스틱서치 시작하기 [Getting Started]
  ####엘라스틱서치[Elastic Search]란?
  엘라스틱서치는 실시간 검색이 가능한 오픈소스 분산 검색엔진으로, 풀텍스트 검색엔진 라이브러리인 아파치 루씬(Apache Lucene)을 기반으로 만들어진 소프트웨어이다.
  엘라스틱서치는 방대한 양의 비정형 데이터를 인덱싱하고 다수의 쿼리를 동시에 처리해 누구나 쉽고 빠르게, 효율적인 데이터관리가 가능하도록 도와준다.
---

### 엘라스틱서치 설치 [Installing Elastic Search]

엘라스틱서치를 사용하기 위해서는 JAVA가 필요하다.
JAVA공식 사이트 ([www.java.com](http://)) 에서 최신 버전의 자바를 다운로드하여 설치하자.

[elasticsearch.org/download](http://) 에서 최신 버전의 엘라스틱서치를 다운받을 수 있다.

```
curl -L -O http://download.elasticsearch.org/PATH/TO/VERSION.zip
unzip relimentsearch-$VERSION.zip
cd relimentsearch-$VERSION
```
엘라스틱서치는 위에 나온 코드를 입력하여 설치하거나, 다운로드 페이지에서 제공되는 Debian 또는 RPM패키지를 이용해 설치할 수 있다.

### 마블 설치 [Installing Marvel]

마블(Marvel)은 엘라스틱서치를 위한 관리 및 모니터링 툴로서 개발 시 무료로 사용할 수 있다. ~~(MCU의 그Marvel이 아니다.)~~
마블은 센스(Sense)라는 인터랙티브 콘솔과 함께 제공되는데, 이것은 브라우저에서 엘라스틱서치와 직접 대화하는 것을 용이하게 해준다.
마블은 `plugin`으로 이용할 수 있다. 마블을 설치하려면 `elasticsearch` 디렉토리에서 다음 명령을 실행하자.

```
./bin/plugin -i elasticsearch/marvel/latest
```

데이터를 수집하지 않도록 설정하거나, 로컬 클러스터 모니터링을 원하지 않을 경우에는 다음 명령을 실행하도록 하자.

```
echo 'marvel.agent.enabled: false' >> ./config/elasticsearch.yml
```

### 엘라스틱서치 실행하기 [Running Elastic Search]

위의 설치를 모두 완료하였다면 이제 foreground에서 다음 명령으로 엘라스틱서치를 실행할 수 있다.

```
./bin/elasticsearch
```
background에서 데몬으로 실행하려면 `-d`옵션을 추가하여 실행하자.
다른 터미널을 열어 테스트를 진행한다.
```
curl 'http://localhost:9200/?pretty'
```
output이 다음과 같다면, 정상적으로 설치된 것이다.

```
{   
	"status": 200,
    "name": "Shrunken Bones",
    "version": {
    	"number": "1.4.0",
        "lucene_version": "4.10"
	},
    "tagline": "You Know, for Search"
}

```
이는 엘라스틱서치 클러스터가 가동되고 있다는 것을 의미하며, 이제 본격적으로 엘라스틱서치를 사용할 수 있다.

