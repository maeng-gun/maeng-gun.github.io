<a href="https://colab.research.google.com/github/maeng-gun/python_basic/blob/main/pandas_1.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

# 데이터프레임(DataFrame)의 자료구조와 생성



## 1. 데이터프레임의 특징
* 2차원(행과 열) 데이터를 표현하기 위한 자료형
* 하나의 데이터프레임은 하나의 엑셀시트와 동일한데, 각 행과 열의 명칭이 별도로 붙어있다는 것이 특징


## 2. 데이터프레임의 구조
### 1) 자료값(value) 
 * 행렬 형태의 2차원 자료의 내용물
 * 행(row) : 주로 자료의 각 단위(횡단면자료는 사람/기업/국가 등, 시계열자료는 시점/기간)로 구성
 * 열(column) : 주로 자료의 각 특성(이름,금액,횟수 등)으로 구성

### 2) 인덱스(index)
 * 각 행을 구분하는 명칭을 순서대로 나열한 객체로, 자료값의 좌측에 위치되
 * 인덱스를 별도로 지정하지 않으면 0,1,2,...로 이어지는 행번호를 자동 지정
 * 로우 레이블(row label)이라고도 함

### 3) 컬럼명(columns)
 * 각 열을 구분하는 명칭을 순서대로 나열한 객체로, 자료값의 상단에 위치함
 * 컬럼명을 별도로 지정하지 않으면 0,1,2,...로 이어지는 열번호를 자동 지정
 * 칼럼 레이블(column label)이라고도 함

  
### 예시


```python
import pandas as pd           # 라이브러리 불러오기

val = [['개',4,'멍멍'],       # 자료값을 변수(val)에 저장
       ['닭',2,'꼬꼬'],
       ['벌',6,'붕붕']]

df1 = pd.DataFrame(val)       # 데이터프레임 생성 후 변수(df1)에 저장
df1                           # 변수 df1 출력하기
```




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
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>개</td>
      <td>4</td>
      <td>멍멍</td>
    </tr>
    <tr>
      <th>1</th>
      <td>닭</td>
      <td>2</td>
      <td>꼬꼬</td>
    </tr>
    <tr>
      <th>2</th>
      <td>벌</td>
      <td>6</td>
      <td>붕붕</td>
    </tr>
  </tbody>
</table>
</div>




```python
val2 = [[4,'멍멍'],            
       [2,'꼬꼬'],
       [6,'붕붕']]
id  = ['개','닭','벌']
col = ['다리수','울음소리']

df2 = pd.DataFrame(val2, index=id, columns=col)
df2
```




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
      <th>다리수</th>
      <th>울음소리</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>개</th>
      <td>4</td>
      <td>멍멍</td>
    </tr>
    <tr>
      <th>닭</th>
      <td>2</td>
      <td>꼬꼬</td>
    </tr>
    <tr>
      <th>벌</th>
      <td>6</td>
      <td>붕붕</td>
    </tr>
  </tbody>
</table>
</div>



## 3. 데이터프레임의 생성

### 1) 데이터를 직접 입력하는 경우

#### a. 행 단위로 자료값 입력 (리스트 of 리스트 활용)
* 앞선 예시 참조

#### b. 열 단위로 자료값 입력 (딕셔너리 활용)


```python
var3 = {'종류'     : ['개','닭','벌'],
        '다리수'   : [4,2,6],
        '울음소리' : ['멍멍','꼬꼬','붕붕']}

df3 = pd.DataFrame(var3)       # 데이터프레임 생성 후 변수(df1)에 저장
df3
```




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
      <th>종류</th>
      <th>다리수</th>
      <th>울음소리</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>개</td>
      <td>4</td>
      <td>멍멍</td>
    </tr>
    <tr>
      <th>1</th>
      <td>닭</td>
      <td>2</td>
      <td>꼬꼬</td>
    </tr>
    <tr>
      <th>2</th>
      <td>벌</td>
      <td>6</td>
      <td>붕붕</td>
    </tr>
  </tbody>
</table>
</div>





### 2) 외부데이터를 불러오는 경우

#### a. 엑셀파일 불러오기


```python
df4 = pd.read_excel('https://maeng-gun.github.io/pandas/raw_data_1.xlsx', thousands=',')
df4
```




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
      <th>지역본부</th>
      <th>시군지부</th>
      <th>사무소명</th>
      <th>사무소코드</th>
      <th>과목</th>
      <th>상품종류</th>
      <th>종목명</th>
      <th>자산구분</th>
      <th>발행일</th>
      <th>만기일</th>
      <th>발행금리</th>
      <th>할인금리</th>
      <th>이자계산구분</th>
      <th>이자계산기간</th>
      <th>자산유동화구분</th>
      <th>매출일</th>
      <th>매입일</th>
      <th>신용등급</th>
      <th>매입수익률</th>
      <th>액면(좌수)</th>
      <th>장부금액</th>
      <th>미수이자</th>
      <th>예수법인세의제</th>
      <th>최초장부금액</th>
      <th>시장수익율</th>
      <th>발행회사</th>
      <th>거래회사</th>
      <th>농축협예수사무소코드</th>
      <th>평가손익</th>
      <th>매입신용등급</th>
      <th>계속보유여부검토대상</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>강원지역본부</td>
      <td>강릉시지부</td>
      <td>강릉농협</td>
      <td>333050</td>
      <td>채권</td>
      <td>금융채</td>
      <td>현대캐피탈1474</td>
      <td>매도가능</td>
      <td>2014-01-07</td>
      <td>2021-01-07</td>
      <td>3.969</td>
      <td>0</td>
      <td>복리채</td>
      <td>12개월</td>
      <td>NaN</td>
      <td>2014-01-07</td>
      <td>2014-01-16</td>
      <td>AA</td>
      <td>3.95</td>
      <td>2000000000</td>
      <td>2057414292</td>
      <td>1920391</td>
      <td>0</td>
      <td>2002279609</td>
      <td>1.506</td>
      <td>현대캐피탈(주)</td>
      <td>삼성증권(주)</td>
      <td>NaN</td>
      <td>57020083</td>
      <td>AA+</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>강원지역본부</td>
      <td>강릉시지부</td>
      <td>강릉농협</td>
      <td>333050</td>
      <td>채권</td>
      <td>금융채</td>
      <td>국민은행3306이표일(3)07후-24</td>
      <td>매도가능</td>
      <td>2013-06-24</td>
      <td>2020-06-24</td>
      <td>3.610</td>
      <td>0</td>
      <td>이표채(FRN,전환)</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>2013-06-24</td>
      <td>2014-04-07</td>
      <td>AA+</td>
      <td>3.56</td>
      <td>2000000000</td>
      <td>2019191187</td>
      <td>0</td>
      <td>0</td>
      <td>2005653261</td>
      <td>1.210</td>
      <td>(주)국민은행</td>
      <td>삼성증권(주)</td>
      <td>NaN</td>
      <td>18721556</td>
      <td>AA+</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>강원지역본부</td>
      <td>강릉시지부</td>
      <td>강릉농협</td>
      <td>333050</td>
      <td>채권</td>
      <td>금융채</td>
      <td>현대커머셜236</td>
      <td>매도가능</td>
      <td>2016-04-07</td>
      <td>2026-04-07</td>
      <td>2.800</td>
      <td>0</td>
      <td>이표채(FRN,전환)</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>2016-04-07</td>
      <td>2016-04-07</td>
      <td>AA-</td>
      <td>2.75</td>
      <td>2000000000</td>
      <td>2076297044</td>
      <td>0</td>
      <td>0</td>
      <td>2008600000</td>
      <td>2.139</td>
      <td>현대커머셜(주)</td>
      <td>엔에이치투자증권(주)</td>
      <td>NaN</td>
      <td>70641649</td>
      <td>AA-</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>강원지역본부</td>
      <td>강릉시지부</td>
      <td>강릉농협</td>
      <td>333050</td>
      <td>채권</td>
      <td>금융채</td>
      <td>현대커머셜360-4</td>
      <td>매도가능</td>
      <td>2019-06-24</td>
      <td>2029-06-24</td>
      <td>2.567</td>
      <td>0</td>
      <td>이표채(FRN,전환)</td>
      <td>1개월</td>
      <td>NaN</td>
      <td>2019-06-24</td>
      <td>2019-11-08</td>
      <td>AA-</td>
      <td>2.75</td>
      <td>1600000000</td>
      <td>1590035132</td>
      <td>0</td>
      <td>0</td>
      <td>1575143871</td>
      <td>2.674</td>
      <td>현대커머셜(주)</td>
      <td>삼성증권(주)</td>
      <td>NaN</td>
      <td>14556643</td>
      <td>AA-</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강원지역본부</td>
      <td>강릉시지부</td>
      <td>강릉농협</td>
      <td>333050</td>
      <td>채권</td>
      <td>금융채(특금)</td>
      <td>팬택관련 채권</td>
      <td>만기보유</td>
      <td>2006-05-24</td>
      <td>2018-12-31</td>
      <td>4.480</td>
      <td>0</td>
      <td>할인채</td>
      <td>12개월</td>
      <td>NaN</td>
      <td>2006-05-24</td>
      <td>2006-05-24</td>
      <td>NaN</td>
      <td>5.20</td>
      <td>55078604</td>
      <td>27539302</td>
      <td>0</td>
      <td>0</td>
      <td>55078604</td>
      <td>2.674</td>
      <td>(주)팬택자산관리</td>
      <td>농협은행(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>AAA</td>
      <td>NaN</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1670</th>
      <td>충북지역본부</td>
      <td>충주시지부</td>
      <td>주덕농협</td>
      <td>417059</td>
      <td>채권</td>
      <td>회사채</td>
      <td>현대상선176-2</td>
      <td>매도가능</td>
      <td>2011-04-07</td>
      <td>2021-04-07</td>
      <td>1.000</td>
      <td>0</td>
      <td>이표채(FRN,전환)</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>2011-04-07</td>
      <td>2011-04-07</td>
      <td>NaN</td>
      <td>5.90</td>
      <td>208336682</td>
      <td>177871548</td>
      <td>0</td>
      <td>0</td>
      <td>209561718</td>
      <td>2.495</td>
      <td>현대상선(주)</td>
      <td>엔에이치투자증권(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>A</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1671</th>
      <td>충북지역본부</td>
      <td>충주시지부</td>
      <td>충주농협</td>
      <td>417015</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>남제천농협 정기예치 (남제천농협)</td>
      <td>기타유가</td>
      <td>2019-04-24</td>
      <td>2020-04-24</td>
      <td>2.800</td>
      <td>0</td>
      <td>복리채</td>
      <td>12개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2019-04-24</td>
      <td>NaN</td>
      <td>2.80</td>
      <td>2000000000</td>
      <td>2000000000</td>
      <td>0</td>
      <td>0</td>
      <td>2000000000</td>
      <td>2.495</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>421078.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1672</th>
      <td>충북지역본부</td>
      <td>충주시지부</td>
      <td>충주농협</td>
      <td>417015</td>
      <td>채권</td>
      <td>회사채</td>
      <td>현대상선177-2</td>
      <td>매도가능</td>
      <td>2011-07-07</td>
      <td>2021-04-07</td>
      <td>1.000</td>
      <td>0</td>
      <td>이표채(거치분할)</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>2011-07-07</td>
      <td>2011-07-08</td>
      <td>NaN</td>
      <td>5.80</td>
      <td>102199293</td>
      <td>87299763</td>
      <td>0</td>
      <td>0</td>
      <td>102193407</td>
      <td>2.495</td>
      <td>현대상선(주)</td>
      <td>엔에이치투자증권(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>A</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1673</th>
      <td>충북지역본부</td>
      <td>충주시지부</td>
      <td>충주농협</td>
      <td>417015</td>
      <td>채권</td>
      <td>회사채</td>
      <td>동부메탈10-1</td>
      <td>매도가능</td>
      <td>2012-04-16</td>
      <td>2020-02-16</td>
      <td>2.000</td>
      <td>0</td>
      <td>이표채(FRN,전환)</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>2012-04-16</td>
      <td>2012-04-17</td>
      <td>NaN</td>
      <td>5.35</td>
      <td>240000000</td>
      <td>144888240</td>
      <td>0</td>
      <td>0</td>
      <td>240660067</td>
      <td>2.495</td>
      <td>(주)동부메탈</td>
      <td>엔에이치투자증권(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>BBB+</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1674</th>
      <td>충북지역본부</td>
      <td>충주시지부</td>
      <td>충주농협</td>
      <td>417015</td>
      <td>채권</td>
      <td>회사채</td>
      <td>한진해운76-2</td>
      <td>매도가능</td>
      <td>2012-06-07</td>
      <td>2017-06-07</td>
      <td>5.900</td>
      <td>0</td>
      <td>이표채(FRN,전환)</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>2012-06-07</td>
      <td>2012-06-07</td>
      <td>NaN</td>
      <td>5.80</td>
      <td>1000000000</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1004300000</td>
      <td>2.495</td>
      <td>(주)한진해운</td>
      <td>엔에이치투자증권(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>A-</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1675 rows × 31 columns</p>
</div>



#### b. CSV 파일 불러오기


```python
df5 = pd.read_csv('https://maeng-gun.github.io/pandas/raw_data_2.csv', thousands=',', compression='gzip')
df5
```

    /usr/local/lib/python3.6/dist-packages/IPython/core/interactiveshell.py:2718: DtypeWarning: Columns (31) have mixed types.Specify dtype option on import or set low_memory=False.
      interactivity=interactivity, compiler=compiler, result=result)
    




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
      <th>Unnamed: 0</th>
      <th>지역본부</th>
      <th>시군지부</th>
      <th>사무소명</th>
      <th>사무소코드</th>
      <th>과목</th>
      <th>상품종류</th>
      <th>표준코드</th>
      <th>계좌번호</th>
      <th>종목명</th>
      <th>자산구분</th>
      <th>발행일</th>
      <th>만기일</th>
      <th>발행금리</th>
      <th>할인금리</th>
      <th>이자계산구분</th>
      <th>이자계산기간</th>
      <th>자산유동화구분</th>
      <th>매출일</th>
      <th>매입일</th>
      <th>신용등급</th>
      <th>매입수익률</th>
      <th>액면(좌수)</th>
      <th>장부금액</th>
      <th>미수이자</th>
      <th>예수법인세의제</th>
      <th>최초장부금액</th>
      <th>시장수익율</th>
      <th>발행회사</th>
      <th>거래회사</th>
      <th>농축협예수사무소코드</th>
      <th>평가손익</th>
      <th>매입신용등급</th>
      <th>계속보유여부검토대상</th>
      <th>매입수익률*장부금액</th>
      <th>보유일자</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>568304</td>
      <td>서울</td>
      <td>서울지역본부</td>
      <td>영동농협</td>
      <td>100012</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>DA1000120063</td>
      <td>100012-134-000721</td>
      <td>정기예탁금(능서농협)</td>
      <td>기타유가</td>
      <td>2014-03-18</td>
      <td>2015-03-18</td>
      <td>3.25</td>
      <td>0.0</td>
      <td>복리채</td>
      <td>12개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2014-03-18</td>
      <td>NaN</td>
      <td>3.25</td>
      <td>10.000000</td>
      <td>10.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.000000e+09</td>
      <td>3.5</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>203049.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>32.5</td>
      <td>2015-01-31</td>
    </tr>
    <tr>
      <th>1</th>
      <td>568305</td>
      <td>서울</td>
      <td>서울지역본부</td>
      <td>영동농협</td>
      <td>100012</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>DA1000120064</td>
      <td>100012-134-000734</td>
      <td>정기예탁금(남면농협)</td>
      <td>기타유가</td>
      <td>2014-03-27</td>
      <td>2015-03-27</td>
      <td>3.20</td>
      <td>0.0</td>
      <td>단리채</td>
      <td>1개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2014-03-27</td>
      <td>NaN</td>
      <td>3.20</td>
      <td>30.000000</td>
      <td>30.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.000000e+09</td>
      <td>3.5</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>201162.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>96.0</td>
      <td>2015-01-31</td>
    </tr>
    <tr>
      <th>2</th>
      <td>568306</td>
      <td>서울</td>
      <td>서울지역본부</td>
      <td>영동농협</td>
      <td>100012</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>DA1000120065</td>
      <td>100012-134-000748</td>
      <td>정기예탁금(은현농협)</td>
      <td>기타유가</td>
      <td>2014-04-01</td>
      <td>2015-04-01</td>
      <td>3.20</td>
      <td>0.0</td>
      <td>단리채</td>
      <td>12개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2014-04-01</td>
      <td>NaN</td>
      <td>3.20</td>
      <td>33.000000</td>
      <td>33.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.300000e+09</td>
      <td>3.5</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>201173.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>105.6</td>
      <td>2015-01-31</td>
    </tr>
    <tr>
      <th>3</th>
      <td>568307</td>
      <td>서울</td>
      <td>서울지역본부</td>
      <td>영동농협</td>
      <td>100012</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>DA1000120070</td>
      <td>100012-134-000796</td>
      <td>정기예탁금(개군농협)</td>
      <td>기타유가</td>
      <td>2014-06-16</td>
      <td>2015-06-16</td>
      <td>3.10</td>
      <td>0.0</td>
      <td>복리채</td>
      <td>12개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2014-06-16</td>
      <td>NaN</td>
      <td>3.10</td>
      <td>35.000000</td>
      <td>35.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.500000e+09</td>
      <td>3.5</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>231046.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>108.5</td>
      <td>2015-01-31</td>
    </tr>
    <tr>
      <th>4</th>
      <td>568308</td>
      <td>서울</td>
      <td>서울지역본부</td>
      <td>영동농협</td>
      <td>100012</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>DA1000120073</td>
      <td>100012-134-000825</td>
      <td>정기예탁금(물금농협)</td>
      <td>기타유가</td>
      <td>2014-08-05</td>
      <td>2015-02-05</td>
      <td>3.10</td>
      <td>0.0</td>
      <td>복리채</td>
      <td>6개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2014-08-05</td>
      <td>NaN</td>
      <td>3.10</td>
      <td>30.000000</td>
      <td>30.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.000000e+09</td>
      <td>3.5</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>813060.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>93.0</td>
      <td>2015-01-31</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>229000</th>
      <td>797304</td>
      <td>제주</td>
      <td>제주시지부</td>
      <td>제주시농협</td>
      <td>901018</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>DA9010180047</td>
      <td>901018-134-000786</td>
      <td>정기예탁금 (애월농협)</td>
      <td>기타유가</td>
      <td>2020-06-12</td>
      <td>2021-06-12</td>
      <td>1.65</td>
      <td>0.0</td>
      <td>단리채</td>
      <td>12개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2020-06-12</td>
      <td>NaN</td>
      <td>1.65</td>
      <td>50.000000</td>
      <td>50.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.000000e+09</td>
      <td>6.5</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>901125.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>82.5</td>
      <td>2020-08-31</td>
    </tr>
    <tr>
      <th>229001</th>
      <td>797305</td>
      <td>제주</td>
      <td>제주시지부</td>
      <td>제주시농협</td>
      <td>901018</td>
      <td>대내외예치금</td>
      <td>농축협예치금</td>
      <td>DA9010180048</td>
      <td>901018-134-000790</td>
      <td>정기예탁금 (회천농협)</td>
      <td>기타유가</td>
      <td>2020-07-27</td>
      <td>2020-10-27</td>
      <td>1.40</td>
      <td>0.0</td>
      <td>단리채</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>0000-00-00</td>
      <td>2020-07-27</td>
      <td>NaN</td>
      <td>1.40</td>
      <td>30.000000</td>
      <td>30.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.000000e+09</td>
      <td>6.5</td>
      <td>농축협공통</td>
      <td>농축협공통</td>
      <td>621047.0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>42.0</td>
      <td>2020-08-31</td>
    </tr>
    <tr>
      <th>229002</th>
      <td>797306</td>
      <td>제주</td>
      <td>서귀포시지부</td>
      <td>대정농협</td>
      <td>903013</td>
      <td>채권</td>
      <td>회사채</td>
      <td>KR6117931263</td>
      <td>903013-134-000348</td>
      <td>한진해운76-2</td>
      <td>매도가능</td>
      <td>2012-06-07</td>
      <td>2017-06-07</td>
      <td>5.90</td>
      <td>0.0</td>
      <td>이표채(FRN,전환)</td>
      <td>3개월</td>
      <td>NaN</td>
      <td>2012-06-07</td>
      <td>2012-07-13</td>
      <td>NaN</td>
      <td>5.73</td>
      <td>40.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>4.028513e+09</td>
      <td>6.5</td>
      <td>(주)한진해운</td>
      <td>유안타증권(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>A-</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>2020-08-31</td>
    </tr>
    <tr>
      <th>229003</th>
      <td>797307</td>
      <td>제주</td>
      <td>서귀포시지부</td>
      <td>안덕농협</td>
      <td>903024</td>
      <td>유동자산</td>
      <td>자산유동화기업어음(ABCP)</td>
      <td>CP0000021581</td>
      <td>903024-134-000181</td>
      <td>루카스ABCP</td>
      <td>만기보유</td>
      <td>2013-12-27</td>
      <td>2015-12-31</td>
      <td>3.77</td>
      <td>0.0</td>
      <td>할인채</td>
      <td>12개월</td>
      <td>ABCP</td>
      <td>0000-00-00</td>
      <td>2013-12-27</td>
      <td>NaN</td>
      <td>3.77</td>
      <td>3.247726</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.247726e+08</td>
      <td>6.5</td>
      <td>루카스(주)</td>
      <td>엔에이치투자증권(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>A2</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>2020-08-31</td>
    </tr>
    <tr>
      <th>229004</th>
      <td>797308</td>
      <td>제주</td>
      <td>서귀포시지부</td>
      <td>안덕농협</td>
      <td>903024</td>
      <td>유동자산</td>
      <td>자산유동화기업어음(ABCP)</td>
      <td>CP0000021581</td>
      <td>903024-134-000195</td>
      <td>루카스ABCP</td>
      <td>만기보유</td>
      <td>2013-12-27</td>
      <td>2015-12-31</td>
      <td>3.77</td>
      <td>0.0</td>
      <td>할인채</td>
      <td>12개월</td>
      <td>ABCP</td>
      <td>0000-00-00</td>
      <td>2013-12-27</td>
      <td>NaN</td>
      <td>3.77</td>
      <td>3.247726</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.247726e+08</td>
      <td>6.5</td>
      <td>루카스(주)</td>
      <td>엔에이치투자증권(주)</td>
      <td>NaN</td>
      <td>0</td>
      <td>A2</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>2020-08-31</td>
    </tr>
  </tbody>
</table>
<p>229005 rows × 36 columns</p>
</div>



#### c. 클립보드에서 불러오기 (엑셀 복사 범위)
* 로컬 환경에서만 쓸 수 있고, 구글코랩에서는 에러 발생
* 활성화된 엑셀 시트에서 특정 범위를 직접 복사(Ctrl + C)한 뒤, 판다스 데이터프레임으로 변환하는 방식


```python
df6 = pd.read_clipboard(thousands=',')
df6
```


    ---------------------------------------------------------------------------

    PyperclipException                        Traceback (most recent call last)

    <ipython-input-6-8e7904951b21> in <module>()
    ----> 1 df6 = pd.read_clipboard(thousands=',')
          2 df6
    

    /usr/local/lib/python3.6/dist-packages/pandas/io/clipboards.py in read_clipboard(sep, **kwargs)
         36     from pandas.io.parsers import read_csv
         37 
    ---> 38     text = clipboard_get()
         39 
         40     # Try to decode (if needed, as "text" might already be a string here).
    

    /usr/local/lib/python3.6/dist-packages/pandas/io/clipboard/__init__.py in lazy_load_stub_paste()
        647     global copy, paste
        648     copy, paste = determine_clipboard()
    --> 649     return paste()
        650 
        651 
    

    /usr/local/lib/python3.6/dist-packages/pandas/io/clipboard/__init__.py in __call__(self, *args, **kwargs)
        285     class ClipboardUnavailable:
        286         def __call__(self, *args, **kwargs):
    --> 287             raise PyperclipException(EXCEPT_MSG)
        288 
        289         def __bool__(self) -> bool:
    

    PyperclipException: 
        Pyperclip could not find a copy/paste mechanism for your system.
        For more information, please visit
        https://pyperclip.readthedocs.io/en/latest/introduction.html#not-implemented-error
        

