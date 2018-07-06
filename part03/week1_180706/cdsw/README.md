# Cloudera Data Science Workbench(CDSW) 1.4.x 설치


- 참고 : https://www.cloudera.com/documentation/data-science-workbench/latest/topics/cdsw_install.html
- CentOS7 기준으로 준비함

## 설치방법
  - Using a Custom Service Descriptor (CSD) and Parcel : 이방법 기준
  - Using a Package 
  
## 설치전에 준비 사항들

### Cloudera Manager and CDH 요구
 - Cloudera Manager가 설치된 환경을 요구 
 - Cloudera Manager 5.13 or higher 5.x versions.


### 지원 운영체제 확인
 - RHEL / CentOS / Oracle Linux RHCK : 7.2, 7.3, 7.4
 - Oracle Linux (UEK - default) : 7.3
 - SUSE Linux Enterprise Server (SLES) : 12 SP2, 12 SP3
 
### JDK Requirements
 - Cloudera Manager에서 설치한 버전과 동일한 JDK1.8.x
 
### 하드웨어 구성
 - CPU: 16+ CPU (vCPU) cores
 - RAM: 32+ GB RAM
 - Disk
     - Root Volume: 100+ GB.
     - Application Block Device or Mount Point (Master Host Only): 1 TB
         - CDSW MASTER서버만 필요
         - 따로 설정하지 않으면  Root Vlume을 사용함.    
         - /var/lib/cdsw     
     - Docker Image Block Device: 1 TB
         - *** 파티션 설정이 되어 있지 않아야 함. ***
         - Do not mount these block devices prior to installation.     
         
### Supported Browsers
  - Chrome (latest stable version) : 추천
  - Internet Explorer (IE) 11+ : 안된다고 보면 됨.
  
### DNS 도메인명 등록  ***필수***
  - cdsw.<your_domain>.com.    cdsw서버의 아이피 
  - *.cdsw.<your_domain>.com  cdsw서버의 아이피
  - 하둡클러스터를 구성하는 서버들도 DNS에 등록
      - 안 하면 pyspark 돌릴때 work node명을 찾을수 없다고 에러 발생함.
  - windowns2012서버의 DNS가 가장 쉬움 
  
### Apache Spark 2 설치
  - 참고 : https://www.cloudera.com/documentation/spark2/latest/topics/spark2_installing.html
  - CDSW도 같이 작업이 있어서 여기서 같이 설명함.
  - wget -P  /opt/cloudera/csd   http://archive.cloudera.com/spark2/csd/SPARK2_ON_YARN-2.3.0.cloudera2.jar
  - wget -P  /opt/cloudera/csd   https://archive.cloudera.com/cdsw1/1.4.0/csd/CLOUDERA_DATA_SCIENCE_WORKBENCH-CDH5-1.4.0.jar
  - chown cloudera-scm:cloudera-scm  /opt/cloudera/csd/*.jar && chmod 644 /opt/cloudera/csd/*.jar 
  - service cloudera-scm-server restart  # 클라우데라 매니저 서버를 재시작
  - Cloudera Management Service 재시작
  ![](01.jpg)
  - Spark2 배포용 Parcels 등록 화면
  ![](02.jpg)
  ![](03.jpg)
  - Spark2 배포 저장소 URL을 등록하고 변경내용 저장 버튼을 클릭
  - CDSW도 같이 작업이 필요하므로 같이 등록하자
  ![](04.jpg)
  - 아래 그림과 같이 되도록 다운로드 -> 배포 -> 활성화 
  ![](05.jpg)
  - Spark2 서비스 추가
  ![](06.jpg)
  ![](07.jpg)
  ![](08.jpg)
  ![](09.jpg)
  - Spark2 서비스 완료 화면
  ![](10.jpg)
   


