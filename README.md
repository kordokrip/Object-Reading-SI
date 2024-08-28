# Object-Reading-SI
Analysis of economic situation through image learning using satellite images (object of interest detection, building outline extraction, road outline extraction, cloud extraction, radar image water system extraction)


아리랑 위성 영상을 활용한 학습 데이터셋 5종(관심객체 검출, 건물 윤곽 추출, 도로 윤곽 추출, 구름 추출, 레이더영상 수계 추출) 구축하여 재난, 환경, 에너지, 자원, 안보, 식량 등 위성 영상을 다루는 다양한 분야에서 효율적으로 분석, 활용


데이터 영역:	영상이미지	
데이터 유형:	이미지
데이터 출처: 한국항공우주연구원	
라벨링 유형:
라벨링 형식:	
데이터 구축년도/데이터 구축량:	2020년/50만 건 이상 (관심객체 검출), 20만 건 이상 (건물윤곽 추출), 6000km 이상 (도로윤곽 추출), 4000장 이상 (구름 추출), 2400장 이상 (수계 추출)

	측정항목	AI TASK	학습모델	지표명	기준값 점수	측정값 점수
1	위성영상 관심객체 검출 및 인식	Object Detection	RoI Transformer	mAP	40 %	50 %
2	위성영상 건물 검출 성능 (Binary Class)	Object Detection	FCN-ResNet101	mIoU	50 %	62 %
3	위성영상 건물 검출 성능 (Multi class)	Object Detection	FCN-ResNet101	mIoU	30 %	30 %
4	위성영상 도로 검출 성능 (Binary Class)	Object Detection	NL-LinkNet	mIoU	50 %	81 %
5	위성영상 도로 검출 성능 (Multi class)	Object Detection	NL-LinkNet	mIoU	30 %	42 %
6	위성영상 구름 검출 성능	Object Detection	DeepLab v3	mIoU	50 %	63.8 %
7	레이더영상 수계 검출 성능	Object Detection	HRNet v2	mIoU	50 %	82.23 %


데이터 구조

관심객체 검출: 객체의 길이, 방향을 알 수 있는 회전된 형태의 바운딩 박스(rotated bounding box)를 지도 좌표와 함께 geojson 형태로 제공
- 위치 박스: [중심좌표 x, y, 박스크기 H, W, 회전각 θ]
건물윤곽 추출: 다각형의 건물 윤곽과 종류를 지도 좌표와 함께 geojson 형태로 제공
- 위치 모양: polygon 형태의 닫힌 도형
도로 추출: 도로 윤곽과 종류를 지도 좌표와 함께 geojson 형태로 제공
- 위치 모양: polygon 형태의 닫힌 도형

속성	설명
image_id:	영상 ID
time:	영상 생성 시간
type_id:	정수 (1~N), 클래스
type_name:	클래스 이름

![building_results](https://github.com/user-attachments/assets/11e79fa7-2725-4231-8322-23a0b9d1c0c3)
