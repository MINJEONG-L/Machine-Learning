## Unsupervised Learning (Clustering)  
  - 클러스터링은 데이터에서 비슷한 객체들을 하나의 그룹으로 묶는 것  
  - 데이터가 `비슷한` 기준은?  
  - 분산 ; 대표값에서 원의 중심점에서 각각의 데이터들 사이의 거리를 다 게산을 해서 평균을 구하는데 그것이 최소화 될 수 있는 짖점을 찾고 또 다른 군집간의 거리를 계싼해보는 것 그 거리가 최대화할 수 잇는 것 자기 그룹끼리는 촘촘하게 다른 그룹하고는 가급적 멀리  
  ![image](https://user-images.githubusercontent.com/82145878/179122381-2bc8e235-ee73-4ab5-bb4e-228c84563489.png)  
  하ㅏㄴ의 데이터는 하나의 군집에만 포함되야하지만 여러개의 군집에 하나의 데이터가 포함되어이을수도잇음
  지금은 ㅎ나의 군집에 하나의 뎅터로 가정  
  1) K-means clustering  
    - 빠르고 특정 데이터에 대해서는 성능이 좋다.  
     ![image](https://user-images.githubusercontent.com/82145878/179122555-84ffc339-aca5-4d64-9b18-db4ad57beabc.png)  
    - 별 모양이 중심점  
    - 중심점은 사용자가 정해야함  
    * 유사도 : distance d 거리  
      i,j는 두 군집임  d(Xi, Xj): 데이터 X에 대해 두 데이터 Xi, Xj 간에 정의되는 임의의 거리  
      유클리디언 거리 (L2 distance), 코싸인 유사도 등 벡터에서 정의되는 모든 거리 척도  
      ![image](https://user-images.githubusercontent.com/82145878/179122933-085f0f43-2039-44d5-82f0-94d562e922c7.png)  
      * 코사인 유사도  
      - 서로에 대한 유사도를 각도로 나타내겠다  즉 두 벡터 사이의 코사인 각도를 구해 서로의 유사도를 구하는 방식  
      - 텍스트 데이터의 유사도를 구하는 방법 중 하나  
      - 데이터 셋의 길이 차이가 심한 상황일 때도 데이터들의 유사도를 판단할 수 있다.  
      - 같은 의미의 문장을 짧게도 길게도 표현할 수 있는데 여기서 유클리디언 거리를 사용하면 유사도 값이 잘 안나옴  
      - 이럴 때 코사인 유사도를 쓴다.  
      ![image](https://user-images.githubusercontent.com/82145878/179123598-1b44b871-ccfc-4bad-b8d3-cb0842c55e58.png)  
      


      
