# RPA Tools pakage
반복노가다 업무 or 로그 분석업무등을 자동화하기 위한 시도들을 모아놓은 패키지
파이썬 최고

## 1. 빌드별 파일사이즈 측정 자동화
파일사이즈의 변동을 모니터링하기 위해, 빌드배포 사이트에서 QA빌드와 기존배포빌드의 파일사이즈값을 취득하여 그래프로 표시해주는 프로그램

### 1. 웹 크롤러 with GUI 
  + Using Tools: PyQt5, Selenium, Pyinstaller, PowerMockup, matplotlib, pandas


![2020-03-24_11h58_50](https://user-images.githubusercontent.com/25470405/77383763-1f57f900-6dc7-11ea-868a-63b321531093.png)
![2020-03-24_11h58_50](https://user-images.githubusercontent.com/25470405/77384067-d5234780-6dc7-11ea-9cbe-1d377b92ca5b.png)

### Demo
![ezgif com-video-to-gif (1)](https://user-images.githubusercontent.com/25470405/77300000-b58d1000-6d30-11ea-98d9-eb412cd8724a.gif)

### Description
![2020-03-23_18h18_37](https://user-images.githubusercontent.com/25470405/77301296-c9397600-6d32-11ea-8d3e-b55cffeb5e09.png)


![2020-03-24_11h33_13](https://user-images.githubusercontent.com/25470405/77382276-50362f00-6dc3-11ea-9dc4-5093a3edfeaa.png)

### Trouble Shooting
* PyDesigner 실행파일 경로
py디자이너는 UI레이아웃을 하드코딩하는 시간을 절약시켜주지만 실행파일이 넘나 숨겨져있음
삽질방지를 위해 경로메모

C:\Users\%USERNAME%\AppData\Local\Programs\Python\Python37\Lib\site-packages\pyqt5_tools\designer.exe

* PyDesiner로 작성한 .ui파일을 .py로 컨버트 하는 커맨드
    ```sh
      pyuic5 {input 파일명}.ui -o {output 파일명}.py
    ```
    
* pyqt 버튼 이벤트 작성방법
디자이너에서 생성된 코드를 동작시키려면 @pyqtSlot으로 event lisner를 작성해서 이벤트를 버튼에 연결시켜 줘야함

    ```python
      # 실행버튼 이벤트 
      @pyqtSlot()
      def executeBtn_on_click(self):
          QMessageBox.about(self, "Info", "파일사이즈 데이터 수집을 시작합니다. 수집동안에는 PC조작을 삼가주세요")
          # (중략)
          
      # 이벤트 연결    
      def setupUi(self, BuildFileSizeChecker):
          self.ExecuteBtn.clicked.connect(self.executeBtn_on_click)
 
    ```

* 로컬에 작성한 GUI프로그램을 다른사람들도 사용할수 있게 exe로 패키징해주는 커맨드
패키징하려는 py파일 경로로 이동하여 아래 커맨드를 실행
    ```sh
      pyinstaller --onefile {파일명}.py
    ```
※icon옵션지정으로 커스텀 이미지로 실행파일 아이콘변경도 가능




### 2. Log Parser
로그를 파싱하여 테스트에 필요한 데이터를 수집 및 csv파일로 출력하는 스크립트
  + Using Tools: parse, xlrd, xlwt


![ios_sdk_size](https://user-images.githubusercontent.com/25470405/77301454-0e5da800-6d33-11ea-8f47-6193169be974.png)


