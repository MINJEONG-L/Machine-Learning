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
      * 유클리디언 거리 (L2 distance), 코싸인 유사도 등 벡터에서 정의되는 모든 거리 척도  
      ![image](https://user-images.githubusercontent.com/82145878/179122933-085f0f43-2039-44d5-82f0-94d562e922c7.png)  
      
      * 코사인 유사도  
      - 서로에 대한 유사도를 각도로 나타내겠다  즉 두 벡터 사이의 코사인 각도를 구해 서로의 유사도를 구하는 방식  
      - 텍스트 데이터의 유사도를 구하는 방법 중 하나  
      - 데이터 셋의 길이 차이가 심한 상황일 때도 데이터들의 유사도를 판단할 수 있다.  
      - 같은 의미의 문장을 짧게도 길게도 표현할 수 있는데 여기서 유클리디언 거리를 사용하면 유사도 값이 잘 안나옴  
      - 이럴 때 코사인 유사도를 쓴다.  
      ![image](https://user-images.githubusercontent.com/82145878/179123598-1b44b871-ccfc-4bad-b8d3-cb0842c55e58.png)  
      >> 두 벡터의 내적을 분자에 놓고 각각의 벡터 공간을 곱한것을 분모에 놓는다.  
      
      - TFITF what  
      
      - 각각의 클러스터의 중심으로 이동을 해서 각각의 데이터와 거리를 계산 ==> 어디 중심과 젤 가깝나 해서 가장 작은 중심으로 군집으로 묶이게 됨  
      - 별은 임의로 선택 된거기때문에 군집이 만드러지면 군집의 중심점(바운더리의 중심점)을 계싼함  
      - 이동하면 좌표가 틀어졌기 때문에 데이터들과 중심점의 거리를 다시 계산해서 군집을 다시 이뤄야함  
      - 자기 군집이 달라졌으니까... 또 중심점 이동을 함 다시 계산을 햇을때 더이상은 점의 색깔이 바뀌징낳을 때 까지의 중심점을 ㅊ자아 나가는 것  
      - 이동을 하고나서 계싼을 해도 클러스터가 변하지 않으면 마무리  
      - 유클리드 거리 이용  
      - 문제 : 처음에 어디에다가 초기좌표를 던지냐에 따라서 군집이 잘되냐안되냐가 매우 다름
      - 똑같이 3회 지정해 ㅈ던져도 군집이 형성도ㅣ는게 달라짐 
      멈추는 구간이 다른 군집으로 넘어가는 게 없을때 멈추기때문에  
      
      - Ball-shaped clusters 원형 모형  
        유클리드거리를 쓰니까 원으로 들어오니까 자기 군집은 다 원형 모양이 되는 것임 서로가 겹치지않는 원형 모양을 ㅊ찾아야함  
        군집이 분류를 햇을때 딱 원형으로만 분리가 되지않는 경우가 더 많지 이런경우 k-means가 잘 안됨 그래서 데이터의 특성에 따라 잘 되고안되고가있음  
        굉장히 큰 문제! 노이즈에 아주 민감하다 sensitive to noise points 
        모든 데이터를 다 계산하기 때문에 이상치가 들어와도 계산을 해서 그쪽으로 치우지게 될 수 잇음  
        
      해결법  
      ![image](https://user-images.githubusercontent.com/82145878/179241008-ff3c8c7f-c1ba-4e61-91fb-4955a681a276.png)  

      1. n_init : 던지는 중심점은 8개를 던지는데 그것은 초기화를 10번을 하겠다는 것임 초기좌표를 10번을 던지겟다?  
      초기 좌표를 잘못 던져서 생긴 문제를 해결하는 방법  
      
      2. init = k-means++ 이렇게 하면 퍼져서 들어가서 붙어서 생기지는 않는다 
      원래는 랜덤하게 들어감  
      볼 모양의 군집은 어케 해결할까?  
      노이즈 포인트는 어케 해결할까?  
      노이즈 땜에 나머지 데이터들이 다른 군집에 뺏김 ==> 아주 크게 흔들림  
      kmeans는 노이즈를 사전에 많이 제거하고 군집을 시키는게 좋음   
      
   * k-means clustering 장단점  
    
    - 장점 : 계산이 쉽다. 다른 군집화 알고리즘에 비해 복잡도가 낮다. 구현이 쉽다. 다양한 언어오 플랫폼에서 제공되는 알고리즘임  
    - 단점 : 노이즈에 매우 민감, 군집 개수를 사전에 지정, 앞의 몇 가지 상황에서는 최적의 군집 구조를 찾기 어려움  
    
   * Evaluation metrics for clustering
    
      - 클러스터링이 잘 됐는지 안됐는지 평가
      - 논문을 봐도 완벽한 방법은 없다 완벽한 평가 척도는 없다.   
      - 그래도 해볼만한것은 있따 그러나 모든 사람이 만족할 만한 것은 아니다   
      
   * Silhouette score 
    
      : 군집간의 거리가 얼마나 효율적으로 분리되어있는지 - 다른 군집과는 멀리 같은 군집과는 가깝게  
      형이상학적 군집에서는 잘 안댐(태극모양)  
      
      ![image](https://user-images.githubusercontent.com/82145878/179127832-f6f5a272-0240-4c82-88ed-0124bc901114.png)  
      
      a는 자기군집, i가 속해있는 군집 / 속하지 않느 군집이 b  
      b(i)-a(i) 마이너스가 나올수도 잇는데 이말은 다른 군집에 데이터 포인트가 할당이 되었다는 말  
      
      ![image](https://user-images.githubusercontent.com/82145878/179243118-20af3d4c-89f7-485b-b979-af4348cc82ee.png)  
      ![image](https://user-images.githubusercontent.com/82145878/179243168-227f666a-c456-454a-aaf6-ec9d8a61723b.png)  
      ![image](https://user-images.githubusercontent.com/82145878/179243199-e04e2d87-316b-4bc1-bf16-f442ccf1086e.png)  


      기울기가 급격하게 바뀔 때 == 군집이 끝났다.??
      
      

  2) Hierarchical clustering 계층적 군집화  

  ![image](https://user-images.githubusercontent.com/82145878/179244132-67ef5cc8-05c7-490e-9e97-09b0570139e5.png)  
  ![image](https://user-images.githubusercontent.com/82145878/179244587-97606297-b539-473e-a02f-d44e2f982e6c.png)  
  
  * 유사도  
  ![image](https://user-images.githubusercontent.com/82145878/179244664-a93d331e-d3d3-4de9-8f01-31f330733777.png)  
  ![image](https://user-images.githubusercontent.com/82145878/179244692-658feeba-9d90-4843-8906-6975fdc9ac20.png)  
  
  - Min distance(Single linkage)  
  - Max distance(Complete linkage)  
  - Group average distance(Average linkage)  
  - Between centroids distance(Centroid linage)  
 
  * 장점   
    - 군집 구조 정보가 매우 풍부  
    - 군집화의 결과가 stable하게 생성  
    - 임의의 모양을 갖는 군집을 생성  

  * 단점
    - 계산 복잡도가 높다.  
    - 메모리 확보 필요  
 
  * 이슈
    - is it possible to cut dynaically a hierarchical cluster tree?  
  
  ![image](https://user-images.githubusercontent.com/82145878/179245725-9df9e222-aec9-4293-917b-3bdf9898b002.png)  
  ![image](https://user-images.githubusercontent.com/82145878/179245782-02db1614-ae6a-4565-9551-9cd75379d99e.png)  

  3) DBSCAN - Density Based Spatial Clustering of Applications with Noise  
  ![image](https://user-images.githubusercontent.com/82145878/179246549-047f2054-efcb-4313-8df8-765a46cd26d8.png)  
  
   * 그룹화  
    ![image](https://user-images.githubusercontent.com/82145878/179246689-ad98b110-1946-46ef-8efe-5d3831f6ebe6.png)  
    ![image](https://user-images.githubusercontent.com/82145878/179246995-3168d5e9-7955-4f8f-9067-b4efbaf4e03c.png)  
    
   * Heuristics  
    ![image](https://user-images.githubusercontent.com/82145878/179247699-225b2410-395a-4b23-8e4a-d26367752f00.png)  
    
   Eps ↑, samples ↑  
   Eps ↑, samples ↓  
   Eps ↓, samples ↑  
   Eps ↓, samples ↓  

   ![image](https://user-images.githubusercontent.com/82145878/179248400-90a86bc1-4c7c-4cbe-897b-2c905886bebd.png)  
   
   Eps ↑  
    
   ![image](https://user-images.githubusercontent.com/82145878/179248609-d6689252-1ac8-4fc3-a1d2-fcd14d919b8c.png)  
   
   Eps ↑, samples ↑  
    
   ![image](https://user-images.githubusercontent.com/82145878/179248681-c4f25234-5a50-4441-86e1-1b9f70db40f7.png)  
   
   Eps ↑, samples ↓  
    
   ![image](https://user-images.githubusercontent.com/82145878/179248776-16272f1a-dd20-4e01-bada-9e350e53c6d3.png)  
   
   Eps ↓, samples ↑  
    
   ![image](https://user-images.githubusercontent.com/82145878/179248850-1fda434a-4762-4ae1-bf77-184e6b8ce5ec.png)  
   
   Eps ↓, samples ↓  
    
    
   * DBSCAN vs Other Clustering  
   ![image](https://user-images.githubusercontent.com/82145878/179249057-04c348d0-6c9e-4dd4-b465-b121791bdbec.png)  
    
   * 장점  
    - 노이즈에 매우 둔간함 군집화 가능  
    - 임의의 모양을 갖는 군집을 생성할 수 있음  
   * 단점  
    - Parameters에 따라 결과가 민감하게 작동  
    - 높은 계산 비용  
    
   * 클러스터링한 결과를 어떻게 판단할 것인가? No Best Rules  
    ![image](https://user-images.githubusercontent.com/82145878/179250002-b3f82cb1-59d3-41aa-8b78-577f9289484a.png)     
    
    
    

    
    













      

