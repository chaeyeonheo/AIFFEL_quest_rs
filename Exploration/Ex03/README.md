# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 허채연
- 리뷰어 : 이주연


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
        - 중요! 해당 조건을 만족하는 부분을 캡쳐해 근거로 첨부
    ```python
        img_result2 = img_rgb.copy()
        # 스티커 영역 추출
        sticker_area = img_result2[y:y+sticker_height, x:x+sticker_width]
        
        # np.where를 사용하여 마스크 기반으로 합성
        # 마스크가 0인 부분(배경)은 원본 이미지, 그렇지 않은 부분은 스티커 이미지
        sticker_area = np.where(mask[:sticker_height, :sticker_width, np.newaxis] == 0, 
                              sticker_area, 
                              rgb_channels[:sticker_height, :sticker_width]).astype(np.uint8)
        
        img_result2[y:y+sticker_height, x:x+sticker_width] = sticker_area
        
        plt.figure(figsize=(8, 8))
        plt.imshow(img_result2)
        plt.title('Cat Whiskers Sticker (using np.where)')
        plt.axis('off')
        plt.show()
    ```
    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭을 왜 핵심적이라고 생각하는지 확인
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드의 기능, 존재 이유, 작동 원리 등을 기술했는지 확인
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
       ```python
        # Step 5: 스티커 적용 위치 계산
        # 고양이 수염은 코와 입 사이에 위치하는 것이 자연스러움
        # 코 끝(33)과 상단 입술의 중앙(51)의 중간점을 사용
        def get_whiskers_position(landmarks):
            nose_tip = landmarks[33]  # 코 끝점
            upper_lip = landmarks[51]  # 윗 입술 중앙
    
        # 코와 입술 사이의 중간점 계산
        whiskers_x = nose_tip[0]
        whiskers_y = (nose_tip[1] + upper_lip[1]) // 2
        
        return whiskers_x, whiskers_y
        ```
        
- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 프로젝트 평가 기준에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
      ```python
         test_images = [
                'aiffel/camera_sticker/images/baby1.jpg',
                'aiffel/camera_sticker/images/baby2.jpg'
            ]
            
            for i, img_path in enumerate(test_images):
                result, msg = apply_sticker(img_path, whiskers_path)
                print(f"테스트 {i+1}: {msg}")
                plt.figure(figsize=(8, 8))
                plt.imshow(result)
                plt.title(f'Test Image {i+1}')
                plt.axis('off')
                plt.show()
        ```
                    
- [ ]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
     
- [x]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화/모듈화했는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
       ```python
           def get_whiskers_position(landmarks):
            nose_tip = landmarks[33]  # 코 끝점
            upper_lip = landmarks[51]  # 윗 입술 중앙
            
            # 코와 입술 사이의 중간점 계산
            whiskers_x = nose_tip[0]
            whiskers_y = (nose_tip[1] + upper_lip[1]) // 2
            
            return whiskers_x, whiskers_y
     ```

# 회고(참고 링크 및 코드 개선)
```
# 리뷰어의 회고를 작성합니다.
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
