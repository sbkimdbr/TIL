데이터를 하이브를 통해 빅데이터에 넣어보자

스프링 웹애플리케이션 아래에 로그 파일을 남긴다.

로그 남기면 하이브를 통해서  빅데이터 시스템에 넣으면 로그 파일은 여러가지 시나리오가 있다 사용자자가 클릭하면 클릭정보를 로그에 남길 수 있고, 사용자가 클릭하지 않고 (웹이 아니고 IOT 신호- 차량의 주행, 위치 등의 정보를 실시간으로 로그로 쌓는다/ 스마트 팩토리의 경우 공장의 여러 라인이나 여러 장비들에서 올라오는 정보를 로그에 계속 쌓는다

삼성전자의 경우 공장이 멈추는 것은 엄청난 손해이므로 온도 습도등 그러한 것들의 변화를 주기적으로 감지하고, 변화가 있는 지점에 대해서 그 장치에 대해 교체하고 정비

올라오는 로그를 분석해서 여러가지 데이터가 올라오면 로그에 찍어서 분석한다. )

-이런 시스템 구성도 안에서 프로젝트를 진행하였다. 깃허브에다가 시스템 구성도와 더불어 개발 언어, 특징, 결과화면 , 소스 올려 리눅스, 하둡 연결, 

웹은 하이브의 데이터를 제이슨으로 가져와서 시각화 하는 것 



웹, 장비에서 클릭이 일어났을 때 로그를 데이터 형태로 찍는 것 - 0928

VMWARE에 웹 애플리케이션을 구축하고 리눅스 위에 

하둡 구축하는 명령어 흐름, 하이브 구축 흐름, 웹을 구축, 로그 쌓는 흐름 



클릭 하면 차트를 뿌리는 것 하둡의 데이터 분석해서 제이슨으로 받아서 화면에 출력해줌

이번엔 클릭-데이터 분석-



사용자들이 상품을 클릭한다- 서버동작-클릭 데이터를 로그에 찍으려고 함



로그인 안했을 때 클릭해도 정보를 수집할 수 없다

로그인 하면 로그인 정보에 대한 로그도 아

해당하는 아이디에 대해 컨트롤러에서 받을 수 있도록 만든다.

찍힌걸 파일로 남기고자 한다

main의 세션으로 



```java
log4j.logger.user = DEBUG, console, user
log4j.logger.work = DEBUG, console, work
log4j.logger.data = DEBUG, console, data
    //debug - 실제 파일에 저장 함
    
```

함수 동작전, 이후, 

aspect orinet project

```java
work 라고 정의 한 내용으로 찍겠다
   
```



req의 내용을 

컨트롤러의 내용을 하나의 옵젝으로 보내겟다 클릭의 이름이ㅡㄹ



로그는 biz에서 찍는다

아이템 클릭 함수가 실행될 때 현재는 로그에는 어떠한 함수가 실행되는지만 찍힌다

이제는 아이템 클릭의 아규먼트를 클릭으로 남기고 싶다 

로그를 남겨서 

온라인 비즈니스 - 로그로 분석해서 비쥬얼 라이즈할 수 있는 것

도식화를 어떻게 할지 



window 에서 생성한 파일

톰캣으로 접속 할 수 있다

리눅스에는 하이브와 아파치 톰캣이 연결되어 있다

apache tomcat 설치

/root/logs

hive.war 실행 

리눅스에서 하이브가 어떻게 실행되는지 

```java
@Service
public interface Shop<T> {
 public void itemClick(T t);
}


@Service
public class ShopBiz implements Shop<Click> {

    @Override
	public void itemClick(Click t) {
		System.out.println(t);
	}
}
```

```bash
[root@hadoop ~]# chmod 777 logs
[root@hadoop ~]# ls -l

drwxrwxrwx --작성할 수 있도록 

[root@hadoop ~]# cd /var/ftp/pub
[root@hadoop pub]# ls
hive.war
[root@hadoop pub]# cp hive.war /usr/local/apache-tomcat-9.0.38/webapps
[root@hadoop pub]# cd /usr/local/apache-tomcat-9.0.38/webapps
[root@hadoop webapps]# ls
ROOT  docs  examples  hive  hive.war  host-manager  manager


```



hadoop에 structure을 만들어주는것이 첫번째 

CREATE TABLE shopclick(

date STRING,

fn STRING,

id STRING,

item STRING,

price INT,

age INT,

gender STRING

)

PARTITIONED BY (logdate)

ROW FORMAT DELIMETED

FIELDS TERMINATED BY ','

LINES TERMINATED BY '\n'

STORED AS TEXTFILE; 



```bash
CP data.log data.log.2020-09-28

//크론탭 동작 스크립트
vi hive.sh 
//위에것만 복사해서 추가 (echo filename 까지)
//FILENAME ="data.log.$partitionName"

chmod 777 hive.sh
hive.sh 
vi hive.sh 
//echo 부터 모두 복사해서 넣기 
// 1. /root/logs/  2.table shopclick  parti
```



cronetab 에 의해 작동되어 하둡에 저장된다

빅데이터 시스템으로 들어갈 수 있는 테이블까지 완성시킴

로그 부분까지 넣을 수 있다.



여러가지 장비로 올라오는 데이터를 올리겠다

sendData 에 들어온 데이터를 웹애플리ㅋ케ㅣ이션으로 날린다

빅데이터에 저장된 값을 분석해서 차트에 

[root@hadoop ~]# cd /var/ftp/pub

cp hive.war /usr/local/apache-tomcat-9.0.38/webapps

[root@hadoop pub]# cd /usr/local/apache-tomcat-9.0.38/webapps



```javascript
<%@ page language="java" contentType="text/html; charset=UTF-8"
	pageEncoding="UTF-8"%>
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>

<style>
#container {
	width: 800px;
	height: 500px;
	border: 2px solid red;
}
</style>

<script>
	function display(data) {
		Highcharts.chart('container', {

		    title: {
		        text: 'Solar Employment Growth by Sector, 2010-2016'
		    },

		    subtitle: {
		        text: 'Source: thesolarfoundation.com'
		    },

		    yAxis: {
		        title: {
		            text: 'Number of Employees'
		        }
		    },

		    xAxis: {
		        accessibility: {
		            rangeDescription: 'Range: 2010 to 2017'
		        }
		    },

		    legend: {
		        layout: 'vertical',
		        align: 'right',
		        verticalAlign: 'middle'
		    },

		    plotOptions: {
		        series: {
		            label: {
		                connectorAllowed: false
		            },
		            pointStart: 2010
		        }
		    },

		    series:data,
		    
		    responsive: {
		        rules: [{
		            condition: {
		                maxWidth: 1000
		            },
		            chartOptions: {
		                legend: {
		                    layout: 'horizontal',
		                    align: 'center',
		                    verticalAlign: 'bottom'
		                }
		            }
		        }]
		    }

		});
	}


	function getData() {
		
		$.ajax({
			url:'getdata1.mc',
			success:function(data){
				//alert(okok);
				display(data);
			},
			error:function(){
				alert(123);
				}
			
		});
		//display();
	};
	$(document).ready(function(){
	      getData();
	});
	
</script>

<h1>chart1</h1>
<div id="container"></div>
```



<script src="https://code.highcharts.com/modules/series-label.js"></script>