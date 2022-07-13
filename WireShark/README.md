# ftp 파일 주고받기
<img width="233" alt="image" src="https://user-images.githubusercontent.com/49769190/178702863-add6f63c-aad0-481e-85f1-69907233f615.png">

# WireShark 패킷분석

<img width="920" alt="image" src="https://user-images.githubusercontent.com/49769190/175260877-c64d3394-fd85-4993-9997-b9b736dc4893.png">


## Error
<img width="1087" alt="image" src="https://user-images.githubusercontent.com/49769190/175284643-170bf11f-5977-44f4-981f-04621d44ede8.png">


## Solving
~  ls -al /dev/bpf*
~  sudo chmod 644 /dev/bpf*
  
  장치에 대한 권한을 664 읽기권한을 변경하여 wireshark(프로그램) 재실행
<img width="682" alt="image" src="https://user-images.githubusercontent.com/49769190/175287310-766d8ac6-2317-4b04-b92c-d5c334acbf11.png">
<img width="682" alt="image" src="https://user-images.githubusercontent.com/49769190/176986912-08d6e3f0-30ff-4efd-9046-0ed318d8ee36.png">


정상적으로 패킷을 받는 것을 확인할 수가 있다.
<img width="1201" alt="image" src="https://user-images.githubusercontent.com/49769190/175287771-d65afc91-9f7b-4764-9442-beb3d6828e1f.png">

<img width="1201" alt="image" src="https://user-images.githubusercontent.com/49769190/175288058-4175778c-66d3-4022-a8f2-3b0ae4d09c60.png">


### QUIC
<img width="983" alt="image" src="https://user-images.githubusercontent.com/49769190/175288656-86f0f4ec-db55-4a73-bf4e-16e3e98cdfd5.png">

### TCP
<img width="983" alt="image" src="https://user-images.githubusercontent.com/49769190/175289366-96476779-c4d5-4b88-b402-2e8edf87c403.png">

### TLS1.2v
<img width="983" alt="image" src="https://user-images.githubusercontent.com/49769190/175289605-04d7e93a-b3b7-4ee5-ab41-8ff525c3d6c3.png">

### DNS
<img width="983" alt="image" src="https://user-images.githubusercontent.com/49769190/175290725-a9e7bcc9-1124-4a71-9bbf-49cffee8a8fd.png">



  #### netstat
  <img width="682" alt="image" src="https://user-images.githubusercontent.com/49769190/175333617-dad56b09-2b01-4976-80a9-8dac5647091a.png">

  #### ping
  <img width="682" alt="image" src="https://user-images.githubusercontent.com/49769190/175333701-0da71f68-92f6-413f-b9ba-d0e7884ee5db.png">
  * KT : 168.126.63.1
  * SKT : 210.220.163.82
  * LG : 61.41.153.2

  #### ICMP
  <img width="983" alt="image" src="https://user-images.githubusercontent.com/49769190/175336407-5b5a8164-ab11-44c8-8f5f-1c6ff992ecbf.png">
  
  #### c



## 참고
* https://velog.io/@sms8377/TIL-24-Wireshark를-이용한-간단-패킷-분석
* https://10th-doctrine.tistory.com/355
* https://mikrkosmos97.tistory.com/3
* https://securitymanjoseph94.tistory.com/6
* https://jineer.tistory.com/50
