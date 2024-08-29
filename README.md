<h1 align="center">Object-Reading-SI</h1>

<p align="center">
  <i>Analysis of economic situation through image learning using satellite images</i><br/>
  <strong> (Object of interest detection, building outline extraction, road outline extraction, cloud extraction, radar image water system extraction)</strong>
</p>

---

<h2>📋 프로젝트 개요</h2>
<p>
  Object-Reading-SI 프로젝트는 위성 이미지를 학습하여 경제 상황을 분석하는 시스템을 개발하는 것을 목표로 합니다.
  이 프로젝트는 특히 아리랑 위성 영상을 활용하여 5종의 학습 데이터셋을 구축하며, 재난, 환경, 에너지, 자원, 안보, 식량 등 
  다양한 분야에서 위성 영상을 효율적으로 분석하고 활용할 수 있도록 합니다.
</p>

---

<h2>🔍 주요 기능</h2>
<ul>
  <li><strong>관심객체 검출:</strong> 위성 영상에서 관심있는 객체를 검출하고, 객체의 길이와 방향을 포함한 정보를 회전된 바운딩 박스(rotated bounding box) 형태로 추출합니다.</li>
  <li><strong>건물 윤곽 추출:</strong> 위성 영상에서 건물의 윤곽을 추출하고, 다각형 형태의 건물 윤곽을 geojson 형식으로 제공합니다.</li>
  <li><strong>도로 윤곽 추출:</strong> 위성 영상에서 도로의 윤곽을 추출하고, 이를 geojson 형태로 제공합니다.</li>
  <li><strong>구름 추출:</strong> 위성 영상에서 구름 영역을 추출합니다.</li>
  <li><strong>레이더 영상 수계 추출:</strong> 레이더 영상을 분석하여 수계(물체계)의 윤곽을 추출합니다.</li>
</ul>

---

<h2>🗂 데이터셋 구축</h2>
<ul>
  <li><strong>데이터 출처:</strong> 한국항공우주연구원</li>
  <li><strong>데이터 구축년도:</strong> 2020년</li>
  <li><strong>구축량:</strong></li>
  <ul>
    <li>관심객체 검출: 50만 건 이상</li>
    <li>건물 윤곽 추출: 20만 건 이상</li>
    <li>도로 윤곽 추출: 6000km 이상</li>
    <li>구름 추출: 4000장 이상</li>
    <li>수계 추출: 2400장 이상</li>
  </ul>
</ul>

---

<h2>📊 AI 모델 성능 지표</h2>
<table align="center">
  <thead>
    <tr>
      <th>측정항목</th>
      <th>AI TASK</th>
      <th>학습모델</th>
      <th>지표명</th>
      <th>기준값 점수</th>
      <th>측정값 점수</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>관심객체 검출 및 인식</td>
      <td>Object Detection</td>
      <td>RoI Transformer</td>
      <td>mAP</td>
      <td>40%</td>
      <td>50%</td>
    </tr>
    <tr>
      <td>건물 검출 성능 (Binary Class)</td>
      <td>Object Detection</td>
      <td>FCN-ResNet101</td>
      <td>mIoU</td>
      <td>50%</td>
      <td>62%</td>
    </tr>
    <tr>
      <td>건물 검출 성능 (Multi class)</td>
      <td>Object Detection</td>
      <td>FCN-ResNet101</td>
      <td>mIoU</td>
      <td>30%</td>
      <td>30%</td>
    </tr>
    <tr>
      <td>도로 검출 성능 (Binary Class)</td>
      <td>Object Detection</td>
      <td>NL-LinkNet</td>
      <td>mIoU</td>
      <td>50%</td>
      <td>81%</td>
    </tr>
    <tr>
      <td>도로 검출 성능 (Multi class)</td>
      <td>Object Detection</td>
      <td>NL-LinkNet</td>
      <td>mIoU</td>
      <td>30%</td>
      <td>42%</td>
    </tr>
    <tr>
      <td>구름 검출 성능</td>
      <td>Object Detection</td>
      <td>DeepLab v3</td>
      <td>mIoU</td>
      <td>50%</td>
      <td>63.8%</td>
    </tr>
    <tr>
      <td>수계 검출 성능</td>
      <td>Object Detection</td>
      <td>HRNet v2</td>
      <td>mIoU</td>
      <td>50%</td>
      <td>82.23%</td>
    </tr>
  </tbody>
</table>

---

<h2>🗺 데이터 구조</h2>
<ul>
  <li><strong>관심객체 검출:</strong> 객체의 길이와 방향을 포함한 회전된 바운딩 박스(rotated bounding box)를 geojson 형태로 제공</li>
  <ul>
    <li>형식: [중심좌표 x, y, 박스크기 H, W, 회전각 θ]</li>
  </ul>
  <li><strong>건물 윤곽 추출:</strong> 다각형 형태의 건물 윤곽을 geojson 형태로 제공</li>
  <ul>
    <li>형식: Polygon (닫힌 도형)</li>
  </ul>
  <li><strong>도로 윤곽 추출:</strong> 도로 윤곽과 종류를 geojson 형태로 제공</li>
  <ul>
    <li>형식: Polygon (닫힌 도형)</li>
  </ul>
</ul>

---

<h2>💻 설치 및 실행 방법</h2>
<ol>
  <li>프로젝트를 클론합니다.
    <pre><code>git clone https://github.com/kordokrip/Object-Reading-SI.git</code></pre>
  </li>
  <li>필수 라이브러리를 설치합니다.
    <pre><code>pip install -r requirements.txt</code></pre>
  </li>
  <li>모델을 실행하여 위성 영상을 분석합니다.
    <pre><code>python src/detect_and_extract.py</code></pre>
  </li>
</ol>

---

<h2>🙌 기여 방법</h2>
<p>새로운 기능 추가나 버그 수정에 기여하려면, 먼저 이슈를 생성하거나 기존 이슈를 참고해주세요.<br/>
Pull Request를 통해 기여할 수 있습니다.</p>

---

<p align="center"><i>감사합니다! 프로젝트에 대한 관심과 기여를 환영합니다!</i></p>


Building-detection 

![building_results](https://github.com/user-attachments/assets/11e79fa7-2725-4231-8322-23a0b9d1c0c3)



Roads-detection 

![class7-2](https://github.com/user-attachments/assets/43ca6097-e65c-4401-904e-1b2d4eb7d8f5)
![class7-1](https://github.com/user-attachments/assets/8f49d408-5d15-48f2-b118-8acf9bc3295e)
