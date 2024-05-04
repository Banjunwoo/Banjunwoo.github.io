---
layout: single
title:  "주식차트 그리기"

---

<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {
      vertical-align: middle;
  }

  .dataframe tbody tr th {
      vertical-align: top;
  }

  .dataframe thead th {
      text-align: center !important;
      padding: 8px;
  }

  .page__content p {
      margin: 0 0 0px !important;
  }

  .page__content p > strong {
    font-size: 0.8rem !important;
  }

  </style>
</head>


### Python for finance with Oreally

Quandl 계정 설치

API

M-xoxW1XQYbdC11GoPtm



```python
pip install quandl numpy pandas matplotlib
```

<pre>
Collecting quandl
  Downloading Quandl-3.7.0-py2.py3-none-any.whl (26 kB)
Requirement already satisfied: numpy in /usr/local/lib/python3.10/dist-packages (1.25.2)
Requirement already satisfied: pandas in /usr/local/lib/python3.10/dist-packages (2.0.3)
Requirement already satisfied: matplotlib in /usr/local/lib/python3.10/dist-packages (3.7.1)
Requirement already satisfied: requests>=2.7.0 in /usr/local/lib/python3.10/dist-packages (from quandl) (2.31.0)
Collecting inflection>=0.3.1 (from quandl)
  Downloading inflection-0.5.1-py2.py3-none-any.whl (9.5 kB)
Requirement already satisfied: python-dateutil in /usr/local/lib/python3.10/dist-packages (from quandl) (2.8.2)
Requirement already satisfied: six in /usr/local/lib/python3.10/dist-packages (from quandl) (1.16.0)
Requirement already satisfied: more-itertools in /usr/local/lib/python3.10/dist-packages (from quandl) (10.1.0)
Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.10/dist-packages (from pandas) (2023.4)
Requirement already satisfied: tzdata>=2022.1 in /usr/local/lib/python3.10/dist-packages (from pandas) (2024.1)
Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (1.2.1)
Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (0.12.1)
Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (4.51.0)
Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (1.4.5)
Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (24.0)
Requirement already satisfied: pillow>=6.2.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (9.4.0)
Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib) (3.1.2)
Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.10/dist-packages (from requests>=2.7.0->quandl) (3.3.2)
Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.10/dist-packages (from requests>=2.7.0->quandl) (3.7)
Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/local/lib/python3.10/dist-packages (from requests>=2.7.0->quandl) (2.0.7)
Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.10/dist-packages (from requests>=2.7.0->quandl) (2024.2.2)
Installing collected packages: inflection, quandl
Successfully installed inflection-0.5.1 quandl-3.7.0
</pre>

```python
import quandl

# API key

QUANDL_API_KEY='M-xoxW1XQYbdC11GoPtm'
quandl.ApiConfig.api_key = QUANDL_API_KEY
df = quandl.get('EURONEXT/ABN')
```


```python
df.head()
```

<pre>
             Open   High     Low   Last      Volume      Turnover
Date                                                             
2015-11-20  18.18  18.43  18.000  18.35  38392898.0  7.003281e+08
2015-11-23  18.45  18.70  18.215  18.61   3352514.0  6.186446e+07
2015-11-24  18.70  18.80  18.370  18.80   4871901.0  8.994087e+07
2015-11-25  18.85  19.50  18.770  19.45   4802607.0  9.153862e+07
2015-11-26  19.48  19.67  19.410  19.43   1648481.0  3.220713e+07
</pre>

```python
df.tail()
```

<pre>
             Open    High     Low    Last     Volume    Turnover
Date                                                            
2021-05-26  10.89  10.890  10.496  10.644  3447200.0  36676187.0
2021-05-27  10.60  10.980  10.584  10.902  3498258.0  38042273.0
2021-05-28  10.90  10.998  10.856  10.964  3001692.0  32847836.0
2021-05-31  11.00  11.030  10.920  10.920  1426676.0  15650390.0
2021-06-01  10.98  11.220  10.980  11.142  2689318.0  29976401.0
</pre>
OPEN = 시가

High = 고가

Low = 저가

Last = 종가

Volume = 거래량



```python
%matplotlib inline
import matplotlib.pyplot as plt

df.plot()
```

<pre>
<Axes: xlabel='Date'>
</pre>
<pre>
<Figure size 640x480 with 1 Axes>
</pre>

```python
prices =df['Last']
volumes =df['Volume']
```


```python
prices.head()
```

<pre>
Date
2015-11-20    18.35
2015-11-23    18.61
2015-11-24    18.80
2015-11-25    19.45
2015-11-26    19.43
Name: Last, dtype: float64
</pre>

```python
volumes.tail()
```

<pre>
Date
2021-05-26    3447200.0
2021-05-27    3498258.0
2021-05-28    3001692.0
2021-05-31    1426676.0
2021-06-01    2689318.0
Name: Volume, dtype: float64
</pre>

```python
 # The top plot consisting of daily closing prices
top = plt.subplot2grid((4, 4), (0, 0), rowspan=3, colspan=4)
top.plot(prices.index, prices, label='Last')
plt.title('ABN Last Price from 2015 - 2021')
plt.legend(loc=2)

  # The bottom plot consisting of daily trading volume
bottom = plt.subplot2grid((4, 4), (3,0), rowspan=1, colspan=4)
bottom.bar(volumes.index, volumes)
plt.title('ABN Daily Trading Volume')

plt.gcf().set_size_inches(12, 8)
plt.subplots_adjust(hspace=0.75)
```

<pre>
<Figure size 1200x800 with 2 Axes>
</pre>
Euronext 거래소의 ANB amro 주가차트

2015~2021년까지의 데이터가 확인 가능하다.







4 by 4 크기로 그래프를 그렸고, (0,0)은 왼쪽 상단 모서리 고정을 의미하며, row spans는 플롯이 4개 행 중 3개 사용하였다. col spans는 플롯이 4개열 모두 사용



```python
pip install mpl-finance
```

<pre>
Collecting mpl-finance
  Downloading mpl_finance-0.10.1-py3-none-any.whl (8.4 kB)
Requirement already satisfied: matplotlib in /usr/local/lib/python3.10/dist-packages (from mpl-finance) (3.7.1)
Requirement already satisfied: contourpy>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (1.2.1)
Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (0.12.1)
Requirement already satisfied: fonttools>=4.22.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (4.51.0)
Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (1.4.5)
Requirement already satisfied: numpy>=1.20 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (1.25.2)
Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (24.0)
Requirement already satisfied: pillow>=6.2.0 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (9.4.0)
Requirement already satisfied: pyparsing>=2.3.1 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (3.1.2)
Requirement already satisfied: python-dateutil>=2.7 in /usr/local/lib/python3.10/dist-packages (from matplotlib->mpl-finance) (2.8.2)
Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.10/dist-packages (from python-dateutil>=2.7->matplotlib->mpl-finance) (1.16.0)
Installing collected packages: mpl-finance
Successfully installed mpl-finance-0.10.1
</pre>

```python
%matplotlib inline
import quandl
from mpl_finance import candlestick_ohlc
import matplotlib.dates as mdates
import matplotlib.pyplot as plt

quandl.ApiConfig.api_key = QUANDL_API_KEY
df_subset = quandl.get('EURONEXT/ABN',
                        start_date='2018-07-01',
                        end_date='2018-07-31')

df_subset['Date'] = df_subset.index.map(mdates.date2num)
df_ohlc = df_subset[['Date','Open', 'High', 'Low', 'Last']]

figure, ax = plt.subplots(figsize = (8,4))
formatter = mdates.DateFormatter('%Y-%m-%d')
ax.xaxis.set_major_formatter(formatter)
candlestick_ohlc(ax,
                  df_ohlc.values,
                  width=0.8,
                  colorup='green',
                  colordown='red')
plt.show()
```

<pre>
<Figure size 800x400 with 1 Axes>
</pre>