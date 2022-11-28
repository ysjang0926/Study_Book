# Chaper 1: 판다스 소개
> 1장에서는 판다스로 샘플 데이터셋을 분석하여 라이브러리가 무엇을 할 수 있는지에 대한 전체적인 그림을 그려볼 수 있도록 개요를 제공합니다.

* 판다스 : 파이썬 프로그랠밍 언어를 기반으로 구축된 데이터 분석용 라이브러리
  * 라이브러리(또는 패키지) : 특정 분야의 문제를 해결하기 위한 코드 모음
* 판다스는 정렬, 필터링, 정리, 중복 제거, 집계, 피벗 등의 데이터 조작 작업을 위한 도구 모음
* 판다스 장점
  * 처리 능력과 사용자 생산성 사이의 균형이 좋음
  * 간단하고 직관적인 명령 집합을 제공

<br>

## 판다스 둘러보기
* 데이터 설명
  * 역대 최고의 수익을 올린 영화 700편의 데이터셋
  * 5개의 변수 : Rank(순위), Title(제목), Studio(제작사), Gross(총수익), Year(개봉연도)


### 1.1 데이터셋 가져오기



```python
# Load pandas library
import pandas as pd
```

* `read_csv()`
  * 판다스는 csv 파일의 내용을 DataFrame 객체로 가져옴
  * 객체 : 데이터를 저장하는 컨테이너
* 판다스는 한가지 유형의 객체(DataFrame)를 사용하여 다중 열의 데이터셋을 저장하고 다른 유형의 객체(Series)를 사용하여 단일 열 데이터셋을 저장함
  * DataFrame은 엑셀의 다중 열 테이블과 유사


```python
pd.read_csv("/content/movies.csv")
```





  <div id="df-ad811f60-1899-4b4a-8383-a89e0ef5d376">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Title</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Avengers: Endgame</td>
      <td>Buena Vista</td>
      <td>$2,796.30</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Avatar</td>
      <td>Fox</td>
      <td>$2,789.70</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Titanic</td>
      <td>Paramount</td>
      <td>$2,187.50</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Star Wars: The Force Awakens</td>
      <td>Buena Vista</td>
      <td>$2,068.20</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Avengers: Infinity War</td>
      <td>Buena Vista</td>
      <td>$2,048.40</td>
      <td>2018</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>777</th>
      <td>778</td>
      <td>Yogi Bear</td>
      <td>Warner Brothers</td>
      <td>$201.60</td>
      <td>2010</td>
    </tr>
    <tr>
      <th>778</th>
      <td>779</td>
      <td>Garfield: The Movie</td>
      <td>Fox</td>
      <td>$200.80</td>
      <td>2004</td>
    </tr>
    <tr>
      <th>779</th>
      <td>780</td>
      <td>Cats &amp; Dogs</td>
      <td>Warner Brothers</td>
      <td>$200.70</td>
      <td>2001</td>
    </tr>
    <tr>
      <th>780</th>
      <td>781</td>
      <td>The Hunt for Red October</td>
      <td>Paramount</td>
      <td>$200.50</td>
      <td>1990</td>
    </tr>
    <tr>
      <th>781</th>
      <td>782</td>
      <td>Valkyrie</td>
      <td>MGM</td>
      <td>$200.30</td>
      <td>2008</td>
    </tr>
  </tbody>
</table>
<p>782 rows × 5 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-ad811f60-1899-4b4a-8383-a89e0ef5d376')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-ad811f60-1899-4b4a-8383-a89e0ef5d376 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-ad811f60-1899-4b4a-8383-a89e0ef5d376');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




* 인덱스는 DataFrame의 왼쪽에 있는 오름차순 숫자
  * 인덱스 레이블은 데이터 행의 식별자 역할
  * 모든 열을 DataFrame의 인덱스로 설정할 수 있음
  * 인덱스에 적합한 열 : 각 행에 대한 기본 식별자 또는 참조 지점으로 사용할 수 있는 값


```python
pd.read_csv('/content/movies.csv', index_col="Title")
```





  <div id="df-f9b8e474-c8c9-4c89-a550-1e66e5078302">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Avengers: Endgame</th>
      <td>1</td>
      <td>Buena Vista</td>
      <td>$2,796.30</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>Avatar</th>
      <td>2</td>
      <td>Fox</td>
      <td>$2,789.70</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>Titanic</th>
      <td>3</td>
      <td>Paramount</td>
      <td>$2,187.50</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>Star Wars: The Force Awakens</th>
      <td>4</td>
      <td>Buena Vista</td>
      <td>$2,068.20</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Avengers: Infinity War</th>
      <td>5</td>
      <td>Buena Vista</td>
      <td>$2,048.40</td>
      <td>2018</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>Yogi Bear</th>
      <td>778</td>
      <td>Warner Brothers</td>
      <td>$201.60</td>
      <td>2010</td>
    </tr>
    <tr>
      <th>Garfield: The Movie</th>
      <td>779</td>
      <td>Fox</td>
      <td>$200.80</td>
      <td>2004</td>
    </tr>
    <tr>
      <th>Cats &amp; Dogs</th>
      <td>780</td>
      <td>Warner Brothers</td>
      <td>$200.70</td>
      <td>2001</td>
    </tr>
    <tr>
      <th>The Hunt for Red October</th>
      <td>781</td>
      <td>Paramount</td>
      <td>$200.50</td>
      <td>1990</td>
    </tr>
    <tr>
      <th>Valkyrie</th>
      <td>782</td>
      <td>MGM</td>
      <td>$200.30</td>
      <td>2008</td>
    </tr>
  </tbody>
</table>
<p>782 rows × 4 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-f9b8e474-c8c9-4c89-a550-1e66e5078302')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-f9b8e474-c8c9-4c89-a550-1e66e5078302 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-f9b8e474-c8c9-4c89-a550-1e66e5078302');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




* 다른 곳에 ㅊㅁ조할 수 있도록 DataFrame을 moview 변수에 할당함
  * 변수 : 객체에 사용자가 붙인 이름


```python
movies = pd.read_csv('/content/movies.csv', index_col="Title")
```

### 1.2 DataFrame 조작


```python
# 첫 몇 행
movies.head(4)
```





  <div id="df-43dbfac2-b5a8-49d7-82c4-c8e3c628f530">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Avengers: Endgame</th>
      <td>1</td>
      <td>Buena Vista</td>
      <td>$2,796.30</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>Avatar</th>
      <td>2</td>
      <td>Fox</td>
      <td>$2,789.70</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>Titanic</th>
      <td>3</td>
      <td>Paramount</td>
      <td>$2,187.50</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>Star Wars: The Force Awakens</th>
      <td>4</td>
      <td>Buena Vista</td>
      <td>$2,068.20</td>
      <td>2015</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-43dbfac2-b5a8-49d7-82c4-c8e3c628f530')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-43dbfac2-b5a8-49d7-82c4-c8e3c628f530 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-43dbfac2-b5a8-49d7-82c4-c8e3c628f530');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 마지막 몇 행
movies.tail(4)
```





  <div id="df-fb231d07-a98d-46a9-9dd3-aaaf9306b14d">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Garfield: The Movie</th>
      <td>779</td>
      <td>Fox</td>
      <td>$200.80</td>
      <td>2004</td>
    </tr>
    <tr>
      <th>Cats &amp; Dogs</th>
      <td>780</td>
      <td>Warner Brothers</td>
      <td>$200.70</td>
      <td>2001</td>
    </tr>
    <tr>
      <th>The Hunt for Red October</th>
      <td>781</td>
      <td>Paramount</td>
      <td>$200.50</td>
      <td>1990</td>
    </tr>
    <tr>
      <th>Valkyrie</th>
      <td>782</td>
      <td>MGM</td>
      <td>$200.30</td>
      <td>2008</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-fb231d07-a98d-46a9-9dd3-aaaf9306b14d')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-fb231d07-a98d-46a9-9dd3-aaaf9306b14d button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-fb231d07-a98d-46a9-9dd3-aaaf9306b14d');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 몇개의 행이 있는지
len(movies)
```




    782




```python
# 행과 열 개수 확인
movies.shape # 782개 행 / 4개 변수
```




    (782, 4)




```python
# 총 셀 개수
movies.size
```




    3128




```python
# 데이터 유형
## int64 : 정수열 / object : 텍스트열
movies.dtypes
```




    Rank       int64
    Studio    object
    Gross     object
    Year       int64
    dtype: object



* 1차원 레이블이 지정된 값 배열인 Series라는 새 객체를 반환함
  * 각 행에 대한 식별자가 있는 단일 데이터 열
  * Series의 인덱스 레이블은 4개의 변수임 -> 기존의 행값을 영로 변경하여 표시함


```python
# 행의 숫자 순서에 따른 행 추출 
## 인덱스는 0부터 계산함
movies.iloc[499]
```




    Rank           500
    Studio         Fox
    Gross     $288.30 
    Year          2018
    Name: Maze Runner: The Death Cure, dtype: object



* 인덱스 레이블을 사용하여 DataFrame 행에 접근할 수 있음


```python
movies.loc["Forrest Gump"]
```




    Rank            119
    Studio    Paramount
    Gross      $677.90 
    Year           1994
    Name: Forrest Gump, dtype: object




```python
movies.loc["101 Dalmatians"]
```





  <div id="df-6ce83ea3-fdc5-4a15-b8f2-13c998c40710">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>101 Dalmatians</th>
      <td>425</td>
      <td>Buena Vista</td>
      <td>$320.70</td>
      <td>1996</td>
    </tr>
    <tr>
      <th>101 Dalmatians</th>
      <td>708</td>
      <td>Buena Vista</td>
      <td>$215.90</td>
      <td>1961</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-6ce83ea3-fdc5-4a15-b8f2-13c998c40710')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-6ce83ea3-fdc5-4a15-b8f2-13c998c40710 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-6ce83ea3-fdc5-4a15-b8f2-13c998c40710');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 가장 최근에 개봉한 영화 다섯편
movies.sort_values(by = "Year", ascending = False).head()
```





  <div id="df-e0e0cc63-bbdc-4186-ab57-d5e3e435dad0">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Avengers: Endgame</th>
      <td>1</td>
      <td>Buena Vista</td>
      <td>$2,796.30</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>John Wick: Chapter 3 - Parabellum</th>
      <td>458</td>
      <td>Lionsgate</td>
      <td>$304.70</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>The Wandering Earth</th>
      <td>114</td>
      <td>China Film Corporation</td>
      <td>$699.80</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>Toy Story 4</th>
      <td>198</td>
      <td>Buena Vista</td>
      <td>$519.80</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>How to Train Your Dragon: The Hidden World</th>
      <td>199</td>
      <td>Universal</td>
      <td>$519.80</td>
      <td>2019</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-e0e0cc63-bbdc-4186-ab57-d5e3e435dad0')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-e0e0cc63-bbdc-4186-ab57-d5e3e435dad0 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-e0e0cc63-bbdc-4186-ab57-d5e3e435dad0');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 영화 제작사와 개봉일을 알파벳 순서대로 나열한 영화
movies.sort_values(by = ["Studio", "Year"]).head()
```





  <div id="df-d5106715-9f0c-45b0-b25f-edbadbde8ca5">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>The Blair Witch Project</th>
      <td>588</td>
      <td>Artisan</td>
      <td>$248.60</td>
      <td>1999</td>
    </tr>
    <tr>
      <th>101 Dalmatians</th>
      <td>708</td>
      <td>Buena Vista</td>
      <td>$215.90</td>
      <td>1961</td>
    </tr>
    <tr>
      <th>The Jungle Book</th>
      <td>755</td>
      <td>Buena Vista</td>
      <td>$205.80</td>
      <td>1967</td>
    </tr>
    <tr>
      <th>Who Framed Roger Rabbit</th>
      <td>410</td>
      <td>Buena Vista</td>
      <td>$329.80</td>
      <td>1988</td>
    </tr>
    <tr>
      <th>Dead Poets Society</th>
      <td>636</td>
      <td>Buena Vista</td>
      <td>$235.90</td>
      <td>1989</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-d5106715-9f0c-45b0-b25f-edbadbde8ca5')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-d5106715-9f0c-45b0-b25f-edbadbde8ca5 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-d5106715-9f0c-45b0-b25f-edbadbde8ca5');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 인덱스 정렬 -> 영화 제목을 알파벳 순서대로 보고 싶을 때
movies.sort_index().head()
```





  <div id="df-2718f9e9-7a73-48e5-981c-45439e448bc4">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10,000 B.C.</th>
      <td>536</td>
      <td>Warner Brothers</td>
      <td>$269.80</td>
      <td>2008</td>
    </tr>
    <tr>
      <th>101 Dalmatians</th>
      <td>708</td>
      <td>Buena Vista</td>
      <td>$215.90</td>
      <td>1961</td>
    </tr>
    <tr>
      <th>101 Dalmatians</th>
      <td>425</td>
      <td>Buena Vista</td>
      <td>$320.70</td>
      <td>1996</td>
    </tr>
    <tr>
      <th>2 Fast 2 Furious</th>
      <td>632</td>
      <td>Universal</td>
      <td>$236.40</td>
      <td>2003</td>
    </tr>
    <tr>
      <th>2012</th>
      <td>93</td>
      <td>Sony</td>
      <td>$769.70</td>
      <td>2009</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-2718f9e9-7a73-48e5-981c-45439e448bc4')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-2718f9e9-7a73-48e5-981c-45439e448bc4 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-2718f9e9-7a73-48e5-981c-45439e448bc4');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




## 1.3 Series의 값 계산
* 목표 : 가장 많은 수익을 올린 영화가 가장 많은 영화 제작사 찾기


```python
# 각 제작사가 Studio 열에서 나타나는 횟수가 필요함
movies["Studio"]
```




    Title
    Avengers: Endgame                   Buena Vista
    Avatar                                      Fox
    Titanic                               Paramount
    Star Wars: The Force Awakens        Buena Vista
    Avengers: Infinity War              Buena Vista
                                         ...       
    Yogi Bear                       Warner Brothers
    Garfield: The Movie                         Fox
    Cats & Dogs                     Warner Brothers
    The Hunt for Red October              Paramount
    Valkyrie                                    MGM
    Name: Studio, Length: 782, dtype: object




```python
# 반환값 : Series 객체
movies["Studio"].value_counts().head(5)
```




    Warner Brothers    132
    Buena Vista        125
    Fox                117
    Universal          109
    Sony                86
    Name: Studio, dtype: int64



## 1.4 하나 이상의 기준으로 열 필터링
* 목표 : 유니버셜 스튜디오에서 제작한 영화만 찾고 싶음


```python
movies[movies["Studio"]=="Universal"]
```





  <div id="df-f4c1be76-7f5d-40dc-aa90-3c5bd8001b38">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jurassic World</th>
      <td>6</td>
      <td>Universal</td>
      <td>$1,671.70</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Furious 7</th>
      <td>8</td>
      <td>Universal</td>
      <td>$1,516.00</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Jurassic World: Fallen Kingdom</th>
      <td>13</td>
      <td>Universal</td>
      <td>$1,309.50</td>
      <td>2018</td>
    </tr>
    <tr>
      <th>The Fate of the Furious</th>
      <td>17</td>
      <td>Universal</td>
      <td>$1,236.00</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>Minions</th>
      <td>19</td>
      <td>Universal</td>
      <td>$1,159.40</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>The Break-Up</th>
      <td>763</td>
      <td>Universal</td>
      <td>$205.00</td>
      <td>2006</td>
    </tr>
    <tr>
      <th>Everest</th>
      <td>766</td>
      <td>Universal</td>
      <td>$203.40</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Patch Adams</th>
      <td>772</td>
      <td>Universal</td>
      <td>$202.30</td>
      <td>1998</td>
    </tr>
    <tr>
      <th>Kindergarten Cop</th>
      <td>775</td>
      <td>Universal</td>
      <td>$202.00</td>
      <td>1990</td>
    </tr>
    <tr>
      <th>Straight Outta Compton</th>
      <td>776</td>
      <td>Universal</td>
      <td>$201.60</td>
      <td>2015</td>
    </tr>
  </tbody>
</table>
<p>109 rows × 4 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-f4c1be76-7f5d-40dc-aa90-3c5bd8001b38')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-f4c1be76-7f5d-40dc-aa90-3c5bd8001b38 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-f4c1be76-7f5d-40dc-aa90-3c5bd8001b38');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




* 필터링 조건을 변수에 할당하면 가독성이 높아짐


```python
released_by_universal = (movies["Studio"]=="Universal")
movies[released_by_universal].head()
```





  <div id="df-4cd018bd-70fa-4a72-b26c-c188c392c4c9">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jurassic World</th>
      <td>6</td>
      <td>Universal</td>
      <td>$1,671.70</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Furious 7</th>
      <td>8</td>
      <td>Universal</td>
      <td>$1,516.00</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Jurassic World: Fallen Kingdom</th>
      <td>13</td>
      <td>Universal</td>
      <td>$1,309.50</td>
      <td>2018</td>
    </tr>
    <tr>
      <th>The Fate of the Furious</th>
      <td>17</td>
      <td>Universal</td>
      <td>$1,236.00</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>Minions</th>
      <td>19</td>
      <td>Universal</td>
      <td>$1,159.40</td>
      <td>2015</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-4cd018bd-70fa-4a72-b26c-c188c392c4c9')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-4cd018bd-70fa-4a72-b26c-c188c392c4c9 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-4cd018bd-70fa-4a72-b26c-c188c392c4c9');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# Universal에서 제작 & 2015에 개봉
released_by_universal = (movies["Studio"]=="Universal")
released_in_2015 = (movies["Year"]==2015)
movies[released_by_universal & released_in_2015]
```





  <div id="df-96d88c41-f2b7-42c1-9b67-1c205aefebf5">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jurassic World</th>
      <td>6</td>
      <td>Universal</td>
      <td>$1,671.70</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Furious 7</th>
      <td>8</td>
      <td>Universal</td>
      <td>$1,516.00</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Minions</th>
      <td>19</td>
      <td>Universal</td>
      <td>$1,159.40</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Fifty Shades of Grey</th>
      <td>165</td>
      <td>Universal</td>
      <td>$571.00</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Pitch Perfect 2</th>
      <td>504</td>
      <td>Universal</td>
      <td>$287.50</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Ted 2</th>
      <td>702</td>
      <td>Universal</td>
      <td>$216.70</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Everest</th>
      <td>766</td>
      <td>Universal</td>
      <td>$203.40</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Straight Outta Compton</th>
      <td>776</td>
      <td>Universal</td>
      <td>$201.60</td>
      <td>2015</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-96d88c41-f2b7-42c1-9b67-1c205aefebf5')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-96d88c41-f2b7-42c1-9b67-1c205aefebf5 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-96d88c41-f2b7-42c1-9b67-1c205aefebf5');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# Universal에서 제작 or 2015에 개봉
released_by_universal = (movies["Studio"]=="Universal")
released_in_2015 = (movies["Year"]==2015)
movies[released_by_universal | released_in_2015]
```





  <div id="df-9f516a3b-93ae-4743-bf81-c067cafd05f8">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Star Wars: The Force Awakens</th>
      <td>4</td>
      <td>Buena Vista</td>
      <td>$2,068.20</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Jurassic World</th>
      <td>6</td>
      <td>Universal</td>
      <td>$1,671.70</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Furious 7</th>
      <td>8</td>
      <td>Universal</td>
      <td>$1,516.00</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Avengers: Age of Ultron</th>
      <td>9</td>
      <td>Buena Vista</td>
      <td>$1,405.40</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Jurassic World: Fallen Kingdom</th>
      <td>13</td>
      <td>Universal</td>
      <td>$1,309.50</td>
      <td>2018</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>The Break-Up</th>
      <td>763</td>
      <td>Universal</td>
      <td>$205.00</td>
      <td>2006</td>
    </tr>
    <tr>
      <th>Everest</th>
      <td>766</td>
      <td>Universal</td>
      <td>$203.40</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Patch Adams</th>
      <td>772</td>
      <td>Universal</td>
      <td>$202.30</td>
      <td>1998</td>
    </tr>
    <tr>
      <th>Kindergarten Cop</th>
      <td>775</td>
      <td>Universal</td>
      <td>$202.00</td>
      <td>1990</td>
    </tr>
    <tr>
      <th>Straight Outta Compton</th>
      <td>776</td>
      <td>Universal</td>
      <td>$201.60</td>
      <td>2015</td>
    </tr>
  </tbody>
</table>
<p>140 rows × 4 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-9f516a3b-93ae-4743-bf81-c067cafd05f8')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-9f516a3b-93ae-4743-bf81-c067cafd05f8 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-9f516a3b-93ae-4743-bf81-c067cafd05f8');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 1975년 이전에 개봉한 영화
before_1975 = movies["Year"] < 1975
movies[before_1975]
```





  <div id="df-3bb11442-5800-4206-8853-958e2a9d525b">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>The Exorcist</th>
      <td>252</td>
      <td>Warner Brothers</td>
      <td>$441.30</td>
      <td>1973</td>
    </tr>
    <tr>
      <th>Gone with the Wind</th>
      <td>288</td>
      <td>MGM</td>
      <td>$402.40</td>
      <td>1939</td>
    </tr>
    <tr>
      <th>Bambi</th>
      <td>540</td>
      <td>RKO</td>
      <td>$267.40</td>
      <td>1942</td>
    </tr>
    <tr>
      <th>The Godfather</th>
      <td>604</td>
      <td>Paramount</td>
      <td>$245.10</td>
      <td>1972</td>
    </tr>
    <tr>
      <th>101 Dalmatians</th>
      <td>708</td>
      <td>Buena Vista</td>
      <td>$215.90</td>
      <td>1961</td>
    </tr>
    <tr>
      <th>The Jungle Book</th>
      <td>755</td>
      <td>Buena Vista</td>
      <td>$205.80</td>
      <td>1967</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-3bb11442-5800-4206-8853-958e2a9d525b')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-3bb11442-5800-4206-8853-958e2a9d525b button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-3bb11442-5800-4206-8853-958e2a9d525b');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 1983년에서 1986년 사이에 개보앟ㄴ 영화
mid_80s = movies["Year"].between(1983, 1986)
movies[mid_80s]
```





  <div id="df-5b8b589f-3908-424c-95da-ea2619f8a384">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Return of the Jedi</th>
      <td>222</td>
      <td>Fox</td>
      <td>$475.10</td>
      <td>1983</td>
    </tr>
    <tr>
      <th>Back to the Future</th>
      <td>311</td>
      <td>Universal</td>
      <td>$381.10</td>
      <td>1985</td>
    </tr>
    <tr>
      <th>Top Gun</th>
      <td>357</td>
      <td>Paramount</td>
      <td>$356.80</td>
      <td>1986</td>
    </tr>
    <tr>
      <th>Indiana Jones and the Temple of Doom</th>
      <td>403</td>
      <td>Paramount</td>
      <td>$333.10</td>
      <td>1984</td>
    </tr>
    <tr>
      <th>Crocodile Dundee</th>
      <td>413</td>
      <td>Paramount</td>
      <td>$328.20</td>
      <td>1986</td>
    </tr>
    <tr>
      <th>Beverly Hills Cop</th>
      <td>432</td>
      <td>Paramount</td>
      <td>$316.40</td>
      <td>1984</td>
    </tr>
    <tr>
      <th>Rocky IV</th>
      <td>467</td>
      <td>MGM</td>
      <td>$300.50</td>
      <td>1985</td>
    </tr>
    <tr>
      <th>Rambo: First Blood Part II</th>
      <td>469</td>
      <td>TriStar</td>
      <td>$300.40</td>
      <td>1985</td>
    </tr>
    <tr>
      <th>Ghostbusters</th>
      <td>485</td>
      <td>Columbia</td>
      <td>$295.20</td>
      <td>1984</td>
    </tr>
    <tr>
      <th>Out of Africa</th>
      <td>662</td>
      <td>Universal</td>
      <td>$227.50</td>
      <td>1985</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-5b8b589f-3908-424c-95da-ea2619f8a384')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-5b8b589f-3908-424c-95da-ea2619f8a384 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-5b8b589f-3908-424c-95da-ea2619f8a384');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 영화 제목을 소문자로 바꾸고 제목에 'dark'라는 단어가 있는 영화
has_dark_in_title = movies.index.str.lower().str.contains("dark")
movies[has_dark_in_title]
```





  <div id="df-a81e0738-4ca5-4e0c-80a7-b600c2e21c61">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Transformers: Dark of the Moon</th>
      <td>23</td>
      <td>Paramount</td>
      <td>$1,123.80</td>
      <td>2011</td>
    </tr>
    <tr>
      <th>The Dark Knight Rises</th>
      <td>27</td>
      <td>Warner Brothers</td>
      <td>$1,084.90</td>
      <td>2012</td>
    </tr>
    <tr>
      <th>The Dark Knight</th>
      <td>39</td>
      <td>Warner Brothers</td>
      <td>$1,004.90</td>
      <td>2008</td>
    </tr>
    <tr>
      <th>Thor: The Dark World</th>
      <td>132</td>
      <td>Buena Vista</td>
      <td>$644.60</td>
      <td>2013</td>
    </tr>
    <tr>
      <th>Star Trek Into Darkness</th>
      <td>232</td>
      <td>Paramount</td>
      <td>$467.40</td>
      <td>2013</td>
    </tr>
    <tr>
      <th>Fifty Shades Darker</th>
      <td>309</td>
      <td>Universal</td>
      <td>$381.50</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>Dark Shadows</th>
      <td>600</td>
      <td>Warner Brothers</td>
      <td>$245.50</td>
      <td>2012</td>
    </tr>
    <tr>
      <th>Dark Phoenix</th>
      <td>603</td>
      <td>Fox</td>
      <td>$245.10</td>
      <td>2019</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-a81e0738-4ca5-4e0c-80a7-b600c2e21c61')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-a81e0738-4ca5-4e0c-80a7-b600c2e21c61 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-a81e0738-4ca5-4e0c-80a7-b600c2e21c61');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




## 1.5 데이터 그룹화
* 목적 : 어떤 제작사가 제작한 영화의 총수익이 가장 높은지
  * Gross 열의 값을 제작사별로 집계

* Gross 열의 값이 숫자가 아닌 텍스트로 저장됨
  * `$`와 `,`를 제거하는 과정이 필요함


```python
# $와 ,를 모두 빈텍스트로 바꾸기 & 부동 소수점 숫자로 변환
movies['Gross'].str.replace("$", "", regex=False).str.replace(",", "", regex=False).astype(float)
```




    Title
    Avengers: Endgame               2796.3
    Avatar                          2789.7
    Titanic                         2187.5
    Star Wars: The Force Awakens    2068.2
    Avengers: Infinity War          2048.4
                                     ...  
    Yogi Bear                        201.6
    Garfield: The Movie              200.8
    Cats & Dogs                      200.7
    The Hunt for Red October         200.5
    Valkyrie                         200.3
    Name: Gross, Length: 782, dtype: float64




```python
movies['Gross'] = (movies['Gross'].str.replace("$", "", regex=False).str.replace(",", "", regex=False).astype(float))
movies.head(5)
```





  <div id="df-891bbad1-7b96-43fe-b2a9-aa100a18c230">
    <div class="colab-df-container">
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
      <th>Rank</th>
      <th>Studio</th>
      <th>Gross</th>
      <th>Year</th>
    </tr>
    <tr>
      <th>Title</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Avengers: Endgame</th>
      <td>1</td>
      <td>Buena Vista</td>
      <td>2796.3</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>Avatar</th>
      <td>2</td>
      <td>Fox</td>
      <td>2789.7</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>Titanic</th>
      <td>3</td>
      <td>Paramount</td>
      <td>2187.5</td>
      <td>1997</td>
    </tr>
    <tr>
      <th>Star Wars: The Force Awakens</th>
      <td>4</td>
      <td>Buena Vista</td>
      <td>2068.2</td>
      <td>2015</td>
    </tr>
    <tr>
      <th>Avengers: Infinity War</th>
      <td>5</td>
      <td>Buena Vista</td>
      <td>2048.4</td>
      <td>2018</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-891bbad1-7b96-43fe-b2a9-aa100a18c230')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-891bbad1-7b96-43fe-b2a9-aa100a18c230 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-891bbad1-7b96-43fe-b2a9-aa100a18c230');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




* 제작사를 식별하고 각 제작사에 속한 영화를 bucket으로 지정해야함 -> 이과정이 그룹화
  * Studio 열의 값을 기반으로 DataFrame의 행을 그룹화하는 예제


```python
studios = movies.groupby("Studio")
```


```python
# 제작사 당 영화 수
studios["Gross"].count().sort_values(ascending=False).head()
```




    Studio
    Warner Brothers    132
    Buena Vista        125
    Fox                117
    Universal          109
    Sony                86
    Name: Gross, dtype: int64




```python
# 제작사 당 수익
studios["Gross"].sum().sort_values(ascending=False).head()
```




    Studio
    Buena Vista        73585.0
    Warner Brothers    58643.8
    Fox                50420.8
    Universal          44302.3
    Sony               32822.5
    Name: Gross, dtype: float64




```python
# 제작사 당 수익 평균
studios["Gross"].mean().sort_values(ascending=False).head()
```




    Studio
    HC                        870.300000
    China Film Corporation    699.800000
    Newmarket                 611.900000
    Buena Vista               588.680000
    Lionsgate                 477.771429
    Name: Gross, dtype: float64


