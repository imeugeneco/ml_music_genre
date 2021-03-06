# ml_music_genre
### 데이터 전 처리 과정
* tempo, energy 등 변수들 사이에 단위수적 차이
* 변화관계의 절대량이 아닌 비율의 접근으로 unit별 차이 극복
* [최종 노트북](modeling_4var_final.ipynb)
1. 필요 컬럼 정렬 및 float 처리
2. 원핫 인코딩 및 최종 모델 전처리
3. log 처리 및 NAN값 제거-최종 데이터풀 구축

### 클러스터 형성
* 깔끔한 산점도를 얻기 위해 음악 분위기와 직결되는 4개의 변수만 남김 (엘보 방법 & 실루엣 계수로 클러스터 개수 k 선택)
* 변수 4개(acousticness, danceability, energy, loudness) 사용 시 산점도에서 경계가 잘 구분되기 때문에 해당 변수 4개로 결정
* 엘보 방법, 실루엣 계수, 산점도를 모두 고려하여 클러스터 개수가 3개/4개일 때가 분류에 적합하다 판단

### 플레이리스트 추천 알고리즘
* [최종 노트북](playlist_algorithm.ipynb)
1. 노래별로 연관 단어 (형용사) 페어 추출
2. 클러스터 재정의
3. 장르 조사
4. 서브 장르 조사 
5. (마이너 장르+서브장르 조합이 경우) 아티스트 조사
6. 대중성 선호도 조사 
7. 장르, 서브 장르, 장르와 서브 장르의 연관 단어, 아티스트, 아티스트의 연관 장르와 서브장르, 대중성 선호도에 관한 각각의 상관관계 등을 통해 플레이리스트 추출
