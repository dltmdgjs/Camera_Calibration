# Camera calibration

### description
- 파이썬 OpenCV 라이브러리를 이용한 calibration & distortion correction
#### 코드 설명
- 카메라를 열어 비디오(체스보드)를 다양한 각도에서 촬영함
  ```python
  video_record()
  ```
- 촬영된 비디오 내에서 이미지를 선택하여 calibration 진행
  ```python
  img_select = select_img_from_video(video_file, board_pattern)
  ```
- calibration 결과값을 얻음
  ```python
  rms, K, dist_coeff, rvecs, tvecs = calib_camera_from_chessboard(img_select, board_pattern, board_cellsize)
  ```
- 위 결과를 이용하여 렌즈 왜곡을 보정
  ```python
  distortion_correction(video_file, K, dist_coeff)
  ```


### Calibration  
- 이미지 선택 및 calibration  
  <img width="700" alt="스크린샷 2025-04-06 오후 9 51 04" src="https://github.com/user-attachments/assets/b38bc98b-58b6-4925-921e-d130e88e854a" />  

- calibration 결과  
  <img width="700" alt="스크린샷 2025-04-06 오후 9 53 06" src="https://github.com/user-attachments/assets/792eb651-d5af-450c-bca1-c0ece91e7e97" />




### Lens distorion correction
- 보정 결과 사진  
  <img width="700" alt="스크린샷 2025-04-06 오후 9 55 06" src="https://github.com/user-attachments/assets/ffd65b28-7214-4f5e-bd90-68cbaa7d323d" />  
  <img width="700" alt="스크린샷 2025-04-06 오후 9 55 22" src="https://github.com/user-attachments/assets/35fd7e37-2729-4e4c-9b82-766683849bb5" />  

- 결과 : 광각 카메라가 아니었기에 렌즈에 의한 이미지 왜곡이 심하지 않아, 보정 후와 차이가 거의 없어 보인다. (광각 카메라로 찍으면 보정 효과가 더 잘 나타날 것이다.)
