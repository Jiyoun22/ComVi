# ComVi
한국어 소개 글이 아래에 나와있습니다.

The Korean introduction is above, and the English introduction follows below.

# 프로젝트 소개
### 프로젝트 제목 
Cutie의 한계 극복을 위한 대조 기반 및 그림자 인식 기술 통합

### 프로젝트 요약 
 본 프로젝트는 Cutie의 한계를 극복하기 위해 새로운 해결 방안을 제안한다. Cutie는 픽셀 기반과 객체 기반을 혼합한 비디오 객체 분할 기술로, 단일 객체 인식 성능은 개선되었지만 근접하거나 겹쳐 있는 객체 인식의 정확도가 떨어지는 문제와 그림자 인식의 부재라는 한계가 있다. 이를 해결하기 위해 대조 기반 인식 기술과 그림자 인식 기술인 LISA를 Cutie에 통합하는 방안을 제안한다. 이를 통해 기대되는 효과는 Cutie의 객체 분할 정확도와, Cutie의 응용 범위를 넓혀 다양한 분야에서의 활용성을 높인다. 
 코랩에 올라온 선행 연구의 코드를 수정하여 더 나은 방향으로 나아가고자 실시한 프로젝트이다. 따라서 주로 코랩을 사용하고 구글 드라이브를 통해 실행결과를 저장하고 관리하였다.

# 서론
 비디오 객체 분할 기술은 비디오 프레임 내에서 특정 객체를 인식하는 기술이다. 이 기술을 통해 자동차, 증강 현실, 영화 및 비디오 편집 등 다양한 분야에서 사용되고 있다. 여러 비디오 객체 분할 기술 중에서 Cutie는 픽셀 기반 분할과 객체 기반 추적의 혼합 방식ㅇ르 사용해 더욱 정밀한 분할을 구현한다. 그러나 기존 VOS 기술의 성능을 개선한 Cutie에도 여전히 해결해야 할 한계점이 존재한다.
 첫번째는 단일 객체에 대한 인식은 향상되었지만 서로 근접하거나 겹쳐 있는 여러 객체를 인식할 때 정확한 결과가 나타나지 않는다는 것이다. 따라서 복잡한 장면에서 객체 간 경계가 흐려지거나 중첩되는 상황에서의 객체 인식 정확도가 떨어진다. 두번째는 Cutie가 그림자 인식을 지원하지 않는다는 점이다. 현재 비디오 객체 분할 기술이 다양한 분야에서 사용되고 있지만, 영화 및 비디오 편집과 같이 현업에서 필요한 기술은 그림자까지 인식하고 편집할 수 있는 기능이다.
 이러한 문제들을 해결하기 위해 Cutie가 사용하는 픽셀 기반과 객체 기반 분할 방식에 더해, 대조 기반 인식 기술을 추가한다. 대조 기반 인식은 서로 가까이 위치하거나 겹쳐 있는 객체의 경계를 명확하게 분할할 수 있도록 한다. 기존 Cutie에 대조 기반 인식 기술을 적용하면 복잡한 장면에서 객체 간의 분리 성능을 향상시킬 수 있을 것이다.
 그림자 인식기술을 추가하기위해 LISA(Light-guided Instance Shadow-kbject Association)를 적용한다. LISA는 객체와 그림자 간의 관계를 조명 정보를 기반으로 파악하여 그림자를 감지하고 제거하는 기술입니다. LISA를 Cutie에 통합하면, 사용자가 필요에 따라 그림자를 객체 인식에 포함시킬 수 있는 옵션을 선택할 수 있습니다.
 이러한 방법은 Cutie의 다양한 분야에서의 응용에 적합하게 만들것입니다.

# 본론
 ![image](https://github.com/user-attachments/assets/335f9351-9d02-4ebe-924e-6dcf739ebede)
 
 픽셀 기반 분할은 객체의 경계를 정밀하게 추출하고 미세한 움직임을 감지하는데 유리하지만, 일관성이 부족하다는 단점이 있다. 반면, 객체 기반 추적은 객체의 일관된 추적을 가능하게 하여 복잡한 장면에서 더 정확한 결과를 제공하지만, 세부적인 변화에 대한 감지 성능이 떨어지는 단점이 있다. 이러한 두가지 기술의 장단점을 결합한 것이 Cutie의 핵심이다. 하지만, Cutie는 여전히 근접하거나 겹쳐 있는 객체를 정확하게 인식하는 데 한계가 있다.
 이를 해결하기 위해 대조 기반 인식 기술의 추가가 필요하다. 대조 기반 인식 기술은 서로 근접한 객체들 간의 색상과 명암 차이를 분석하여 경계를 더욱 명확하게 구분해주는 기술이다. 원핫 코딩을 이용하여 객체와 객체가 아닌 것을 나누고 그에 따른 마스킹을 진행하기 때문에 모든 객체들이 동일한 색의 마스크로 출력된다는 특징이 있다. 또한 첫 프레임에서 인식할 객체의 수를 입력받기 때문에 자동적으로 객체를 인식하던 전 기술보다는 정확한 객체의 개수를 인식할 수 있을 것이다. 후에 LISA 기술을 통해 그림자를 객체와 구별하거나 필요에 따라 포함할 수 있는 기능을 제공한다.

# 결론
 이번 프로젝트에서는 비디오 객체 분할 기술 Cutie의 한계를 극복하기 위한 대조 기반 인식 기술과 그림자 인식 기술인 LISA의 통합을 제안한다. Cutie는 기존 필셀 기반과 객체 기반 방법을 혼합한 기술로, 근접하거나 겹쳐 있는 객체 인식의 정확도와 그림자 인식의 부재라는 문제점을 가지고 있었다. 이를 극복하기 위해 대조 기반 인식 기술을 통해 복잡한 장면에서의 객체 인식 정확도를 높이고, LISA를 통해 그림자를 효과적으로 인식할 수 잇는 옵션을 실행하여 Cutie의 응용 범위를 넓히는 방안을 제안하였다. 
 추가적으로 원핫 코딩을 이용하였기 때문에 마스킹이 전부 동일한 색으로 표현되기 때문에 서로 겹쳐진 물체에 대해서는 인식이 잘 되었는지 확인하기 어려울 수 있을 것이다. 따라서 물체가 마스킹된 색을 다르게 수정하는 작업이 필요할 것이다. 더 나아가 Cutie의 메모리 및 계산 자원 요구량 문제를 해결하는 것이 중요할 것이다. Cutie는 고해상도 픽셀 메모리와 객체 메모리를 사용하여 높은 정확도를 내지만, 이는 대규모 비디오를 처리할 때, 효율성이 떨어질 수 있다. 이러한 문제를 해결하기 위해 알고리즘 최적화를 진행하고 실제 산업 활용 가능성을 높이는 방향으로 연구를 진행할 계획이다.



***



# Project Introduction
### Project Title
Overcoming the Limitations of Cutie: Integrating Contrastive and Shadow Recognition Technologies

### Project Summary
 This project proposes a new solution to overcome the limitations of Cutie. Cutie is a video object segmentation technology that combines pixel-based and object-based methods. While the performance of single-object recognition has improved, it still faces issues with accurately recognizing closely positioned or overlapping objects, as well as the lack of shadow recognition. To address these issues, we propose integrating contrastive recognition technology and shadow recognition technology, LISA, into Cutie. The expected outcome is to improve Cutie’s object segmentation accuracy and expand its application range for use in various fields.
 This project was conducted by modifying the code of a previous study available on Google Colab to improve upon it. Consequently, we primarily used Colab and stored and managed the results via Google Drive.

### Introduction
 Video object segmentation is a technology that identifies specific objects within video frames. This technology is widely used in fields such as automotive, augmented reality, and movie and video editing. Among the various video object segmentation techniques, Cutie utilizes a hybrid approach combining pixel-based segmentation and object-based tracking to achieve more precise segmentation. However, even though Cutie improves the performance of existing video object segmentation (VOS) technologies, there are still limitations to be addressed.
 The first limitation is that, while the recognition of single objects has improved, Cutie struggles to recognize multiple objects that are near each other or overlapping. This leads to inaccurate results in complex scenes where the boundaries between objects become blurred or overlapped. The second limitation is that Cutie does not support shadow recognition. While current video object segmentation technologies are used in various fields, industries such as movie and video editing require technology that can detect and edit shadows.
 To solve these problems, we propose adding contrastive recognition technology and LISA (Light-guided Instance Shadow-object Association), a shadow recognition technology, to Cutie’s existing pixel-based and object-based segmentation methods. Contrastive recognition technology will help clearly segment the boundaries of objects that are close or overlapping. By applying contrastive recognition to Cutie, the object separation performance in complex scenes can be improved.
 To add shadow recognition capabilities, we integrate LISA, which detects and removes shadows by understanding the relationship between objects and shadows based on lighting information. By integrating LISA into Cutie, users will have the option to include or exclude shadows from object recognition based on their needs.
This approach will make Cutie more suitable for a wide range of applications.

### Main Body
 ![image](https://github.com/user-attachments/assets/04959ef8-a4f3-47bf-b3be-a330057d08c8)

 Pixel-based segmentation is advantageous for precisely extracting object boundaries and detecting small movements but has the disadvantage of lacking consistency. On the other hand, object-based tracking enables consistent tracking of objects, providing more accurate results in complex scenes, but its ability to detect subtle changes is limited. The core of Cutie combines the strengths of both of these technologies. However, Cutie still has limitations when it comes to accurately recognizing close or overlapping objects.
 To address this, the addition of contrastive recognition technology is necessary. Contrastive recognition technology analyzes the color and brightness differences between closely positioned objects, helping to define their boundaries more clearly. Using one-hot encoding, we can distinguish between objects and non-objects and apply masking accordingly. This ensures that all objects are output with the same color mask. Additionally, by taking the number of objects to be recognized from the first frame as input, it will be more accurate in recognizing the correct number of objects compared to previous technologies that automatically recognized objects. Later, the LISA technology can either distinguish shadows from objects or include them, as needed.

### Conclusion
 This project proposes integrating contrastive recognition technology and the shadow recognition technology LISA into Cutie to overcome the limitations of Cutie’s video object segmentation. Cutie, a hybrid technology combining pixel-based and object-based methods, had issues with accurately recognizing close or overlapping objects and lacked shadow recognition capabilities. By adding contrastive recognition technology, we aim to improve object recognition accuracy in complex scenes, and with LISA, we provide an option to effectively recognize shadows. This integration expands the application range of Cutie.
 Additionally, because we used one-hot encoding, the masking is represented in the same color for all objects, which may make it difficult to verify the recognition of overlapping objects. Therefore, adjusting the mask colors for the objects will be necessary. Furthermore, addressing the memory and computational resource requirements of Cutie will be crucial. While Cutie achieves high accuracy by using high-resolution pixel memory and object memory, it may suffer from efficiency issues when processing large-scale videos. To resolve this, we plan to optimize the algorithm and further research to improve its potential for industrial applications.

# Reference
### Putting the Object Back into Video Object Segmentation (CVPR 2024 Highlight)
https://hkchengrex.com/Cutie/
https://github.com/hkchengrex/Cutie

### LIsA
https://go-hard.tistory.com/40
https://github.com/stevewongv/InstanceShadowDetection

[1] Cheng, H. K., Oh, S. W., Price, B., Lee, J. Y., & Schwing, A. (2024). _Putting the Object Back into Video Object Segmentation_. GitHub. https://github.com/hkchengrex/Cutie.  
[2] Oh, S. W., Lee, J. Y., Xu, N., & Kim, S. J. (2019). _Video Object Segmentation using Space-Time Memory Networks_. GitHub. https://github.com/seoungwugoh/STM.
[3] Wang, T., Hu, X., Wang, Q., Heng, P.-A., & Fu, C.-W. (2020). _Instance Shadow Detection_. GitHub. https://github.com/stevewongv/InstanceShadowDetection.
[4] Wang, T., Hu, X., Heng, P.-A., & Fu, C.-W. (2021). _SSIS (CVPR 2021 Oral) & SSISv2 (TPAMI 2022)_. GitHub. https://github.com/stevewongv/SSIS.

