IoT Cloud PlatForm 프로젝트

저희는 공공시설의 쓰레기통을 관리하고 제어하는 IoT 서비스를 개발했습니다. 
Arduino 디바이스 플랫폼에서 무게를 감지하는 센서인 ‘로드셀’을 사용하여 공공시설의 쓰레기통의 무게를 실시간으로 측정할 수 있도록 만들었습니다.

Arduino MKR 1010 보드를 이용했으며 센서로는 LED 그리고 무게 센서 HX711를 사용하였습니다. 
이렇게 측정된 쓰레기통의 무게(weight)를 Arduino와 연동된 AWS 플랫폼에 전송하여 저장합니다. 
AWS 플랫폼에 저장된 로그정보를 Android Mobile App에서 실시간 쓰레기통의 무게를 확인할 수 있도록 대시보드를 구현했습니다. 

IoT 백엔드는 AWS의 다양한 서비스(AWS IoT Core, AWS Lambda, Amazon DyanmoDB, Amazon SNS, Amazon API Gateway)를 이용해 구축된 IoT 클라우드 플랫폼입니다.
AWS IoT Device gateway를 통해서 연결된 아두이노 디바이스(MKRWiFi1010)로부터 무게값과 LED 상태를 수신하고, MQTT 프로토콜을 이용하여 Device shadow와 상호작용합니다.
Device shadow는 Device gateway를 통해 게시된 주제에 따라 디바이스 상태정보를 업데이트하거나 현재 상태정보를 게시합니다.
AWS Lambda 함수를 통해서 수신된 실시간 무게값을 Amazon DynamoDB에 저장하였습니다.

Amazon API Gateway는 AWS Lambda함수를 통해서 다음 기능을 수행합니다.
1. AWS IoT Core에 등록된 디바이스 목록을 조회하는 REST API
2. 디바이스의 정보를 조회하거나 변경하는 REST API
3. 디바이스의 로그 정보를 조회하는 REST API

Arduino : https://github.com/qkrrhksdlr/IoT_Cloudplatform/tree/master/AWS_IoT_DHT11/AWS_IoT_DHT11

Android : https://github.com/qkrrhksdlr/IoT_Cloudplatform/tree/master/Android-RestAPI-master

사물조회 : https://github.com/qkrrhksdlr/IoT_Cloudplatform/tree/master/ListingDeviceLambdaJavaProject

상태조회 : https://github.com/qkrrhksdlr/IoT_Cloudplatform/tree/master/GetDeviceLambdaJavaProject

상태변경 : https://github.com/qkrrhksdlr/IoT_Cloudplatform/tree/master/UpdateDeviceLambdaJavaProject

DB저장 : https://github.com/qkrrhksdlr/IoT_Cloudplatform/tree/master/RecordingDeviceDataJavaProject2

로그값조회 : https://github.com/qkrrhksdlr/IoT_Cloudplatform/tree/master/LogDeviceLambdaJavaProject
