---
title: 
categories:
 - 
tags:
 - 
---
### 판다스 설치 및 불러오기

아나콘다(Anaconda)를 사용한다면 판다스가 기본으로 장착돼있으므로 별도의 설치과정이 필요 없다. 표준 파이썬을 사용하거나 가상환경을 만든다면 다음과 같이 판다스를 설치하면 된다. 참고로 주피터 노트북에서 느낌표(!)를 앞에 붙이면 명령프롬프트(cmd창)에서의 명령어를 사용할 수 있다.

<div class="prompt input_prompt">
In&nbsp;[None]:
</div>

```python
pip install pandas             # cmd 창 또는 터미널에서 입력할 경우
pip install pandas --upgrade  # 이미 설치된 상태에서 버전 업그레이드 하는 경우
!pip install pandas           # 주피터 노트북에서 입력할 경우

```

판다스 라이브러리를 사용하려면 우선 임포트(import)를 해야한다. 판다스는 pd 라는 별칭으로 임포트하는 것이 전세계적인 관례이므로 따르도록 하자. 아래와 같이 판다스의 버전을 확인해보자. 구버전일 경우 업그레이드를 해주자 (2021.2.21 현재 1.2.2 가 최신)

<div class="prompt input_prompt">
In&nbsp;[1]:
</div>

```python
import pandas as pd   # 라이브러리 임포트

pd.__version__         # 버전 확인
```

<div class="prompt output_prompt">
Out&nbsp;[1]:
</div>




{:.output_data_text}
    '1.2.2'



아래에는 판다스를 통해 할 수 있는 간단한 작업들의 예시다. 연습삼아 주피터 노트북을 켜고 코드를 따라 치면서 결과를 확인해보자.

### 엑셀 파일에서 데이터 읽어오기

원본 데이터를 담고 있는 [엑셀파일](/asset/excel/패널자료_2010_2019. 코스피코스닥.xlsx)은 다음과 같다. 코스피와 코스닥에 상장된 기업들의 과거 10년간의 매출액, 영업이익, 당기순이익과 섹터 정보를 담은 자료이다. 총 22,600개의 행(row)과 7개의 열(column)로 구성돼있다.

![엑셀 데이터 원본](/assets/image/krx_annual.png)

이 데이터를 판다스 명령어를 통해 파이썬 환경으로 불러오자

<div class="prompt input_prompt">
In&nbsp;[6]:
</div>

```python
data = pd.read_excel('패널자료_2010_2019. 코스피코스닥.xlsx')
data
```

<div class="prompt output_prompt">
Out&nbsp;[6]:
</div>




<div markdown="0">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>종목코드</th>
      <th>종목명</th>
      <th>연도</th>
      <th>매출액(천원)</th>
      <th>영업이익(천원)</th>
      <th>당기순이익(천원)</th>
      <th>섹터</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A005930</td>
      <td>삼성전자</td>
      <td>2010</td>
      <td>1.546303e+11</td>
      <td>1.662103e+10</td>
      <td>1.614652e+10</td>
      <td>반도체</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A005930</td>
      <td>삼성전자</td>
      <td>2011</td>
      <td>1.650018e+11</td>
      <td>1.564429e+10</td>
      <td>1.375904e+10</td>
      <td>반도체</td>
    </tr>
    <tr>
      <th>2</th>
      <td>A005930</td>
      <td>삼성전자</td>
      <td>2012</td>
      <td>2.011036e+11</td>
      <td>2.904934e+10</td>
      <td>2.384528e+10</td>
      <td>반도체</td>
    </tr>
    <tr>
      <th>3</th>
      <td>A005930</td>
      <td>삼성전자</td>
      <td>2013</td>
      <td>2.286927e+11</td>
      <td>3.678501e+10</td>
      <td>3.047476e+10</td>
      <td>하드웨어</td>
    </tr>
    <tr>
      <th>4</th>
      <td>A005930</td>
      <td>삼성전자</td>
      <td>2014</td>
      <td>2.062060e+11</td>
      <td>2.502507e+10</td>
      <td>2.339436e+10</td>
      <td>하드웨어</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>22595</th>
      <td>A352820</td>
      <td>빅히트</td>
      <td>2015</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22596</th>
      <td>A352820</td>
      <td>빅히트</td>
      <td>2016</td>
      <td>3.522050e+07</td>
      <td>1.038005e+07</td>
      <td>9.008618e+06</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22597</th>
      <td>A352820</td>
      <td>빅히트</td>
      <td>2017</td>
      <td>9.240176e+07</td>
      <td>3.254540e+07</td>
      <td>2.456881e+07</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22598</th>
      <td>A352820</td>
      <td>빅히트</td>
      <td>2018</td>
      <td>3.013718e+08</td>
      <td>7.993060e+07</td>
      <td>-7.046558e+07</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22599</th>
      <td>A352820</td>
      <td>빅히트</td>
      <td>2019</td>
      <td>5.872245e+08</td>
      <td>9.874247e+07</td>
      <td>7.242410e+07</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>22600 rows × 7 columns</p>
</div>
</div>



### 필터링 / 정렬하기

LG전자의 2015년 이후의 자료만 뽑아서 연도 역순으로 정렬을 해보자.

<div class="prompt input_prompt">
In&nbsp;[9]:
</div>

```python
condition = (data.종목명 == 'LG전자') & (data.연도 >= 2015)
lg = data[condition].sort_values(by='연도', ascending=False)
lg
```

<div class="prompt output_prompt">
Out&nbsp;[9]:
</div>




<div markdown="0">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>종목코드</th>
      <th>종목명</th>
      <th>연도</th>
      <th>매출액(천원)</th>
      <th>영업이익(천원)</th>
      <th>당기순이익(천원)</th>
      <th>섹터</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11439</th>
      <td>A066570</td>
      <td>LG전자</td>
      <td>2019</td>
      <td>6.230618e+10</td>
      <td>2.436139e+09</td>
      <td>1.799480e+08</td>
      <td>내구소비재 및 의류</td>
    </tr>
    <tr>
      <th>11438</th>
      <td>A066570</td>
      <td>LG전자</td>
      <td>2018</td>
      <td>6.134166e+10</td>
      <td>2.703291e+09</td>
      <td>1.472814e+09</td>
      <td>내구소비재 및 의류</td>
    </tr>
    <tr>
      <th>11437</th>
      <td>A066570</td>
      <td>LG전자</td>
      <td>2017</td>
      <td>6.139628e+10</td>
      <td>2.468549e+09</td>
      <td>1.869518e+09</td>
      <td>내구소비재 및 의류</td>
    </tr>
    <tr>
      <th>11436</th>
      <td>A066570</td>
      <td>LG전자</td>
      <td>2016</td>
      <td>5.536703e+10</td>
      <td>1.337763e+09</td>
      <td>1.263150e+08</td>
      <td>내구소비재 및 의류</td>
    </tr>
    <tr>
      <th>11435</th>
      <td>A066570</td>
      <td>LG전자</td>
      <td>2015</td>
      <td>5.650901e+10</td>
      <td>1.192291e+09</td>
      <td>2.491430e+08</td>
      <td>디스플레이</td>
    </tr>
  </tbody>
</table>
</div>
</div>



### 피벗테이블 

행에는 연도별, 열에는 섹터별로 구분해 해당 기업들의 영업이익 합계를 보여주는 피벗테이블을 생성해보자

<div class="prompt input_prompt">
In&nbsp;[16]:
</div>

```python
pivot = data.pivot_table(values='영업이익(천원)', index = '연도', columns='섹터', aggfunc='sum')
pivot
```

<div class="prompt output_prompt">
Out&nbsp;[16]:
</div>




<div markdown="0">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>섹터</th>
      <th>기타금융</th>
      <th>내구소비재 및 의류</th>
      <th>디스플레이</th>
      <th>미디어</th>
      <th>반도체</th>
      <th>보험</th>
      <th>부동산</th>
      <th>상업서비스</th>
      <th>생활용품</th>
      <th>소비자 서비스</th>
      <th>...</th>
      <th>유틸리티</th>
      <th>은행</th>
      <th>음식료 및 담배</th>
      <th>의료 장비 및 서비스</th>
      <th>자동차 및 부품</th>
      <th>자본재</th>
      <th>제약 및 바이오</th>
      <th>증권</th>
      <th>통신서비스</th>
      <th>하드웨어</th>
    </tr>
    <tr>
      <th>연도</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2010</th>
      <td>1.402077e+09</td>
      <td>2.944675e+09</td>
      <td>2.436067e+09</td>
      <td>3.826167e+08</td>
      <td>2.028361e+10</td>
      <td>4.249219e+09</td>
      <td>-5.692247e+07</td>
      <td>6.225229e+08</td>
      <td>1.189731e+09</td>
      <td>1.222803e+09</td>
      <td>...</td>
      <td>3.198684e+09</td>
      <td>6.979284e+09</td>
      <td>5.074602e+09</td>
      <td>7.898370e+07</td>
      <td>1.414171e+10</td>
      <td>1.984304e+10</td>
      <td>1.660456e+09</td>
      <td>1.545113e+09</td>
      <td>4.720252e+09</td>
      <td>1.870261e+09</td>
    </tr>
    <tr>
      <th>2011</th>
      <td>4.338564e+08</td>
      <td>2.017018e+09</td>
      <td>-2.398353e+08</td>
      <td>5.612712e+08</td>
      <td>1.678310e+10</td>
      <td>4.530638e+09</td>
      <td>5.916126e+07</td>
      <td>6.823309e+08</td>
      <td>1.265394e+09</td>
      <td>1.297582e+09</td>
      <td>...</td>
      <td>4.043390e+08</td>
      <td>1.207904e+10</td>
      <td>4.861143e+09</td>
      <td>7.420770e+07</td>
      <td>1.759945e+10</td>
      <td>1.623375e+10</td>
      <td>1.491778e+09</td>
      <td>1.582784e+09</td>
      <td>4.324472e+09</td>
      <td>1.496819e+09</td>
    </tr>
    <tr>
      <th>2012</th>
      <td>9.499003e+08</td>
      <td>1.558786e+09</td>
      <td>1.288646e+09</td>
      <td>7.917403e+08</td>
      <td>2.956363e+10</td>
      <td>4.830134e+09</td>
      <td>5.729134e+07</td>
      <td>7.970500e+08</td>
      <td>1.441707e+09</td>
      <td>1.270034e+09</td>
      <td>...</td>
      <td>1.078467e+09</td>
      <td>1.014047e+10</td>
      <td>5.226630e+09</td>
      <td>8.797397e+07</td>
      <td>1.881736e+10</td>
      <td>1.140954e+10</td>
      <td>1.261153e+09</td>
      <td>9.774022e+08</td>
      <td>3.068342e+09</td>
      <td>3.413049e+09</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>3.282670e+08</td>
      <td>1.722981e+09</td>
      <td>3.016177e+09</td>
      <td>7.030213e+08</td>
      <td>3.957123e+09</td>
      <td>3.009804e+09</td>
      <td>9.528742e+07</td>
      <td>6.161014e+08</td>
      <td>1.441739e+09</td>
      <td>1.228534e+09</td>
      <td>...</td>
      <td>3.666296e+09</td>
      <td>7.779141e+09</td>
      <td>4.701856e+09</td>
      <td>1.853633e+08</td>
      <td>1.931532e+10</td>
      <td>3.912393e+09</td>
      <td>1.396425e+09</td>
      <td>-9.970465e+07</td>
      <td>3.399636e+09</td>
      <td>3.874400e+10</td>
    </tr>
    <tr>
      <th>2014</th>
      <td>1.028046e+09</td>
      <td>1.864722e+09</td>
      <td>3.558197e+09</td>
      <td>6.471227e+08</td>
      <td>6.008643e+09</td>
      <td>4.653864e+09</td>
      <td>8.111735e+07</td>
      <td>6.491948e+08</td>
      <td>1.890226e+09</td>
      <td>1.182185e+09</td>
      <td>...</td>
      <td>7.381537e+09</td>
      <td>8.612867e+09</td>
      <td>5.322884e+09</td>
      <td>1.665123e+08</td>
      <td>1.822650e+10</td>
      <td>4.275238e+09</td>
      <td>1.562700e+09</td>
      <td>1.330831e+09</td>
      <td>2.019918e+09</td>
      <td>2.613542e+10</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>6.558617e+08</td>
      <td>2.088120e+09</td>
      <td>3.345029e+09</td>
      <td>8.234777e+08</td>
      <td>6.518309e+09</td>
      <td>5.287695e+09</td>
      <td>1.186583e+08</td>
      <td>9.966161e+08</td>
      <td>2.795738e+09</td>
      <td>1.413629e+09</td>
      <td>...</td>
      <td>1.297556e+10</td>
      <td>8.582198e+09</td>
      <td>6.207576e+09</td>
      <td>2.434121e+08</td>
      <td>1.680211e+10</td>
      <td>1.587474e+09</td>
      <td>2.033145e+09</td>
      <td>2.502278e+09</td>
      <td>3.646648e+09</td>
      <td>2.762514e+10</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>6.968253e+08</td>
      <td>3.313054e+09</td>
      <td>1.942677e+09</td>
      <td>7.699622e+08</td>
      <td>4.597680e+09</td>
      <td>5.332493e+09</td>
      <td>2.545526e+08</td>
      <td>1.267140e+09</td>
      <td>3.373968e+09</td>
      <td>1.525731e+09</td>
      <td>...</td>
      <td>1.346024e+10</td>
      <td>9.343782e+09</td>
      <td>6.658820e+09</td>
      <td>2.970801e+08</td>
      <td>1.597699e+10</td>
      <td>1.180827e+10</td>
      <td>1.696073e+09</td>
      <td>1.734491e+09</td>
      <td>3.730430e+09</td>
      <td>2.931299e+10</td>
    </tr>
    <tr>
      <th>2017</th>
      <td>8.717716e+08</td>
      <td>4.940874e+09</td>
      <td>3.671457e+09</td>
      <td>7.763464e+08</td>
      <td>1.601460e+10</td>
      <td>7.809635e+09</td>
      <td>3.694350e+08</td>
      <td>5.491872e+08</td>
      <td>2.788962e+09</td>
      <td>1.230273e+09</td>
      <td>...</td>
      <td>6.553649e+09</td>
      <td>1.400350e+10</td>
      <td>6.777083e+09</td>
      <td>2.733390e+08</td>
      <td>1.001525e+10</td>
      <td>1.669612e+10</td>
      <td>2.244993e+09</td>
      <td>4.341085e+09</td>
      <td>3.745894e+09</td>
      <td>5.593330e+10</td>
    </tr>
    <tr>
      <th>2018</th>
      <td>8.087551e+08</td>
      <td>5.481685e+09</td>
      <td>9.536465e+08</td>
      <td>1.049645e+09</td>
      <td>2.318075e+10</td>
      <td>7.701115e+09</td>
      <td>4.165879e+08</td>
      <td>7.074463e+08</td>
      <td>2.559772e+09</td>
      <td>1.028330e+09</td>
      <td>...</td>
      <td>1.603319e+09</td>
      <td>1.605634e+10</td>
      <td>4.711524e+09</td>
      <td>2.299851e+08</td>
      <td>8.332036e+09</td>
      <td>1.777192e+10</td>
      <td>1.667900e+09</td>
      <td>4.558544e+09</td>
      <td>3.211307e+09</td>
      <td>6.216125e+10</td>
    </tr>
    <tr>
      <th>2019</th>
      <td>9.081723e+08</td>
      <td>6.105800e+09</td>
      <td>-9.898823e+08</td>
      <td>1.155878e+09</td>
      <td>4.595345e+09</td>
      <td>4.770805e+09</td>
      <td>3.379355e+08</td>
      <td>1.073942e+09</td>
      <td>2.437352e+09</td>
      <td>1.129512e+09</td>
      <td>...</td>
      <td>6.099816e+08</td>
      <td>1.979920e+10</td>
      <td>4.638856e+09</td>
      <td>3.487813e+08</td>
      <td>1.112191e+10</td>
      <td>1.563592e+10</td>
      <td>1.621191e+09</td>
      <td>5.842008e+09</td>
      <td>2.928385e+09</td>
      <td>3.128180e+10</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 25 columns</p>
</div>
</div>



### 시각화

위에서 생성한 피벗테이블 중에서 '자동차 및 부품' 산업과 '자본재' 산업의 영업이익의 시계열 그래프를 그려보자

<div class="prompt input_prompt">
In&nbsp;[17]:
</div>

```python
pivot[['자동차 및 부품', '자본재']].plot()
```

<div class="prompt output_prompt">
Out&nbsp;[17]:
</div>




{:.output_data_text}
    <AxesSubplot:xlabel='연도'>




    
![png](pandas_1_files/pandas_1_12_1.png)
    

