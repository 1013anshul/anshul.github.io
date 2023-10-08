```python
# import libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

import warnings
warnings.filterwarnings('ignore')

from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"
%matplotlib inline

pd.set_option("display.max_columns", 300)
pd.set_option("display.max_rows", 300)
```


```python
# read data
churn = pd.read_csv("telecom_data_for_students.csv")
```


```python
# look at initial rows of the data
churn.head(10)
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
      <th>mobile_number</th>
      <th>circle_id</th>
      <th>loc_og_t2o_mou</th>
      <th>std_og_t2o_mou</th>
      <th>loc_ic_t2o_mou</th>
      <th>last_date_of_month_6</th>
      <th>last_date_of_month_7</th>
      <th>last_date_of_month_8</th>
      <th>last_date_of_month_9</th>
      <th>arpu_6</th>
      <th>arpu_7</th>
      <th>arpu_8</th>
      <th>arpu_9</th>
      <th>onnet_mou_6</th>
      <th>onnet_mou_7</th>
      <th>onnet_mou_8</th>
      <th>onnet_mou_9</th>
      <th>offnet_mou_6</th>
      <th>offnet_mou_7</th>
      <th>offnet_mou_8</th>
      <th>offnet_mou_9</th>
      <th>roam_ic_mou_6</th>
      <th>roam_ic_mou_7</th>
      <th>roam_ic_mou_8</th>
      <th>roam_ic_mou_9</th>
      <th>roam_og_mou_6</th>
      <th>roam_og_mou_7</th>
      <th>roam_og_mou_8</th>
      <th>roam_og_mou_9</th>
      <th>loc_og_t2t_mou_6</th>
      <th>loc_og_t2t_mou_7</th>
      <th>loc_og_t2t_mou_8</th>
      <th>loc_og_t2t_mou_9</th>
      <th>loc_og_t2m_mou_6</th>
      <th>loc_og_t2m_mou_7</th>
      <th>loc_og_t2m_mou_8</th>
      <th>loc_og_t2m_mou_9</th>
      <th>loc_og_t2f_mou_6</th>
      <th>loc_og_t2f_mou_7</th>
      <th>loc_og_t2f_mou_8</th>
      <th>loc_og_t2f_mou_9</th>
      <th>loc_og_t2c_mou_6</th>
      <th>loc_og_t2c_mou_7</th>
      <th>loc_og_t2c_mou_8</th>
      <th>loc_og_t2c_mou_9</th>
      <th>loc_og_mou_6</th>
      <th>loc_og_mou_7</th>
      <th>loc_og_mou_8</th>
      <th>loc_og_mou_9</th>
      <th>std_og_t2t_mou_6</th>
      <th>std_og_t2t_mou_7</th>
      <th>std_og_t2t_mou_8</th>
      <th>std_og_t2t_mou_9</th>
      <th>std_og_t2m_mou_6</th>
      <th>std_og_t2m_mou_7</th>
      <th>std_og_t2m_mou_8</th>
      <th>std_og_t2m_mou_9</th>
      <th>std_og_t2f_mou_6</th>
      <th>std_og_t2f_mou_7</th>
      <th>std_og_t2f_mou_8</th>
      <th>std_og_t2f_mou_9</th>
      <th>std_og_t2c_mou_6</th>
      <th>std_og_t2c_mou_7</th>
      <th>std_og_t2c_mou_8</th>
      <th>std_og_t2c_mou_9</th>
      <th>std_og_mou_6</th>
      <th>std_og_mou_7</th>
      <th>std_og_mou_8</th>
      <th>std_og_mou_9</th>
      <th>isd_og_mou_6</th>
      <th>isd_og_mou_7</th>
      <th>isd_og_mou_8</th>
      <th>isd_og_mou_9</th>
      <th>spl_og_mou_6</th>
      <th>spl_og_mou_7</th>
      <th>spl_og_mou_8</th>
      <th>spl_og_mou_9</th>
      <th>og_others_6</th>
      <th>og_others_7</th>
      <th>og_others_8</th>
      <th>og_others_9</th>
      <th>total_og_mou_6</th>
      <th>total_og_mou_7</th>
      <th>total_og_mou_8</th>
      <th>total_og_mou_9</th>
      <th>loc_ic_t2t_mou_6</th>
      <th>loc_ic_t2t_mou_7</th>
      <th>loc_ic_t2t_mou_8</th>
      <th>loc_ic_t2t_mou_9</th>
      <th>loc_ic_t2m_mou_6</th>
      <th>loc_ic_t2m_mou_7</th>
      <th>loc_ic_t2m_mou_8</th>
      <th>loc_ic_t2m_mou_9</th>
      <th>loc_ic_t2f_mou_6</th>
      <th>loc_ic_t2f_mou_7</th>
      <th>loc_ic_t2f_mou_8</th>
      <th>loc_ic_t2f_mou_9</th>
      <th>loc_ic_mou_6</th>
      <th>loc_ic_mou_7</th>
      <th>loc_ic_mou_8</th>
      <th>loc_ic_mou_9</th>
      <th>std_ic_t2t_mou_6</th>
      <th>std_ic_t2t_mou_7</th>
      <th>std_ic_t2t_mou_8</th>
      <th>std_ic_t2t_mou_9</th>
      <th>std_ic_t2m_mou_6</th>
      <th>std_ic_t2m_mou_7</th>
      <th>std_ic_t2m_mou_8</th>
      <th>std_ic_t2m_mou_9</th>
      <th>std_ic_t2f_mou_6</th>
      <th>std_ic_t2f_mou_7</th>
      <th>std_ic_t2f_mou_8</th>
      <th>std_ic_t2f_mou_9</th>
      <th>std_ic_t2o_mou_6</th>
      <th>std_ic_t2o_mou_7</th>
      <th>std_ic_t2o_mou_8</th>
      <th>std_ic_t2o_mou_9</th>
      <th>std_ic_mou_6</th>
      <th>std_ic_mou_7</th>
      <th>std_ic_mou_8</th>
      <th>std_ic_mou_9</th>
      <th>total_ic_mou_6</th>
      <th>total_ic_mou_7</th>
      <th>total_ic_mou_8</th>
      <th>total_ic_mou_9</th>
      <th>spl_ic_mou_6</th>
      <th>spl_ic_mou_7</th>
      <th>spl_ic_mou_8</th>
      <th>spl_ic_mou_9</th>
      <th>isd_ic_mou_6</th>
      <th>isd_ic_mou_7</th>
      <th>isd_ic_mou_8</th>
      <th>isd_ic_mou_9</th>
      <th>ic_others_6</th>
      <th>ic_others_7</th>
      <th>ic_others_8</th>
      <th>ic_others_9</th>
      <th>total_rech_num_6</th>
      <th>total_rech_num_7</th>
      <th>total_rech_num_8</th>
      <th>total_rech_num_9</th>
      <th>total_rech_amt_6</th>
      <th>total_rech_amt_7</th>
      <th>total_rech_amt_8</th>
      <th>total_rech_amt_9</th>
      <th>max_rech_amt_6</th>
      <th>max_rech_amt_7</th>
      <th>max_rech_amt_8</th>
      <th>max_rech_amt_9</th>
      <th>date_of_last_rech_6</th>
      <th>date_of_last_rech_7</th>
      <th>date_of_last_rech_8</th>
      <th>date_of_last_rech_9</th>
      <th>last_day_rch_amt_6</th>
      <th>last_day_rch_amt_7</th>
      <th>last_day_rch_amt_8</th>
      <th>last_day_rch_amt_9</th>
      <th>date_of_last_rech_data_6</th>
      <th>date_of_last_rech_data_7</th>
      <th>date_of_last_rech_data_8</th>
      <th>date_of_last_rech_data_9</th>
      <th>total_rech_data_6</th>
      <th>total_rech_data_7</th>
      <th>total_rech_data_8</th>
      <th>total_rech_data_9</th>
      <th>max_rech_data_6</th>
      <th>max_rech_data_7</th>
      <th>max_rech_data_8</th>
      <th>max_rech_data_9</th>
      <th>count_rech_2g_6</th>
      <th>count_rech_2g_7</th>
      <th>count_rech_2g_8</th>
      <th>count_rech_2g_9</th>
      <th>count_rech_3g_6</th>
      <th>count_rech_3g_7</th>
      <th>count_rech_3g_8</th>
      <th>count_rech_3g_9</th>
      <th>av_rech_amt_data_6</th>
      <th>av_rech_amt_data_7</th>
      <th>av_rech_amt_data_8</th>
      <th>av_rech_amt_data_9</th>
      <th>vol_2g_mb_6</th>
      <th>vol_2g_mb_7</th>
      <th>vol_2g_mb_8</th>
      <th>vol_2g_mb_9</th>
      <th>vol_3g_mb_6</th>
      <th>vol_3g_mb_7</th>
      <th>vol_3g_mb_8</th>
      <th>vol_3g_mb_9</th>
      <th>arpu_3g_6</th>
      <th>arpu_3g_7</th>
      <th>arpu_3g_8</th>
      <th>arpu_3g_9</th>
      <th>arpu_2g_6</th>
      <th>arpu_2g_7</th>
      <th>arpu_2g_8</th>
      <th>arpu_2g_9</th>
      <th>night_pck_user_6</th>
      <th>night_pck_user_7</th>
      <th>night_pck_user_8</th>
      <th>night_pck_user_9</th>
      <th>monthly_2g_6</th>
      <th>monthly_2g_7</th>
      <th>monthly_2g_8</th>
      <th>monthly_2g_9</th>
      <th>sachet_2g_6</th>
      <th>sachet_2g_7</th>
      <th>sachet_2g_8</th>
      <th>sachet_2g_9</th>
      <th>monthly_3g_6</th>
      <th>monthly_3g_7</th>
      <th>monthly_3g_8</th>
      <th>monthly_3g_9</th>
      <th>sachet_3g_6</th>
      <th>sachet_3g_7</th>
      <th>sachet_3g_8</th>
      <th>sachet_3g_9</th>
      <th>fb_user_6</th>
      <th>fb_user_7</th>
      <th>fb_user_8</th>
      <th>fb_user_9</th>
      <th>aon</th>
      <th>aug_vbc_3g</th>
      <th>jul_vbc_3g</th>
      <th>jun_vbc_3g</th>
      <th>sep_vbc_3g</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7000842753</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>197.385</td>
      <td>214.816</td>
      <td>213.803</td>
      <td>21.100</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.16</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.13</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.15</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.44</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>5.44</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>4</td>
      <td>3</td>
      <td>2</td>
      <td>6</td>
      <td>362</td>
      <td>252</td>
      <td>252</td>
      <td>0</td>
      <td>252</td>
      <td>252</td>
      <td>252</td>
      <td>0</td>
      <td>6/21/2014</td>
      <td>7/16/2014</td>
      <td>8/8/2014</td>
      <td>9/28/2014</td>
      <td>252</td>
      <td>252</td>
      <td>252</td>
      <td>0</td>
      <td>6/21/2014</td>
      <td>7/16/2014</td>
      <td>8/8/2014</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>252.0</td>
      <td>252.0</td>
      <td>252.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>252.0</td>
      <td>252.0</td>
      <td>252.0</td>
      <td>NaN</td>
      <td>30.13</td>
      <td>1.32</td>
      <td>5.75</td>
      <td>0.0</td>
      <td>83.57</td>
      <td>150.76</td>
      <td>109.61</td>
      <td>0.00</td>
      <td>212.17</td>
      <td>212.17</td>
      <td>212.17</td>
      <td>NaN</td>
      <td>212.17</td>
      <td>212.17</td>
      <td>212.17</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>968</td>
      <td>30.40</td>
      <td>0.00</td>
      <td>101.20</td>
      <td>3.58</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7001865778</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>34.047</td>
      <td>355.074</td>
      <td>268.321</td>
      <td>86.285</td>
      <td>24.11</td>
      <td>78.68</td>
      <td>7.68</td>
      <td>18.34</td>
      <td>15.74</td>
      <td>99.84</td>
      <td>304.76</td>
      <td>53.76</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>23.88</td>
      <td>74.56</td>
      <td>7.68</td>
      <td>18.34</td>
      <td>11.51</td>
      <td>75.94</td>
      <td>291.86</td>
      <td>53.76</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>2.91</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>35.39</td>
      <td>150.51</td>
      <td>299.54</td>
      <td>72.11</td>
      <td>0.23</td>
      <td>4.11</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.46</td>
      <td>0.13</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.23</td>
      <td>4.58</td>
      <td>0.13</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>4.68</td>
      <td>23.43</td>
      <td>12.76</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>40.31</td>
      <td>178.53</td>
      <td>312.44</td>
      <td>72.11</td>
      <td>1.61</td>
      <td>29.91</td>
      <td>29.23</td>
      <td>116.09</td>
      <td>17.48</td>
      <td>65.38</td>
      <td>375.58</td>
      <td>56.93</td>
      <td>0.00</td>
      <td>8.93</td>
      <td>3.61</td>
      <td>0.00</td>
      <td>19.09</td>
      <td>104.23</td>
      <td>408.43</td>
      <td>173.03</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>2.35</td>
      <td>0.00</td>
      <td>5.90</td>
      <td>0.00</td>
      <td>12.49</td>
      <td>15.01</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.90</td>
      <td>0.00</td>
      <td>14.84</td>
      <td>15.01</td>
      <td>26.83</td>
      <td>104.23</td>
      <td>423.28</td>
      <td>188.04</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>1.83</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>4</td>
      <td>9</td>
      <td>11</td>
      <td>5</td>
      <td>74</td>
      <td>384</td>
      <td>283</td>
      <td>121</td>
      <td>44</td>
      <td>154</td>
      <td>65</td>
      <td>50</td>
      <td>6/29/2014</td>
      <td>7/31/2014</td>
      <td>8/28/2014</td>
      <td>9/30/2014</td>
      <td>44</td>
      <td>23</td>
      <td>30</td>
      <td>0</td>
      <td>NaN</td>
      <td>7/25/2014</td>
      <td>8/10/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>154.0</td>
      <td>25.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>154.0</td>
      <td>50.0</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>108.07</td>
      <td>365.47</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>28.61</td>
      <td>7.60</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>1006</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7001625959</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>167.690</td>
      <td>189.058</td>
      <td>210.226</td>
      <td>290.714</td>
      <td>11.54</td>
      <td>55.24</td>
      <td>37.26</td>
      <td>74.81</td>
      <td>143.33</td>
      <td>220.59</td>
      <td>208.36</td>
      <td>118.91</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>38.49</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>70.94</td>
      <td>7.19</td>
      <td>28.74</td>
      <td>13.58</td>
      <td>14.39</td>
      <td>29.34</td>
      <td>16.86</td>
      <td>38.46</td>
      <td>28.16</td>
      <td>24.11</td>
      <td>21.79</td>
      <td>15.61</td>
      <td>22.24</td>
      <td>0.00</td>
      <td>135.54</td>
      <td>45.76</td>
      <td>0.48</td>
      <td>60.66</td>
      <td>67.41</td>
      <td>67.66</td>
      <td>64.81</td>
      <td>4.34</td>
      <td>26.49</td>
      <td>22.58</td>
      <td>8.76</td>
      <td>41.81</td>
      <td>67.41</td>
      <td>75.53</td>
      <td>9.28</td>
      <td>1.48</td>
      <td>14.76</td>
      <td>22.83</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>47.64</td>
      <td>108.68</td>
      <td>120.94</td>
      <td>18.04</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>46.56</td>
      <td>236.84</td>
      <td>96.84</td>
      <td>42.08</td>
      <td>0.45</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>155.33</td>
      <td>412.94</td>
      <td>285.46</td>
      <td>124.94</td>
      <td>115.69</td>
      <td>71.11</td>
      <td>67.46</td>
      <td>148.23</td>
      <td>14.38</td>
      <td>15.44</td>
      <td>38.89</td>
      <td>38.98</td>
      <td>99.48</td>
      <td>122.29</td>
      <td>49.63</td>
      <td>158.19</td>
      <td>229.56</td>
      <td>208.86</td>
      <td>155.99</td>
      <td>345.41</td>
      <td>72.41</td>
      <td>71.29</td>
      <td>28.69</td>
      <td>49.44</td>
      <td>45.18</td>
      <td>177.01</td>
      <td>167.09</td>
      <td>118.18</td>
      <td>21.73</td>
      <td>58.34</td>
      <td>43.23</td>
      <td>3.86</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>139.33</td>
      <td>306.66</td>
      <td>239.03</td>
      <td>171.49</td>
      <td>370.04</td>
      <td>519.53</td>
      <td>395.03</td>
      <td>517.74</td>
      <td>0.21</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.45</td>
      <td>0.00</td>
      <td>0.85</td>
      <td>0.00</td>
      <td>0.01</td>
      <td>0.93</td>
      <td>3.14</td>
      <td>0.00</td>
      <td>0.36</td>
      <td>5</td>
      <td>4</td>
      <td>2</td>
      <td>7</td>
      <td>168</td>
      <td>315</td>
      <td>116</td>
      <td>358</td>
      <td>86</td>
      <td>200</td>
      <td>86</td>
      <td>100</td>
      <td>6/17/2014</td>
      <td>7/24/2014</td>
      <td>8/14/2014</td>
      <td>9/29/2014</td>
      <td>0</td>
      <td>200</td>
      <td>86</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/17/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>46.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>46.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>8.42</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.84</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>1103</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>4.17</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>7001204172</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>221.338</td>
      <td>251.102</td>
      <td>508.054</td>
      <td>389.500</td>
      <td>99.91</td>
      <td>54.39</td>
      <td>310.98</td>
      <td>241.71</td>
      <td>123.31</td>
      <td>109.01</td>
      <td>71.68</td>
      <td>113.54</td>
      <td>0.00</td>
      <td>54.86</td>
      <td>44.38</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>28.09</td>
      <td>39.04</td>
      <td>0.00</td>
      <td>73.68</td>
      <td>34.81</td>
      <td>10.61</td>
      <td>15.49</td>
      <td>107.43</td>
      <td>83.21</td>
      <td>22.46</td>
      <td>65.46</td>
      <td>1.91</td>
      <td>0.65</td>
      <td>4.91</td>
      <td>2.06</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>183.03</td>
      <td>118.68</td>
      <td>37.99</td>
      <td>83.03</td>
      <td>26.23</td>
      <td>14.89</td>
      <td>289.58</td>
      <td>226.21</td>
      <td>2.99</td>
      <td>1.73</td>
      <td>6.53</td>
      <td>9.99</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>29.23</td>
      <td>16.63</td>
      <td>296.11</td>
      <td>236.21</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>10.96</td>
      <td>0.00</td>
      <td>18.09</td>
      <td>43.29</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>223.23</td>
      <td>135.31</td>
      <td>352.21</td>
      <td>362.54</td>
      <td>62.08</td>
      <td>19.98</td>
      <td>8.04</td>
      <td>41.73</td>
      <td>113.96</td>
      <td>64.51</td>
      <td>20.28</td>
      <td>52.86</td>
      <td>57.43</td>
      <td>27.09</td>
      <td>19.84</td>
      <td>65.59</td>
      <td>233.48</td>
      <td>111.59</td>
      <td>48.18</td>
      <td>160.19</td>
      <td>43.48</td>
      <td>66.44</td>
      <td>0.00</td>
      <td>129.84</td>
      <td>1.33</td>
      <td>38.56</td>
      <td>4.94</td>
      <td>13.98</td>
      <td>1.18</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>45.99</td>
      <td>105.01</td>
      <td>4.94</td>
      <td>143.83</td>
      <td>280.08</td>
      <td>216.61</td>
      <td>53.13</td>
      <td>305.38</td>
      <td>0.59</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.55</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.80</td>
      <td>10</td>
      <td>11</td>
      <td>18</td>
      <td>14</td>
      <td>230</td>
      <td>310</td>
      <td>601</td>
      <td>410</td>
      <td>60</td>
      <td>50</td>
      <td>50</td>
      <td>50</td>
      <td>6/28/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>30</td>
      <td>50</td>
      <td>50</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2491</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7000142493</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>261.636</td>
      <td>309.876</td>
      <td>238.174</td>
      <td>163.426</td>
      <td>50.31</td>
      <td>149.44</td>
      <td>83.89</td>
      <td>58.78</td>
      <td>76.96</td>
      <td>91.88</td>
      <td>124.26</td>
      <td>45.81</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>50.31</td>
      <td>149.44</td>
      <td>83.89</td>
      <td>58.78</td>
      <td>67.64</td>
      <td>91.88</td>
      <td>124.26</td>
      <td>37.89</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>1.93</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>117.96</td>
      <td>241.33</td>
      <td>208.16</td>
      <td>98.61</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>9.31</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>9.31</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>5.98</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>127.28</td>
      <td>241.33</td>
      <td>208.16</td>
      <td>104.59</td>
      <td>105.68</td>
      <td>88.49</td>
      <td>233.81</td>
      <td>154.56</td>
      <td>106.84</td>
      <td>109.54</td>
      <td>104.13</td>
      <td>48.24</td>
      <td>1.50</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>214.03</td>
      <td>198.04</td>
      <td>337.94</td>
      <td>202.81</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.86</td>
      <td>2.31</td>
      <td>1.93</td>
      <td>0.25</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.93</td>
      <td>0.25</td>
      <td>0.86</td>
      <td>2.31</td>
      <td>216.44</td>
      <td>198.29</td>
      <td>338.81</td>
      <td>205.31</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.18</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.48</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>5</td>
      <td>6</td>
      <td>3</td>
      <td>4</td>
      <td>196</td>
      <td>350</td>
      <td>287</td>
      <td>200</td>
      <td>56</td>
      <td>110</td>
      <td>110</td>
      <td>50</td>
      <td>6/26/2014</td>
      <td>7/28/2014</td>
      <td>8/9/2014</td>
      <td>9/28/2014</td>
      <td>50</td>
      <td>110</td>
      <td>110</td>
      <td>50</td>
      <td>6/4/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1526</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>7000286308</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>50.258</td>
      <td>58.810</td>
      <td>83.386</td>
      <td>170.826</td>
      <td>50.16</td>
      <td>43.63</td>
      <td>85.48</td>
      <td>138.79</td>
      <td>19.28</td>
      <td>13.44</td>
      <td>14.46</td>
      <td>46.91</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>50.16</td>
      <td>43.63</td>
      <td>85.48</td>
      <td>138.79</td>
      <td>16.39</td>
      <td>8.83</td>
      <td>12.38</td>
      <td>44.78</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>2.13</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>66.56</td>
      <td>52.46</td>
      <td>97.86</td>
      <td>185.71</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>2.88</td>
      <td>4.61</td>
      <td>2.08</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.88</td>
      <td>4.61</td>
      <td>2.08</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>69.44</td>
      <td>57.08</td>
      <td>99.94</td>
      <td>185.71</td>
      <td>28.73</td>
      <td>30.03</td>
      <td>56.26</td>
      <td>68.38</td>
      <td>49.19</td>
      <td>57.44</td>
      <td>62.46</td>
      <td>84.01</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>77.93</td>
      <td>87.48</td>
      <td>118.73</td>
      <td>152.39</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>77.03</td>
      <td>71.06</td>
      <td>37.93</td>
      <td>52.03</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>77.03</td>
      <td>71.06</td>
      <td>37.93</td>
      <td>52.03</td>
      <td>155.39</td>
      <td>158.76</td>
      <td>157.13</td>
      <td>205.39</td>
      <td>0.43</td>
      <td>0.21</td>
      <td>0.23</td>
      <td>0.53</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.23</td>
      <td>0.43</td>
      <td>2</td>
      <td>2</td>
      <td>3</td>
      <td>3</td>
      <td>120</td>
      <td>0</td>
      <td>130</td>
      <td>130</td>
      <td>120</td>
      <td>0</td>
      <td>130</td>
      <td>130</td>
      <td>6/19/2014</td>
      <td>7/17/2014</td>
      <td>8/24/2014</td>
      <td>9/28/2014</td>
      <td>120</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1471</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7001051193</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>429.023</td>
      <td>190.704</td>
      <td>255.114</td>
      <td>114.751</td>
      <td>71.03</td>
      <td>45.03</td>
      <td>76.66</td>
      <td>15.23</td>
      <td>262.73</td>
      <td>49.24</td>
      <td>92.08</td>
      <td>50.33</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>71.03</td>
      <td>45.03</td>
      <td>76.14</td>
      <td>15.23</td>
      <td>252.23</td>
      <td>48.71</td>
      <td>80.63</td>
      <td>50.33</td>
      <td>10.38</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.11</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>333.64</td>
      <td>93.74</td>
      <td>156.78</td>
      <td>65.56</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.51</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.53</td>
      <td>11.45</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.53</td>
      <td>11.96</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.11</td>
      <td>0.53</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.35</td>
      <td>333.76</td>
      <td>94.81</td>
      <td>168.74</td>
      <td>65.91</td>
      <td>1857.99</td>
      <td>1427.04</td>
      <td>1896.43</td>
      <td>2334.88</td>
      <td>248.64</td>
      <td>336.96</td>
      <td>265.28</td>
      <td>231.41</td>
      <td>20.24</td>
      <td>22.69</td>
      <td>2.51</td>
      <td>6.19</td>
      <td>2126.89</td>
      <td>1786.71</td>
      <td>2164.23</td>
      <td>2572.49</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>1.39</td>
      <td>0.76</td>
      <td>2.60</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.39</td>
      <td>0.76</td>
      <td>2.60</td>
      <td>0.00</td>
      <td>2128.41</td>
      <td>1788.06</td>
      <td>2167.11</td>
      <td>2572.49</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.11</td>
      <td>0.58</td>
      <td>0.28</td>
      <td>0.00</td>
      <td>15</td>
      <td>10</td>
      <td>11</td>
      <td>7</td>
      <td>499</td>
      <td>222</td>
      <td>294</td>
      <td>141</td>
      <td>90</td>
      <td>37</td>
      <td>50</td>
      <td>30</td>
      <td>6/28/2014</td>
      <td>7/31/2014</td>
      <td>8/28/2014</td>
      <td>9/28/2014</td>
      <td>37</td>
      <td>24</td>
      <td>10</td>
      <td>24</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1673</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7000701601</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>1069.180</td>
      <td>1349.850</td>
      <td>3171.480</td>
      <td>500.000</td>
      <td>57.84</td>
      <td>54.68</td>
      <td>52.29</td>
      <td>NaN</td>
      <td>453.43</td>
      <td>567.16</td>
      <td>325.91</td>
      <td>NaN</td>
      <td>16.23</td>
      <td>33.49</td>
      <td>31.64</td>
      <td>NaN</td>
      <td>23.74</td>
      <td>12.59</td>
      <td>38.06</td>
      <td>NaN</td>
      <td>51.39</td>
      <td>31.38</td>
      <td>40.28</td>
      <td>NaN</td>
      <td>308.63</td>
      <td>447.38</td>
      <td>162.28</td>
      <td>NaN</td>
      <td>62.13</td>
      <td>55.14</td>
      <td>53.23</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>422.16</td>
      <td>533.91</td>
      <td>255.79</td>
      <td>NaN</td>
      <td>4.30</td>
      <td>23.29</td>
      <td>12.01</td>
      <td>NaN</td>
      <td>49.89</td>
      <td>31.76</td>
      <td>49.14</td>
      <td>NaN</td>
      <td>6.66</td>
      <td>20.08</td>
      <td>16.68</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>60.86</td>
      <td>75.14</td>
      <td>77.84</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.18</td>
      <td>10.01</td>
      <td>NaN</td>
      <td>4.50</td>
      <td>0.00</td>
      <td>6.50</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>487.53</td>
      <td>609.24</td>
      <td>350.16</td>
      <td>0.00</td>
      <td>58.14</td>
      <td>32.26</td>
      <td>27.31</td>
      <td>NaN</td>
      <td>217.56</td>
      <td>221.49</td>
      <td>121.19</td>
      <td>NaN</td>
      <td>152.16</td>
      <td>101.46</td>
      <td>39.53</td>
      <td>NaN</td>
      <td>427.88</td>
      <td>355.23</td>
      <td>188.04</td>
      <td>NaN</td>
      <td>36.89</td>
      <td>11.83</td>
      <td>30.39</td>
      <td>NaN</td>
      <td>91.44</td>
      <td>126.99</td>
      <td>141.33</td>
      <td>NaN</td>
      <td>52.19</td>
      <td>34.24</td>
      <td>22.21</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>180.54</td>
      <td>173.08</td>
      <td>193.94</td>
      <td>NaN</td>
      <td>626.46</td>
      <td>558.04</td>
      <td>428.74</td>
      <td>0.00</td>
      <td>0.21</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>2.06</td>
      <td>14.53</td>
      <td>31.59</td>
      <td>NaN</td>
      <td>15.74</td>
      <td>15.19</td>
      <td>15.14</td>
      <td>NaN</td>
      <td>5</td>
      <td>5</td>
      <td>7</td>
      <td>3</td>
      <td>1580</td>
      <td>790</td>
      <td>3638</td>
      <td>0</td>
      <td>1580</td>
      <td>790</td>
      <td>1580</td>
      <td>0</td>
      <td>6/27/2014</td>
      <td>7/25/2014</td>
      <td>8/26/2014</td>
      <td>9/30/2014</td>
      <td>0</td>
      <td>0</td>
      <td>779</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>802</td>
      <td>57.74</td>
      <td>19.38</td>
      <td>18.74</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>8</th>
      <td>7001524846</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>378.721</td>
      <td>492.223</td>
      <td>137.362</td>
      <td>166.787</td>
      <td>413.69</td>
      <td>351.03</td>
      <td>35.08</td>
      <td>33.46</td>
      <td>94.66</td>
      <td>80.63</td>
      <td>136.48</td>
      <td>108.71</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>297.13</td>
      <td>217.59</td>
      <td>12.49</td>
      <td>26.13</td>
      <td>80.96</td>
      <td>70.58</td>
      <td>50.54</td>
      <td>34.58</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>7.15</td>
      <td>0.00</td>
      <td>378.09</td>
      <td>288.18</td>
      <td>63.04</td>
      <td>60.71</td>
      <td>116.56</td>
      <td>133.43</td>
      <td>22.58</td>
      <td>7.33</td>
      <td>13.69</td>
      <td>10.04</td>
      <td>75.69</td>
      <td>74.13</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>130.26</td>
      <td>143.48</td>
      <td>98.28</td>
      <td>81.46</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>10.23</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>508.36</td>
      <td>431.66</td>
      <td>171.56</td>
      <td>142.18</td>
      <td>23.84</td>
      <td>9.84</td>
      <td>0.31</td>
      <td>4.03</td>
      <td>57.58</td>
      <td>13.98</td>
      <td>15.48</td>
      <td>17.34</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>81.43</td>
      <td>23.83</td>
      <td>15.79</td>
      <td>21.38</td>
      <td>0.00</td>
      <td>0.58</td>
      <td>0.10</td>
      <td>0.00</td>
      <td>22.43</td>
      <td>4.08</td>
      <td>0.65</td>
      <td>13.53</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>22.43</td>
      <td>4.66</td>
      <td>0.75</td>
      <td>13.53</td>
      <td>103.86</td>
      <td>28.49</td>
      <td>16.54</td>
      <td>34.91</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>19</td>
      <td>21</td>
      <td>14</td>
      <td>15</td>
      <td>437</td>
      <td>601</td>
      <td>120</td>
      <td>186</td>
      <td>90</td>
      <td>154</td>
      <td>30</td>
      <td>36</td>
      <td>6/25/2014</td>
      <td>7/31/2014</td>
      <td>8/30/2014</td>
      <td>9/30/2014</td>
      <td>50</td>
      <td>0</td>
      <td>10</td>
      <td>0</td>
      <td>NaN</td>
      <td>7/31/2014</td>
      <td>8/23/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>154.0</td>
      <td>23.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>177.0</td>
      <td>69.0</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>356.00</td>
      <td>0.03</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>750.95</td>
      <td>11.94</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>19.83</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>315</td>
      <td>21.03</td>
      <td>910.65</td>
      <td>122.16</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>9</th>
      <td>7001864400</td>
      <td>109</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>119.518</td>
      <td>247.435</td>
      <td>170.231</td>
      <td>160.042</td>
      <td>33.89</td>
      <td>30.11</td>
      <td>22.43</td>
      <td>27.84</td>
      <td>63.48</td>
      <td>54.16</td>
      <td>78.34</td>
      <td>123.48</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>33.89</td>
      <td>30.11</td>
      <td>22.43</td>
      <td>27.84</td>
      <td>38.03</td>
      <td>40.06</td>
      <td>34.93</td>
      <td>37.26</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>71.93</td>
      <td>70.18</td>
      <td>57.36</td>
      <td>65.11</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>25.45</td>
      <td>14.09</td>
      <td>43.41</td>
      <td>83.26</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>2.94</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>25.45</td>
      <td>14.09</td>
      <td>43.41</td>
      <td>86.21</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.66</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>98.04</td>
      <td>84.28</td>
      <td>100.78</td>
      <td>151.33</td>
      <td>129.34</td>
      <td>124.34</td>
      <td>49.93</td>
      <td>313.38</td>
      <td>132.94</td>
      <td>96.24</td>
      <td>122.58</td>
      <td>65.06</td>
      <td>0.40</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.48</td>
      <td>262.69</td>
      <td>220.59</td>
      <td>172.51</td>
      <td>378.93</td>
      <td>0.30</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>4.38</td>
      <td>32.86</td>
      <td>78.21</td>
      <td>1.74</td>
      <td>1.18</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>33.16</td>
      <td>78.21</td>
      <td>1.74</td>
      <td>5.56</td>
      <td>303.98</td>
      <td>327.31</td>
      <td>219.86</td>
      <td>412.63</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>8.11</td>
      <td>28.49</td>
      <td>45.59</td>
      <td>28.13</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>4</td>
      <td>2</td>
      <td>5</td>
      <td>3</td>
      <td>220</td>
      <td>195</td>
      <td>210</td>
      <td>180</td>
      <td>110</td>
      <td>154</td>
      <td>50</td>
      <td>130</td>
      <td>6/29/2014</td>
      <td>7/23/2014</td>
      <td>8/29/2014</td>
      <td>9/20/2014</td>
      <td>110</td>
      <td>154</td>
      <td>30</td>
      <td>50</td>
      <td>NaN</td>
      <td>7/23/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>154.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>154.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>7.37</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>902</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
# feature type summary
churn.info(verbose=1)
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 99999 entries, 0 to 99998
    Data columns (total 226 columns):
    mobile_number               int64
    circle_id                   int64
    loc_og_t2o_mou              float64
    std_og_t2o_mou              float64
    loc_ic_t2o_mou              float64
    last_date_of_month_6        object
    last_date_of_month_7        object
    last_date_of_month_8        object
    last_date_of_month_9        object
    arpu_6                      float64
    arpu_7                      float64
    arpu_8                      float64
    arpu_9                      float64
    onnet_mou_6                 float64
    onnet_mou_7                 float64
    onnet_mou_8                 float64
    onnet_mou_9                 float64
    offnet_mou_6                float64
    offnet_mou_7                float64
    offnet_mou_8                float64
    offnet_mou_9                float64
    roam_ic_mou_6               float64
    roam_ic_mou_7               float64
    roam_ic_mou_8               float64
    roam_ic_mou_9               float64
    roam_og_mou_6               float64
    roam_og_mou_7               float64
    roam_og_mou_8               float64
    roam_og_mou_9               float64
    loc_og_t2t_mou_6            float64
    loc_og_t2t_mou_7            float64
    loc_og_t2t_mou_8            float64
    loc_og_t2t_mou_9            float64
    loc_og_t2m_mou_6            float64
    loc_og_t2m_mou_7            float64
    loc_og_t2m_mou_8            float64
    loc_og_t2m_mou_9            float64
    loc_og_t2f_mou_6            float64
    loc_og_t2f_mou_7            float64
    loc_og_t2f_mou_8            float64
    loc_og_t2f_mou_9            float64
    loc_og_t2c_mou_6            float64
    loc_og_t2c_mou_7            float64
    loc_og_t2c_mou_8            float64
    loc_og_t2c_mou_9            float64
    loc_og_mou_6                float64
    loc_og_mou_7                float64
    loc_og_mou_8                float64
    loc_og_mou_9                float64
    std_og_t2t_mou_6            float64
    std_og_t2t_mou_7            float64
    std_og_t2t_mou_8            float64
    std_og_t2t_mou_9            float64
    std_og_t2m_mou_6            float64
    std_og_t2m_mou_7            float64
    std_og_t2m_mou_8            float64
    std_og_t2m_mou_9            float64
    std_og_t2f_mou_6            float64
    std_og_t2f_mou_7            float64
    std_og_t2f_mou_8            float64
    std_og_t2f_mou_9            float64
    std_og_t2c_mou_6            float64
    std_og_t2c_mou_7            float64
    std_og_t2c_mou_8            float64
    std_og_t2c_mou_9            float64
    std_og_mou_6                float64
    std_og_mou_7                float64
    std_og_mou_8                float64
    std_og_mou_9                float64
    isd_og_mou_6                float64
    isd_og_mou_7                float64
    isd_og_mou_8                float64
    isd_og_mou_9                float64
    spl_og_mou_6                float64
    spl_og_mou_7                float64
    spl_og_mou_8                float64
    spl_og_mou_9                float64
    og_others_6                 float64
    og_others_7                 float64
    og_others_8                 float64
    og_others_9                 float64
    total_og_mou_6              float64
    total_og_mou_7              float64
    total_og_mou_8              float64
    total_og_mou_9              float64
    loc_ic_t2t_mou_6            float64
    loc_ic_t2t_mou_7            float64
    loc_ic_t2t_mou_8            float64
    loc_ic_t2t_mou_9            float64
    loc_ic_t2m_mou_6            float64
    loc_ic_t2m_mou_7            float64
    loc_ic_t2m_mou_8            float64
    loc_ic_t2m_mou_9            float64
    loc_ic_t2f_mou_6            float64
    loc_ic_t2f_mou_7            float64
    loc_ic_t2f_mou_8            float64
    loc_ic_t2f_mou_9            float64
    loc_ic_mou_6                float64
    loc_ic_mou_7                float64
    loc_ic_mou_8                float64
    loc_ic_mou_9                float64
    std_ic_t2t_mou_6            float64
    std_ic_t2t_mou_7            float64
    std_ic_t2t_mou_8            float64
    std_ic_t2t_mou_9            float64
    std_ic_t2m_mou_6            float64
    std_ic_t2m_mou_7            float64
    std_ic_t2m_mou_8            float64
    std_ic_t2m_mou_9            float64
    std_ic_t2f_mou_6            float64
    std_ic_t2f_mou_7            float64
    std_ic_t2f_mou_8            float64
    std_ic_t2f_mou_9            float64
    std_ic_t2o_mou_6            float64
    std_ic_t2o_mou_7            float64
    std_ic_t2o_mou_8            float64
    std_ic_t2o_mou_9            float64
    std_ic_mou_6                float64
    std_ic_mou_7                float64
    std_ic_mou_8                float64
    std_ic_mou_9                float64
    total_ic_mou_6              float64
    total_ic_mou_7              float64
    total_ic_mou_8              float64
    total_ic_mou_9              float64
    spl_ic_mou_6                float64
    spl_ic_mou_7                float64
    spl_ic_mou_8                float64
    spl_ic_mou_9                float64
    isd_ic_mou_6                float64
    isd_ic_mou_7                float64
    isd_ic_mou_8                float64
    isd_ic_mou_9                float64
    ic_others_6                 float64
    ic_others_7                 float64
    ic_others_8                 float64
    ic_others_9                 float64
    total_rech_num_6            int64
    total_rech_num_7            int64
    total_rech_num_8            int64
    total_rech_num_9            int64
    total_rech_amt_6            int64
    total_rech_amt_7            int64
    total_rech_amt_8            int64
    total_rech_amt_9            int64
    max_rech_amt_6              int64
    max_rech_amt_7              int64
    max_rech_amt_8              int64
    max_rech_amt_9              int64
    date_of_last_rech_6         object
    date_of_last_rech_7         object
    date_of_last_rech_8         object
    date_of_last_rech_9         object
    last_day_rch_amt_6          int64
    last_day_rch_amt_7          int64
    last_day_rch_amt_8          int64
    last_day_rch_amt_9          int64
    date_of_last_rech_data_6    object
    date_of_last_rech_data_7    object
    date_of_last_rech_data_8    object
    date_of_last_rech_data_9    object
    total_rech_data_6           float64
    total_rech_data_7           float64
    total_rech_data_8           float64
    total_rech_data_9           float64
    max_rech_data_6             float64
    max_rech_data_7             float64
    max_rech_data_8             float64
    max_rech_data_9             float64
    count_rech_2g_6             float64
    count_rech_2g_7             float64
    count_rech_2g_8             float64
    count_rech_2g_9             float64
    count_rech_3g_6             float64
    count_rech_3g_7             float64
    count_rech_3g_8             float64
    count_rech_3g_9             float64
    av_rech_amt_data_6          float64
    av_rech_amt_data_7          float64
    av_rech_amt_data_8          float64
    av_rech_amt_data_9          float64
    vol_2g_mb_6                 float64
    vol_2g_mb_7                 float64
    vol_2g_mb_8                 float64
    vol_2g_mb_9                 float64
    vol_3g_mb_6                 float64
    vol_3g_mb_7                 float64
    vol_3g_mb_8                 float64
    vol_3g_mb_9                 float64
    arpu_3g_6                   float64
    arpu_3g_7                   float64
    arpu_3g_8                   float64
    arpu_3g_9                   float64
    arpu_2g_6                   float64
    arpu_2g_7                   float64
    arpu_2g_8                   float64
    arpu_2g_9                   float64
    night_pck_user_6            float64
    night_pck_user_7            float64
    night_pck_user_8            float64
    night_pck_user_9            float64
    monthly_2g_6                int64
    monthly_2g_7                int64
    monthly_2g_8                int64
    monthly_2g_9                int64
    sachet_2g_6                 int64
    sachet_2g_7                 int64
    sachet_2g_8                 int64
    sachet_2g_9                 int64
    monthly_3g_6                int64
    monthly_3g_7                int64
    monthly_3g_8                int64
    monthly_3g_9                int64
    sachet_3g_6                 int64
    sachet_3g_7                 int64
    sachet_3g_8                 int64
    sachet_3g_9                 int64
    fb_user_6                   float64
    fb_user_7                   float64
    fb_user_8                   float64
    fb_user_9                   float64
    aon                         int64
    aug_vbc_3g                  float64
    jul_vbc_3g                  float64
    jun_vbc_3g                  float64
    sep_vbc_3g                  float64
    dtypes: float64(179), int64(35), object(12)
    memory usage: 172.4+ MB


There are 99999 rows and 226 columns in the data. Lot of the columns are numeric type, but we need to inspect which are the categorical columns.


```python
# look at data statistics
churn.describe(include='all')
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
      <th>mobile_number</th>
      <th>circle_id</th>
      <th>loc_og_t2o_mou</th>
      <th>std_og_t2o_mou</th>
      <th>loc_ic_t2o_mou</th>
      <th>last_date_of_month_6</th>
      <th>last_date_of_month_7</th>
      <th>last_date_of_month_8</th>
      <th>last_date_of_month_9</th>
      <th>arpu_6</th>
      <th>arpu_7</th>
      <th>arpu_8</th>
      <th>arpu_9</th>
      <th>onnet_mou_6</th>
      <th>onnet_mou_7</th>
      <th>onnet_mou_8</th>
      <th>onnet_mou_9</th>
      <th>offnet_mou_6</th>
      <th>offnet_mou_7</th>
      <th>offnet_mou_8</th>
      <th>offnet_mou_9</th>
      <th>roam_ic_mou_6</th>
      <th>roam_ic_mou_7</th>
      <th>roam_ic_mou_8</th>
      <th>roam_ic_mou_9</th>
      <th>roam_og_mou_6</th>
      <th>roam_og_mou_7</th>
      <th>roam_og_mou_8</th>
      <th>roam_og_mou_9</th>
      <th>loc_og_t2t_mou_6</th>
      <th>loc_og_t2t_mou_7</th>
      <th>loc_og_t2t_mou_8</th>
      <th>loc_og_t2t_mou_9</th>
      <th>loc_og_t2m_mou_6</th>
      <th>loc_og_t2m_mou_7</th>
      <th>loc_og_t2m_mou_8</th>
      <th>loc_og_t2m_mou_9</th>
      <th>loc_og_t2f_mou_6</th>
      <th>loc_og_t2f_mou_7</th>
      <th>loc_og_t2f_mou_8</th>
      <th>loc_og_t2f_mou_9</th>
      <th>loc_og_t2c_mou_6</th>
      <th>loc_og_t2c_mou_7</th>
      <th>loc_og_t2c_mou_8</th>
      <th>loc_og_t2c_mou_9</th>
      <th>loc_og_mou_6</th>
      <th>loc_og_mou_7</th>
      <th>loc_og_mou_8</th>
      <th>loc_og_mou_9</th>
      <th>std_og_t2t_mou_6</th>
      <th>std_og_t2t_mou_7</th>
      <th>std_og_t2t_mou_8</th>
      <th>std_og_t2t_mou_9</th>
      <th>std_og_t2m_mou_6</th>
      <th>std_og_t2m_mou_7</th>
      <th>std_og_t2m_mou_8</th>
      <th>std_og_t2m_mou_9</th>
      <th>std_og_t2f_mou_6</th>
      <th>std_og_t2f_mou_7</th>
      <th>std_og_t2f_mou_8</th>
      <th>std_og_t2f_mou_9</th>
      <th>std_og_t2c_mou_6</th>
      <th>std_og_t2c_mou_7</th>
      <th>std_og_t2c_mou_8</th>
      <th>std_og_t2c_mou_9</th>
      <th>std_og_mou_6</th>
      <th>std_og_mou_7</th>
      <th>std_og_mou_8</th>
      <th>std_og_mou_9</th>
      <th>isd_og_mou_6</th>
      <th>isd_og_mou_7</th>
      <th>isd_og_mou_8</th>
      <th>isd_og_mou_9</th>
      <th>spl_og_mou_6</th>
      <th>spl_og_mou_7</th>
      <th>spl_og_mou_8</th>
      <th>spl_og_mou_9</th>
      <th>og_others_6</th>
      <th>og_others_7</th>
      <th>og_others_8</th>
      <th>og_others_9</th>
      <th>total_og_mou_6</th>
      <th>total_og_mou_7</th>
      <th>total_og_mou_8</th>
      <th>total_og_mou_9</th>
      <th>loc_ic_t2t_mou_6</th>
      <th>loc_ic_t2t_mou_7</th>
      <th>loc_ic_t2t_mou_8</th>
      <th>loc_ic_t2t_mou_9</th>
      <th>loc_ic_t2m_mou_6</th>
      <th>loc_ic_t2m_mou_7</th>
      <th>loc_ic_t2m_mou_8</th>
      <th>loc_ic_t2m_mou_9</th>
      <th>loc_ic_t2f_mou_6</th>
      <th>loc_ic_t2f_mou_7</th>
      <th>loc_ic_t2f_mou_8</th>
      <th>loc_ic_t2f_mou_9</th>
      <th>loc_ic_mou_6</th>
      <th>loc_ic_mou_7</th>
      <th>loc_ic_mou_8</th>
      <th>loc_ic_mou_9</th>
      <th>std_ic_t2t_mou_6</th>
      <th>std_ic_t2t_mou_7</th>
      <th>std_ic_t2t_mou_8</th>
      <th>std_ic_t2t_mou_9</th>
      <th>std_ic_t2m_mou_6</th>
      <th>std_ic_t2m_mou_7</th>
      <th>std_ic_t2m_mou_8</th>
      <th>std_ic_t2m_mou_9</th>
      <th>std_ic_t2f_mou_6</th>
      <th>std_ic_t2f_mou_7</th>
      <th>std_ic_t2f_mou_8</th>
      <th>std_ic_t2f_mou_9</th>
      <th>std_ic_t2o_mou_6</th>
      <th>std_ic_t2o_mou_7</th>
      <th>std_ic_t2o_mou_8</th>
      <th>std_ic_t2o_mou_9</th>
      <th>std_ic_mou_6</th>
      <th>std_ic_mou_7</th>
      <th>std_ic_mou_8</th>
      <th>std_ic_mou_9</th>
      <th>total_ic_mou_6</th>
      <th>total_ic_mou_7</th>
      <th>total_ic_mou_8</th>
      <th>total_ic_mou_9</th>
      <th>spl_ic_mou_6</th>
      <th>spl_ic_mou_7</th>
      <th>spl_ic_mou_8</th>
      <th>spl_ic_mou_9</th>
      <th>isd_ic_mou_6</th>
      <th>isd_ic_mou_7</th>
      <th>isd_ic_mou_8</th>
      <th>isd_ic_mou_9</th>
      <th>ic_others_6</th>
      <th>ic_others_7</th>
      <th>ic_others_8</th>
      <th>ic_others_9</th>
      <th>total_rech_num_6</th>
      <th>total_rech_num_7</th>
      <th>total_rech_num_8</th>
      <th>total_rech_num_9</th>
      <th>total_rech_amt_6</th>
      <th>total_rech_amt_7</th>
      <th>total_rech_amt_8</th>
      <th>total_rech_amt_9</th>
      <th>max_rech_amt_6</th>
      <th>max_rech_amt_7</th>
      <th>max_rech_amt_8</th>
      <th>max_rech_amt_9</th>
      <th>date_of_last_rech_6</th>
      <th>date_of_last_rech_7</th>
      <th>date_of_last_rech_8</th>
      <th>date_of_last_rech_9</th>
      <th>last_day_rch_amt_6</th>
      <th>last_day_rch_amt_7</th>
      <th>last_day_rch_amt_8</th>
      <th>last_day_rch_amt_9</th>
      <th>date_of_last_rech_data_6</th>
      <th>date_of_last_rech_data_7</th>
      <th>date_of_last_rech_data_8</th>
      <th>date_of_last_rech_data_9</th>
      <th>total_rech_data_6</th>
      <th>total_rech_data_7</th>
      <th>total_rech_data_8</th>
      <th>total_rech_data_9</th>
      <th>max_rech_data_6</th>
      <th>max_rech_data_7</th>
      <th>max_rech_data_8</th>
      <th>max_rech_data_9</th>
      <th>count_rech_2g_6</th>
      <th>count_rech_2g_7</th>
      <th>count_rech_2g_8</th>
      <th>count_rech_2g_9</th>
      <th>count_rech_3g_6</th>
      <th>count_rech_3g_7</th>
      <th>count_rech_3g_8</th>
      <th>count_rech_3g_9</th>
      <th>av_rech_amt_data_6</th>
      <th>av_rech_amt_data_7</th>
      <th>av_rech_amt_data_8</th>
      <th>av_rech_amt_data_9</th>
      <th>vol_2g_mb_6</th>
      <th>vol_2g_mb_7</th>
      <th>vol_2g_mb_8</th>
      <th>vol_2g_mb_9</th>
      <th>vol_3g_mb_6</th>
      <th>vol_3g_mb_7</th>
      <th>vol_3g_mb_8</th>
      <th>vol_3g_mb_9</th>
      <th>arpu_3g_6</th>
      <th>arpu_3g_7</th>
      <th>arpu_3g_8</th>
      <th>arpu_3g_9</th>
      <th>arpu_2g_6</th>
      <th>arpu_2g_7</th>
      <th>arpu_2g_8</th>
      <th>arpu_2g_9</th>
      <th>night_pck_user_6</th>
      <th>night_pck_user_7</th>
      <th>night_pck_user_8</th>
      <th>night_pck_user_9</th>
      <th>monthly_2g_6</th>
      <th>monthly_2g_7</th>
      <th>monthly_2g_8</th>
      <th>monthly_2g_9</th>
      <th>sachet_2g_6</th>
      <th>sachet_2g_7</th>
      <th>sachet_2g_8</th>
      <th>sachet_2g_9</th>
      <th>monthly_3g_6</th>
      <th>monthly_3g_7</th>
      <th>monthly_3g_8</th>
      <th>monthly_3g_9</th>
      <th>sachet_3g_6</th>
      <th>sachet_3g_7</th>
      <th>sachet_3g_8</th>
      <th>sachet_3g_9</th>
      <th>fb_user_6</th>
      <th>fb_user_7</th>
      <th>fb_user_8</th>
      <th>fb_user_9</th>
      <th>aon</th>
      <th>aug_vbc_3g</th>
      <th>jul_vbc_3g</th>
      <th>jun_vbc_3g</th>
      <th>sep_vbc_3g</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9.999900e+04</td>
      <td>99999.0</td>
      <td>98981.0</td>
      <td>98981.0</td>
      <td>98981.0</td>
      <td>99999</td>
      <td>99398</td>
      <td>98899</td>
      <td>98340</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.0</td>
      <td>96140.0</td>
      <td>94621.0</td>
      <td>92254.0</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.0</td>
      <td>96140.0</td>
      <td>94621.0</td>
      <td>92254.0</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>96062.000000</td>
      <td>96140.000000</td>
      <td>94621.000000</td>
      <td>92254.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>98392</td>
      <td>98232</td>
      <td>96377</td>
      <td>95239</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>25153</td>
      <td>25571</td>
      <td>26339</td>
      <td>25922</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.00000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
      <td>99999.000000</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30</td>
      <td>31</td>
      <td>31</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30</td>
      <td>31</td>
      <td>31</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>top</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/30/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/29/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6/30/2014</td>
      <td>7/31/2014</td>
      <td>8/31/2014</td>
      <td>9/29/2014</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>99999</td>
      <td>99398</td>
      <td>98899</td>
      <td>98340</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>16960</td>
      <td>17288</td>
      <td>14706</td>
      <td>22623</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1888</td>
      <td>1813</td>
      <td>1998</td>
      <td>2329</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>7.001207e+09</td>
      <td>109.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>282.987358</td>
      <td>278.536648</td>
      <td>279.154731</td>
      <td>261.645069</td>
      <td>132.395875</td>
      <td>133.670805</td>
      <td>133.018098</td>
      <td>130.302327</td>
      <td>197.935577</td>
      <td>197.045133</td>
      <td>196.574803</td>
      <td>190.337222</td>
      <td>9.950013</td>
      <td>7.149898</td>
      <td>7.292981</td>
      <td>6.343841</td>
      <td>13.911337</td>
      <td>9.818732</td>
      <td>9.971890</td>
      <td>8.555519</td>
      <td>47.100763</td>
      <td>46.473010</td>
      <td>45.887806</td>
      <td>44.584446</td>
      <td>93.342088</td>
      <td>91.397131</td>
      <td>91.755128</td>
      <td>90.463192</td>
      <td>3.751013</td>
      <td>3.792985</td>
      <td>3.677991</td>
      <td>3.655123</td>
      <td>1.123056</td>
      <td>1.368500</td>
      <td>1.433821</td>
      <td>1.232726</td>
      <td>144.201175</td>
      <td>141.670476</td>
      <td>141.328209</td>
      <td>138.709970</td>
      <td>79.829870</td>
      <td>83.299598</td>
      <td>83.282673</td>
      <td>82.342919</td>
      <td>87.299624</td>
      <td>90.804137</td>
      <td>89.838390</td>
      <td>86.276622</td>
      <td>1.129011</td>
      <td>1.115010</td>
      <td>1.067792</td>
      <td>1.042362</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>168.261218</td>
      <td>175.221436</td>
      <td>174.191498</td>
      <td>169.664466</td>
      <td>0.798277</td>
      <td>0.776572</td>
      <td>0.791247</td>
      <td>0.723892</td>
      <td>3.916811</td>
      <td>4.978279</td>
      <td>5.053769</td>
      <td>4.412767</td>
      <td>0.454157</td>
      <td>0.030235</td>
      <td>0.033372</td>
      <td>0.047456</td>
      <td>305.133424</td>
      <td>310.231175</td>
      <td>304.119513</td>
      <td>289.279198</td>
      <td>47.922365</td>
      <td>47.990520</td>
      <td>47.211362</td>
      <td>46.281794</td>
      <td>107.475650</td>
      <td>107.120493</td>
      <td>108.460515</td>
      <td>106.155471</td>
      <td>12.084305</td>
      <td>12.599697</td>
      <td>11.751834</td>
      <td>12.173105</td>
      <td>167.491059</td>
      <td>167.719540</td>
      <td>167.432575</td>
      <td>164.619293</td>
      <td>9.575993</td>
      <td>10.011904</td>
      <td>9.883921</td>
      <td>9.432479</td>
      <td>20.722240</td>
      <td>21.656415</td>
      <td>21.183211</td>
      <td>19.620913</td>
      <td>2.156397</td>
      <td>2.216923</td>
      <td>2.085004</td>
      <td>2.173419</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>32.457179</td>
      <td>33.887833</td>
      <td>33.154735</td>
      <td>31.229344</td>
      <td>200.130037</td>
      <td>202.853055</td>
      <td>198.750783</td>
      <td>189.214260</td>
      <td>0.061557</td>
      <td>0.033585</td>
      <td>0.040361</td>
      <td>0.163137</td>
      <td>7.460608</td>
      <td>8.334936</td>
      <td>8.442001</td>
      <td>8.063003</td>
      <td>0.854656</td>
      <td>1.012960</td>
      <td>0.970800</td>
      <td>1.017162</td>
      <td>7.558806</td>
      <td>7.700367</td>
      <td>7.212912</td>
      <td>6.893019</td>
      <td>327.514615</td>
      <td>322.962970</td>
      <td>324.157122</td>
      <td>303.345673</td>
      <td>104.637486</td>
      <td>104.752398</td>
      <td>107.728207</td>
      <td>101.943889</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>63.156252</td>
      <td>59.385804</td>
      <td>62.641716</td>
      <td>43.901249</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.463802</td>
      <td>2.666419</td>
      <td>2.651999</td>
      <td>2.441170</td>
      <td>126.393392</td>
      <td>126.729459</td>
      <td>125.717301</td>
      <td>124.94144</td>
      <td>1.864668</td>
      <td>2.044699</td>
      <td>2.016288</td>
      <td>1.781807</td>
      <td>0.599133</td>
      <td>0.621720</td>
      <td>0.635711</td>
      <td>0.659363</td>
      <td>192.600982</td>
      <td>200.981292</td>
      <td>197.526489</td>
      <td>192.734315</td>
      <td>51.904956</td>
      <td>51.229937</td>
      <td>50.170154</td>
      <td>44.719701</td>
      <td>121.396219</td>
      <td>128.995847</td>
      <td>135.410689</td>
      <td>136.056613</td>
      <td>89.555057</td>
      <td>89.384120</td>
      <td>91.173849</td>
      <td>100.264116</td>
      <td>86.398003</td>
      <td>85.914450</td>
      <td>86.599478</td>
      <td>93.712026</td>
      <td>0.025086</td>
      <td>0.023034</td>
      <td>0.020844</td>
      <td>0.015971</td>
      <td>0.079641</td>
      <td>0.083221</td>
      <td>0.081001</td>
      <td>0.068781</td>
      <td>0.389384</td>
      <td>0.439634</td>
      <td>0.450075</td>
      <td>0.393104</td>
      <td>0.075921</td>
      <td>0.078581</td>
      <td>0.082941</td>
      <td>0.086341</td>
      <td>0.074781</td>
      <td>0.080401</td>
      <td>0.084501</td>
      <td>0.084581</td>
      <td>0.914404</td>
      <td>0.908764</td>
      <td>0.890808</td>
      <td>0.860968</td>
      <td>1219.854749</td>
      <td>68.170248</td>
      <td>66.839062</td>
      <td>60.021204</td>
      <td>3.299373</td>
    </tr>
    <tr>
      <th>std</th>
      <td>6.956694e+05</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>328.439770</td>
      <td>338.156291</td>
      <td>344.474791</td>
      <td>341.998630</td>
      <td>297.207406</td>
      <td>308.794148</td>
      <td>308.951589</td>
      <td>308.477668</td>
      <td>316.851613</td>
      <td>325.862803</td>
      <td>327.170662</td>
      <td>319.396092</td>
      <td>72.825411</td>
      <td>73.447948</td>
      <td>68.402466</td>
      <td>57.137537</td>
      <td>71.443196</td>
      <td>58.455762</td>
      <td>64.713221</td>
      <td>58.438186</td>
      <td>150.856393</td>
      <td>155.318705</td>
      <td>151.184830</td>
      <td>147.995390</td>
      <td>162.780544</td>
      <td>157.492308</td>
      <td>156.537048</td>
      <td>158.681454</td>
      <td>14.230438</td>
      <td>14.264986</td>
      <td>13.270996</td>
      <td>13.457549</td>
      <td>5.448946</td>
      <td>7.533445</td>
      <td>6.783335</td>
      <td>5.619021</td>
      <td>251.751489</td>
      <td>248.731086</td>
      <td>245.914311</td>
      <td>245.934517</td>
      <td>252.476533</td>
      <td>263.631042</td>
      <td>265.486090</td>
      <td>267.184991</td>
      <td>255.617850</td>
      <td>269.347911</td>
      <td>271.757783</td>
      <td>261.407396</td>
      <td>7.984970</td>
      <td>8.599406</td>
      <td>7.905971</td>
      <td>8.261770</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>389.948499</td>
      <td>408.922934</td>
      <td>411.633049</td>
      <td>405.138658</td>
      <td>25.765248</td>
      <td>25.603052</td>
      <td>25.544471</td>
      <td>21.310751</td>
      <td>14.936449</td>
      <td>20.661570</td>
      <td>17.855111</td>
      <td>16.328227</td>
      <td>4.125911</td>
      <td>2.161717</td>
      <td>2.323464</td>
      <td>3.635466</td>
      <td>463.419481</td>
      <td>480.031178</td>
      <td>478.150031</td>
      <td>468.980002</td>
      <td>140.258485</td>
      <td>145.795055</td>
      <td>137.239552</td>
      <td>140.130610</td>
      <td>171.713903</td>
      <td>169.423620</td>
      <td>169.723759</td>
      <td>165.492803</td>
      <td>40.140895</td>
      <td>42.977442</td>
      <td>39.125379</td>
      <td>43.840776</td>
      <td>254.124029</td>
      <td>256.242707</td>
      <td>250.025523</td>
      <td>249.845070</td>
      <td>54.330607</td>
      <td>57.411971</td>
      <td>55.073186</td>
      <td>53.376273</td>
      <td>80.793414</td>
      <td>86.521393</td>
      <td>83.683565</td>
      <td>74.913050</td>
      <td>16.495594</td>
      <td>16.454061</td>
      <td>15.812580</td>
      <td>15.978601</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>106.283386</td>
      <td>113.720168</td>
      <td>110.127008</td>
      <td>101.982303</td>
      <td>291.651671</td>
      <td>298.124954</td>
      <td>289.321094</td>
      <td>284.823024</td>
      <td>0.160920</td>
      <td>0.155725</td>
      <td>0.146147</td>
      <td>0.527860</td>
      <td>59.722948</td>
      <td>65.219829</td>
      <td>63.813098</td>
      <td>63.505379</td>
      <td>11.955164</td>
      <td>12.673099</td>
      <td>13.284348</td>
      <td>12.381172</td>
      <td>7.078405</td>
      <td>7.070422</td>
      <td>7.203753</td>
      <td>7.096261</td>
      <td>398.019701</td>
      <td>408.114237</td>
      <td>416.540455</td>
      <td>404.588583</td>
      <td>120.614894</td>
      <td>124.523970</td>
      <td>126.902505</td>
      <td>125.375109</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>97.356649</td>
      <td>95.915385</td>
      <td>104.431816</td>
      <td>90.809712</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.789128</td>
      <td>3.031593</td>
      <td>3.074987</td>
      <td>2.516339</td>
      <td>108.477235</td>
      <td>109.765267</td>
      <td>109.437851</td>
      <td>111.36376</td>
      <td>2.570254</td>
      <td>2.768332</td>
      <td>2.720132</td>
      <td>2.214701</td>
      <td>1.274428</td>
      <td>1.394524</td>
      <td>1.422827</td>
      <td>1.411513</td>
      <td>192.646318</td>
      <td>196.791224</td>
      <td>191.301305</td>
      <td>188.400286</td>
      <td>213.356445</td>
      <td>212.302217</td>
      <td>212.347892</td>
      <td>198.653570</td>
      <td>544.247227</td>
      <td>541.494013</td>
      <td>558.775335</td>
      <td>577.394194</td>
      <td>193.124653</td>
      <td>195.893924</td>
      <td>188.180936</td>
      <td>216.291992</td>
      <td>172.767523</td>
      <td>176.379871</td>
      <td>168.247852</td>
      <td>171.384224</td>
      <td>0.156391</td>
      <td>0.150014</td>
      <td>0.142863</td>
      <td>0.125366</td>
      <td>0.295058</td>
      <td>0.304395</td>
      <td>0.299568</td>
      <td>0.278120</td>
      <td>1.497320</td>
      <td>1.636230</td>
      <td>1.630263</td>
      <td>1.347140</td>
      <td>0.363371</td>
      <td>0.387231</td>
      <td>0.384947</td>
      <td>0.384978</td>
      <td>0.568344</td>
      <td>0.628334</td>
      <td>0.660234</td>
      <td>0.650457</td>
      <td>0.279772</td>
      <td>0.287950</td>
      <td>0.311885</td>
      <td>0.345987</td>
      <td>954.733842</td>
      <td>267.580450</td>
      <td>271.201856</td>
      <td>253.938223</td>
      <td>32.408353</td>
    </tr>
    <tr>
      <th>min</th>
      <td>7.000000e+09</td>
      <td>109.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-2258.709000</td>
      <td>-2014.045000</td>
      <td>-945.808000</td>
      <td>-1899.505000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.00000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.500000</td>
      <td>0.500000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-30.820000</td>
      <td>-26.040000</td>
      <td>-24.490000</td>
      <td>-71.090000</td>
      <td>-35.830000</td>
      <td>-15.480000</td>
      <td>-55.830000</td>
      <td>-45.740000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>180.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>7.000606e+09</td>
      <td>109.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>93.411500</td>
      <td>86.980500</td>
      <td>84.126000</td>
      <td>62.685000</td>
      <td>7.380000</td>
      <td>6.660000</td>
      <td>6.460000</td>
      <td>5.330000</td>
      <td>34.730000</td>
      <td>32.190000</td>
      <td>31.630000</td>
      <td>27.130000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.660000</td>
      <td>1.630000</td>
      <td>1.600000</td>
      <td>1.360000</td>
      <td>9.880000</td>
      <td>10.025000</td>
      <td>9.810000</td>
      <td>8.810000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>17.110000</td>
      <td>17.480000</td>
      <td>17.110000</td>
      <td>15.560000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>44.740000</td>
      <td>43.010000</td>
      <td>38.580000</td>
      <td>25.510000</td>
      <td>2.990000</td>
      <td>3.230000</td>
      <td>3.280000</td>
      <td>3.290000</td>
      <td>17.290000</td>
      <td>18.590000</td>
      <td>18.930000</td>
      <td>18.560000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>30.390000</td>
      <td>32.460000</td>
      <td>32.740000</td>
      <td>32.290000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.010000</td>
      <td>0.000000</td>
      <td>38.530000</td>
      <td>41.190000</td>
      <td>38.290000</td>
      <td>32.370000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>109.000000</td>
      <td>100.000000</td>
      <td>90.000000</td>
      <td>52.000000</td>
      <td>30.000000</td>
      <td>30.000000</td>
      <td>30.000000</td>
      <td>28.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>25.000000</td>
      <td>25.000000</td>
      <td>25.000000</td>
      <td>25.00000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>82.000000</td>
      <td>92.000000</td>
      <td>87.000000</td>
      <td>69.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>467.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>7.001205e+09</td>
      <td>109.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>197.704000</td>
      <td>191.640000</td>
      <td>192.080000</td>
      <td>176.849000</td>
      <td>34.310000</td>
      <td>32.330000</td>
      <td>32.360000</td>
      <td>29.840000</td>
      <td>96.310000</td>
      <td>91.735000</td>
      <td>92.140000</td>
      <td>87.290000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>11.910000</td>
      <td>11.610000</td>
      <td>11.730000</td>
      <td>11.260000</td>
      <td>41.030000</td>
      <td>40.430000</td>
      <td>40.360000</td>
      <td>39.120000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>65.110000</td>
      <td>63.685000</td>
      <td>63.730000</td>
      <td>61.840000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>3.950000</td>
      <td>3.635000</td>
      <td>3.310000</td>
      <td>2.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>11.640000</td>
      <td>11.090000</td>
      <td>10.410000</td>
      <td>8.410000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>145.140000</td>
      <td>141.530000</td>
      <td>138.610000</td>
      <td>125.460000</td>
      <td>15.690000</td>
      <td>15.740000</td>
      <td>16.030000</td>
      <td>15.660000</td>
      <td>56.490000</td>
      <td>57.080000</td>
      <td>58.240000</td>
      <td>56.610000</td>
      <td>0.880000</td>
      <td>0.930000</td>
      <td>0.930000</td>
      <td>0.960000</td>
      <td>92.160000</td>
      <td>92.550000</td>
      <td>93.830000</td>
      <td>91.640000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.030000</td>
      <td>2.040000</td>
      <td>2.030000</td>
      <td>1.740000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.890000</td>
      <td>5.960000</td>
      <td>5.880000</td>
      <td>5.380000</td>
      <td>114.740000</td>
      <td>116.340000</td>
      <td>114.660000</td>
      <td>105.890000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>5.000000</td>
      <td>5.000000</td>
      <td>230.000000</td>
      <td>220.000000</td>
      <td>225.000000</td>
      <td>200.000000</td>
      <td>110.000000</td>
      <td>110.000000</td>
      <td>98.000000</td>
      <td>61.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30.000000</td>
      <td>30.000000</td>
      <td>30.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>145.000000</td>
      <td>145.000000</td>
      <td>145.000000</td>
      <td>145.00000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>154.000000</td>
      <td>154.000000</td>
      <td>154.000000</td>
      <td>164.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.480000</td>
      <td>0.420000</td>
      <td>0.880000</td>
      <td>2.605000</td>
      <td>10.830000</td>
      <td>8.810000</td>
      <td>9.270000</td>
      <td>14.800000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>863.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7.001812e+09</td>
      <td>109.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>371.060000</td>
      <td>365.344500</td>
      <td>369.370500</td>
      <td>353.466500</td>
      <td>118.740000</td>
      <td>115.595000</td>
      <td>115.860000</td>
      <td>112.130000</td>
      <td>231.860000</td>
      <td>226.815000</td>
      <td>228.260000</td>
      <td>220.505000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>40.960000</td>
      <td>39.910000</td>
      <td>40.110000</td>
      <td>39.280000</td>
      <td>110.390000</td>
      <td>107.560000</td>
      <td>109.090000</td>
      <td>106.810000</td>
      <td>2.080000</td>
      <td>2.090000</td>
      <td>2.040000</td>
      <td>1.940000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>168.270000</td>
      <td>164.382500</td>
      <td>166.110000</td>
      <td>162.225000</td>
      <td>30.807500</td>
      <td>31.132500</td>
      <td>30.580000</td>
      <td>28.230000</td>
      <td>53.290000</td>
      <td>54.040000</td>
      <td>52.490000</td>
      <td>48.560000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>144.837500</td>
      <td>150.615000</td>
      <td>147.940000</td>
      <td>142.105000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.430000</td>
      <td>3.710000</td>
      <td>3.990000</td>
      <td>3.230000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>372.860000</td>
      <td>378.570000</td>
      <td>369.900000</td>
      <td>353.480000</td>
      <td>46.840000</td>
      <td>45.810000</td>
      <td>46.290000</td>
      <td>45.180000</td>
      <td>132.387500</td>
      <td>130.960000</td>
      <td>133.930000</td>
      <td>130.490000</td>
      <td>8.140000</td>
      <td>8.282500</td>
      <td>8.110000</td>
      <td>8.140000</td>
      <td>208.075000</td>
      <td>205.837500</td>
      <td>207.280000</td>
      <td>202.737500</td>
      <td>4.060000</td>
      <td>4.230000</td>
      <td>4.080000</td>
      <td>3.510000</td>
      <td>15.030000</td>
      <td>15.740000</td>
      <td>15.360000</td>
      <td>14.260000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>26.930000</td>
      <td>28.310000</td>
      <td>27.710000</td>
      <td>25.690000</td>
      <td>251.670000</td>
      <td>250.660000</td>
      <td>248.990000</td>
      <td>236.320000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.060000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>9.000000</td>
      <td>10.000000</td>
      <td>9.000000</td>
      <td>9.000000</td>
      <td>437.500000</td>
      <td>428.000000</td>
      <td>434.500000</td>
      <td>415.000000</td>
      <td>120.000000</td>
      <td>128.000000</td>
      <td>144.000000</td>
      <td>144.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>110.000000</td>
      <td>110.000000</td>
      <td>130.000000</td>
      <td>50.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>177.000000</td>
      <td>177.000000</td>
      <td>179.000000</td>
      <td>179.00000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>252.000000</td>
      <td>252.000000</td>
      <td>252.000000</td>
      <td>252.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>122.070000</td>
      <td>119.560000</td>
      <td>122.070000</td>
      <td>140.010000</td>
      <td>122.070000</td>
      <td>122.070000</td>
      <td>122.070000</td>
      <td>140.010000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1807.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>7.002411e+09</td>
      <td>109.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>27731.088000</td>
      <td>35145.834000</td>
      <td>33543.624000</td>
      <td>38805.617000</td>
      <td>7376.710000</td>
      <td>8157.780000</td>
      <td>10752.560000</td>
      <td>10427.460000</td>
      <td>8362.360000</td>
      <td>9667.130000</td>
      <td>14007.340000</td>
      <td>10310.760000</td>
      <td>13724.380000</td>
      <td>15371.040000</td>
      <td>13095.360000</td>
      <td>8464.030000</td>
      <td>3775.110000</td>
      <td>2812.040000</td>
      <td>5337.040000</td>
      <td>4428.460000</td>
      <td>6431.330000</td>
      <td>7400.660000</td>
      <td>10752.560000</td>
      <td>10389.240000</td>
      <td>4729.740000</td>
      <td>4557.140000</td>
      <td>4961.330000</td>
      <td>4429.880000</td>
      <td>1466.030000</td>
      <td>1196.430000</td>
      <td>928.490000</td>
      <td>927.410000</td>
      <td>342.860000</td>
      <td>916.240000</td>
      <td>502.090000</td>
      <td>339.840000</td>
      <td>10643.380000</td>
      <td>7674.780000</td>
      <td>11039.910000</td>
      <td>11099.260000</td>
      <td>7366.580000</td>
      <td>8133.660000</td>
      <td>8014.430000</td>
      <td>9382.580000</td>
      <td>8314.760000</td>
      <td>9284.740000</td>
      <td>13950.040000</td>
      <td>10223.430000</td>
      <td>628.560000</td>
      <td>544.630000</td>
      <td>516.910000</td>
      <td>808.490000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8432.990000</td>
      <td>10936.730000</td>
      <td>13980.060000</td>
      <td>11495.310000</td>
      <td>5900.660000</td>
      <td>5490.280000</td>
      <td>5681.540000</td>
      <td>4244.530000</td>
      <td>1023.210000</td>
      <td>2372.510000</td>
      <td>1390.880000</td>
      <td>1635.710000</td>
      <td>800.890000</td>
      <td>370.130000</td>
      <td>394.930000</td>
      <td>787.790000</td>
      <td>10674.030000</td>
      <td>11365.310000</td>
      <td>14043.060000</td>
      <td>11517.730000</td>
      <td>6626.930000</td>
      <td>9324.660000</td>
      <td>10696.230000</td>
      <td>10598.830000</td>
      <td>4693.860000</td>
      <td>4455.830000</td>
      <td>6274.190000</td>
      <td>5463.780000</td>
      <td>1872.340000</td>
      <td>1983.010000</td>
      <td>2433.060000</td>
      <td>4318.280000</td>
      <td>7454.630000</td>
      <td>9669.910000</td>
      <td>10830.160000</td>
      <td>10796.290000</td>
      <td>5459.560000</td>
      <td>5800.930000</td>
      <td>4309.290000</td>
      <td>3819.830000</td>
      <td>5647.160000</td>
      <td>6141.880000</td>
      <td>5645.860000</td>
      <td>5689.760000</td>
      <td>1351.110000</td>
      <td>1136.080000</td>
      <td>1394.890000</td>
      <td>1431.960000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5712.110000</td>
      <td>6745.760000</td>
      <td>5957.140000</td>
      <td>5956.660000</td>
      <td>7716.140000</td>
      <td>9699.010000</td>
      <td>10830.380000</td>
      <td>10796.590000</td>
      <td>19.760000</td>
      <td>21.330000</td>
      <td>16.860000</td>
      <td>62.380000</td>
      <td>6789.410000</td>
      <td>5289.540000</td>
      <td>4127.010000</td>
      <td>5057.740000</td>
      <td>1362.940000</td>
      <td>1495.940000</td>
      <td>2327.510000</td>
      <td>1005.230000</td>
      <td>307.000000</td>
      <td>138.000000</td>
      <td>196.000000</td>
      <td>131.000000</td>
      <td>35190.000000</td>
      <td>40335.000000</td>
      <td>45320.000000</td>
      <td>37235.000000</td>
      <td>4010.000000</td>
      <td>4010.000000</td>
      <td>4449.000000</td>
      <td>3399.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4010.000000</td>
      <td>4010.000000</td>
      <td>4449.000000</td>
      <td>3399.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>61.000000</td>
      <td>54.000000</td>
      <td>60.000000</td>
      <td>84.000000</td>
      <td>1555.000000</td>
      <td>1555.000000</td>
      <td>1555.000000</td>
      <td>1555.00000</td>
      <td>42.000000</td>
      <td>48.000000</td>
      <td>44.000000</td>
      <td>40.000000</td>
      <td>29.000000</td>
      <td>35.000000</td>
      <td>45.000000</td>
      <td>49.000000</td>
      <td>7546.000000</td>
      <td>4365.000000</td>
      <td>4076.000000</td>
      <td>4061.000000</td>
      <td>10285.900000</td>
      <td>7873.550000</td>
      <td>11117.610000</td>
      <td>8993.950000</td>
      <td>45735.400000</td>
      <td>28144.120000</td>
      <td>30036.060000</td>
      <td>39221.270000</td>
      <td>6362.280000</td>
      <td>4980.900000</td>
      <td>3716.900000</td>
      <td>13884.310000</td>
      <td>6433.760000</td>
      <td>4809.360000</td>
      <td>3483.170000</td>
      <td>3467.170000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>4.000000</td>
      <td>5.000000</td>
      <td>5.000000</td>
      <td>4.000000</td>
      <td>42.000000</td>
      <td>48.000000</td>
      <td>44.000000</td>
      <td>40.000000</td>
      <td>14.000000</td>
      <td>16.000000</td>
      <td>16.000000</td>
      <td>11.000000</td>
      <td>29.000000</td>
      <td>35.000000</td>
      <td>41.000000</td>
      <td>49.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>4337.000000</td>
      <td>12916.220000</td>
      <td>9165.600000</td>
      <td>11166.210000</td>
      <td>2618.570000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# create backup of data
original = churn.copy()
```


```python
# create column name list by types of columns
id_cols = ['mobile_number', 'circle_id']

date_cols = ['last_date_of_month_6',
             'last_date_of_month_7',
             'last_date_of_month_8',
             'last_date_of_month_9',
             'date_of_last_rech_6',
             'date_of_last_rech_7',
             'date_of_last_rech_8',
             'date_of_last_rech_9',
             'date_of_last_rech_data_6',
             'date_of_last_rech_data_7',
             'date_of_last_rech_data_8',
             'date_of_last_rech_data_9'
            ]

cat_cols =  ['night_pck_user_6',
             'night_pck_user_7',
             'night_pck_user_8',
             'night_pck_user_9',
             'fb_user_6',
             'fb_user_7',
             'fb_user_8',
             'fb_user_9'
            ]

num_cols = [column for column in churn.columns if column not in id_cols + date_cols + cat_cols]

# print the number of columns in each list
print("#ID cols: %d\n#Date cols:%d\n#Numeric cols:%d\n#Category cols:%d" % (len(id_cols), len(date_cols), len(num_cols), len(cat_cols)))

# check if we have missed any column or not
print(len(id_cols) + len(date_cols) + len(num_cols) + len(cat_cols) == churn.shape[1])
```

    #ID cols: 2
    #Date cols:12
    #Numeric cols:204
    #Category cols:8
    True


# Handling missing values


```python
# look at missing value ratio in each column
churn.isnull().sum()*100/churn.shape[0]
```




    mobile_number                0.000000
    circle_id                    0.000000
    loc_og_t2o_mou               1.018010
    std_og_t2o_mou               1.018010
    loc_ic_t2o_mou               1.018010
    last_date_of_month_6         0.000000
    last_date_of_month_7         0.601006
    last_date_of_month_8         1.100011
    last_date_of_month_9         1.659017
    arpu_6                       0.000000
    arpu_7                       0.000000
    arpu_8                       0.000000
    arpu_9                       0.000000
    onnet_mou_6                  3.937039
    onnet_mou_7                  3.859039
    onnet_mou_8                  5.378054
    onnet_mou_9                  7.745077
    offnet_mou_6                 3.937039
    offnet_mou_7                 3.859039
    offnet_mou_8                 5.378054
    offnet_mou_9                 7.745077
    roam_ic_mou_6                3.937039
    roam_ic_mou_7                3.859039
    roam_ic_mou_8                5.378054
    roam_ic_mou_9                7.745077
    roam_og_mou_6                3.937039
    roam_og_mou_7                3.859039
    roam_og_mou_8                5.378054
    roam_og_mou_9                7.745077
    loc_og_t2t_mou_6             3.937039
    loc_og_t2t_mou_7             3.859039
    loc_og_t2t_mou_8             5.378054
    loc_og_t2t_mou_9             7.745077
    loc_og_t2m_mou_6             3.937039
    loc_og_t2m_mou_7             3.859039
    loc_og_t2m_mou_8             5.378054
    loc_og_t2m_mou_9             7.745077
    loc_og_t2f_mou_6             3.937039
    loc_og_t2f_mou_7             3.859039
    loc_og_t2f_mou_8             5.378054
    loc_og_t2f_mou_9             7.745077
    loc_og_t2c_mou_6             3.937039
    loc_og_t2c_mou_7             3.859039
    loc_og_t2c_mou_8             5.378054
    loc_og_t2c_mou_9             7.745077
    loc_og_mou_6                 3.937039
    loc_og_mou_7                 3.859039
    loc_og_mou_8                 5.378054
    loc_og_mou_9                 7.745077
    std_og_t2t_mou_6             3.937039
    std_og_t2t_mou_7             3.859039
    std_og_t2t_mou_8             5.378054
    std_og_t2t_mou_9             7.745077
    std_og_t2m_mou_6             3.937039
    std_og_t2m_mou_7             3.859039
    std_og_t2m_mou_8             5.378054
    std_og_t2m_mou_9             7.745077
    std_og_t2f_mou_6             3.937039
    std_og_t2f_mou_7             3.859039
    std_og_t2f_mou_8             5.378054
    std_og_t2f_mou_9             7.745077
    std_og_t2c_mou_6             3.937039
    std_og_t2c_mou_7             3.859039
    std_og_t2c_mou_8             5.378054
    std_og_t2c_mou_9             7.745077
    std_og_mou_6                 3.937039
    std_og_mou_7                 3.859039
    std_og_mou_8                 5.378054
    std_og_mou_9                 7.745077
    isd_og_mou_6                 3.937039
    isd_og_mou_7                 3.859039
    isd_og_mou_8                 5.378054
    isd_og_mou_9                 7.745077
    spl_og_mou_6                 3.937039
    spl_og_mou_7                 3.859039
    spl_og_mou_8                 5.378054
    spl_og_mou_9                 7.745077
    og_others_6                  3.937039
    og_others_7                  3.859039
    og_others_8                  5.378054
    og_others_9                  7.745077
    total_og_mou_6               0.000000
    total_og_mou_7               0.000000
    total_og_mou_8               0.000000
    total_og_mou_9               0.000000
    loc_ic_t2t_mou_6             3.937039
    loc_ic_t2t_mou_7             3.859039
    loc_ic_t2t_mou_8             5.378054
    loc_ic_t2t_mou_9             7.745077
    loc_ic_t2m_mou_6             3.937039
    loc_ic_t2m_mou_7             3.859039
    loc_ic_t2m_mou_8             5.378054
    loc_ic_t2m_mou_9             7.745077
    loc_ic_t2f_mou_6             3.937039
    loc_ic_t2f_mou_7             3.859039
    loc_ic_t2f_mou_8             5.378054
    loc_ic_t2f_mou_9             7.745077
    loc_ic_mou_6                 3.937039
    loc_ic_mou_7                 3.859039
    loc_ic_mou_8                 5.378054
    loc_ic_mou_9                 7.745077
    std_ic_t2t_mou_6             3.937039
    std_ic_t2t_mou_7             3.859039
    std_ic_t2t_mou_8             5.378054
    std_ic_t2t_mou_9             7.745077
    std_ic_t2m_mou_6             3.937039
    std_ic_t2m_mou_7             3.859039
    std_ic_t2m_mou_8             5.378054
    std_ic_t2m_mou_9             7.745077
    std_ic_t2f_mou_6             3.937039
    std_ic_t2f_mou_7             3.859039
    std_ic_t2f_mou_8             5.378054
    std_ic_t2f_mou_9             7.745077
    std_ic_t2o_mou_6             3.937039
    std_ic_t2o_mou_7             3.859039
    std_ic_t2o_mou_8             5.378054
    std_ic_t2o_mou_9             7.745077
    std_ic_mou_6                 3.937039
    std_ic_mou_7                 3.859039
    std_ic_mou_8                 5.378054
    std_ic_mou_9                 7.745077
    total_ic_mou_6               0.000000
    total_ic_mou_7               0.000000
    total_ic_mou_8               0.000000
    total_ic_mou_9               0.000000
    spl_ic_mou_6                 3.937039
    spl_ic_mou_7                 3.859039
    spl_ic_mou_8                 5.378054
    spl_ic_mou_9                 7.745077
    isd_ic_mou_6                 3.937039
    isd_ic_mou_7                 3.859039
    isd_ic_mou_8                 5.378054
    isd_ic_mou_9                 7.745077
    ic_others_6                  3.937039
    ic_others_7                  3.859039
    ic_others_8                  5.378054
    ic_others_9                  7.745077
    total_rech_num_6             0.000000
    total_rech_num_7             0.000000
    total_rech_num_8             0.000000
    total_rech_num_9             0.000000
    total_rech_amt_6             0.000000
    total_rech_amt_7             0.000000
    total_rech_amt_8             0.000000
    total_rech_amt_9             0.000000
    max_rech_amt_6               0.000000
    max_rech_amt_7               0.000000
    max_rech_amt_8               0.000000
    max_rech_amt_9               0.000000
    date_of_last_rech_6          1.607016
    date_of_last_rech_7          1.767018
    date_of_last_rech_8          3.622036
    date_of_last_rech_9          4.760048
    last_day_rch_amt_6           0.000000
    last_day_rch_amt_7           0.000000
    last_day_rch_amt_8           0.000000
    last_day_rch_amt_9           0.000000
    date_of_last_rech_data_6    74.846748
    date_of_last_rech_data_7    74.428744
    date_of_last_rech_data_8    73.660737
    date_of_last_rech_data_9    74.077741
    total_rech_data_6           74.846748
    total_rech_data_7           74.428744
    total_rech_data_8           73.660737
    total_rech_data_9           74.077741
    max_rech_data_6             74.846748
    max_rech_data_7             74.428744
    max_rech_data_8             73.660737
    max_rech_data_9             74.077741
    count_rech_2g_6             74.846748
    count_rech_2g_7             74.428744
    count_rech_2g_8             73.660737
    count_rech_2g_9             74.077741
    count_rech_3g_6             74.846748
    count_rech_3g_7             74.428744
    count_rech_3g_8             73.660737
    count_rech_3g_9             74.077741
    av_rech_amt_data_6          74.846748
    av_rech_amt_data_7          74.428744
    av_rech_amt_data_8          73.660737
    av_rech_amt_data_9          74.077741
    vol_2g_mb_6                  0.000000
    vol_2g_mb_7                  0.000000
    vol_2g_mb_8                  0.000000
    vol_2g_mb_9                  0.000000
    vol_3g_mb_6                  0.000000
    vol_3g_mb_7                  0.000000
    vol_3g_mb_8                  0.000000
    vol_3g_mb_9                  0.000000
    arpu_3g_6                   74.846748
    arpu_3g_7                   74.428744
    arpu_3g_8                   73.660737
    arpu_3g_9                   74.077741
    arpu_2g_6                   74.846748
    arpu_2g_7                   74.428744
    arpu_2g_8                   73.660737
    arpu_2g_9                   74.077741
    night_pck_user_6            74.846748
    night_pck_user_7            74.428744
    night_pck_user_8            73.660737
    night_pck_user_9            74.077741
    monthly_2g_6                 0.000000
    monthly_2g_7                 0.000000
    monthly_2g_8                 0.000000
    monthly_2g_9                 0.000000
    sachet_2g_6                  0.000000
    sachet_2g_7                  0.000000
    sachet_2g_8                  0.000000
    sachet_2g_9                  0.000000
    monthly_3g_6                 0.000000
    monthly_3g_7                 0.000000
    monthly_3g_8                 0.000000
    monthly_3g_9                 0.000000
    sachet_3g_6                  0.000000
    sachet_3g_7                  0.000000
    sachet_3g_8                  0.000000
    sachet_3g_9                  0.000000
    fb_user_6                   74.846748
    fb_user_7                   74.428744
    fb_user_8                   73.660737
    fb_user_9                   74.077741
    aon                          0.000000
    aug_vbc_3g                   0.000000
    jul_vbc_3g                   0.000000
    jun_vbc_3g                   0.000000
    sep_vbc_3g                   0.000000
    dtype: float64



# impute missing values

## i) Imputing with zeroes


```python
# some recharge columns have minimum value of 1 while some don't
recharge_cols = ['total_rech_data_6', 'total_rech_data_7', 'total_rech_data_8', 'total_rech_data_9',
                 'count_rech_2g_6', 'count_rech_2g_7', 'count_rech_2g_8', 'count_rech_2g_9',
                 'count_rech_3g_6', 'count_rech_3g_7', 'count_rech_3g_8', 'count_rech_3g_9',
                 'max_rech_data_6', 'max_rech_data_7', 'max_rech_data_8', 'max_rech_data_9',
                 'av_rech_amt_data_6', 'av_rech_amt_data_7', 'av_rech_amt_data_8', 'av_rech_amt_data_9',
                 ]

churn[recharge_cols].describe(include='all')
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
      <th>total_rech_data_6</th>
      <th>total_rech_data_7</th>
      <th>total_rech_data_8</th>
      <th>total_rech_data_9</th>
      <th>count_rech_2g_6</th>
      <th>count_rech_2g_7</th>
      <th>count_rech_2g_8</th>
      <th>count_rech_2g_9</th>
      <th>count_rech_3g_6</th>
      <th>count_rech_3g_7</th>
      <th>count_rech_3g_8</th>
      <th>count_rech_3g_9</th>
      <th>max_rech_data_6</th>
      <th>max_rech_data_7</th>
      <th>max_rech_data_8</th>
      <th>max_rech_data_9</th>
      <th>av_rech_amt_data_6</th>
      <th>av_rech_amt_data_7</th>
      <th>av_rech_amt_data_8</th>
      <th>av_rech_amt_data_9</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.00000</td>
      <td>25153.000000</td>
      <td>25571.000000</td>
      <td>26339.000000</td>
      <td>25922.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2.463802</td>
      <td>2.666419</td>
      <td>2.651999</td>
      <td>2.441170</td>
      <td>1.864668</td>
      <td>2.044699</td>
      <td>2.016288</td>
      <td>1.781807</td>
      <td>0.599133</td>
      <td>0.621720</td>
      <td>0.635711</td>
      <td>0.659363</td>
      <td>126.393392</td>
      <td>126.729459</td>
      <td>125.717301</td>
      <td>124.94144</td>
      <td>192.600982</td>
      <td>200.981292</td>
      <td>197.526489</td>
      <td>192.734315</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2.789128</td>
      <td>3.031593</td>
      <td>3.074987</td>
      <td>2.516339</td>
      <td>2.570254</td>
      <td>2.768332</td>
      <td>2.720132</td>
      <td>2.214701</td>
      <td>1.274428</td>
      <td>1.394524</td>
      <td>1.422827</td>
      <td>1.411513</td>
      <td>108.477235</td>
      <td>109.765267</td>
      <td>109.437851</td>
      <td>111.36376</td>
      <td>192.646318</td>
      <td>196.791224</td>
      <td>191.301305</td>
      <td>188.400286</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.00000</td>
      <td>1.000000</td>
      <td>0.500000</td>
      <td>0.500000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>25.000000</td>
      <td>25.000000</td>
      <td>25.000000</td>
      <td>25.00000</td>
      <td>82.000000</td>
      <td>92.000000</td>
      <td>87.000000</td>
      <td>69.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>145.000000</td>
      <td>145.000000</td>
      <td>145.000000</td>
      <td>145.00000</td>
      <td>154.000000</td>
      <td>154.000000</td>
      <td>154.000000</td>
      <td>164.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>177.000000</td>
      <td>177.000000</td>
      <td>179.000000</td>
      <td>179.00000</td>
      <td>252.000000</td>
      <td>252.000000</td>
      <td>252.000000</td>
      <td>252.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>61.000000</td>
      <td>54.000000</td>
      <td>60.000000</td>
      <td>84.000000</td>
      <td>42.000000</td>
      <td>48.000000</td>
      <td>44.000000</td>
      <td>40.000000</td>
      <td>29.000000</td>
      <td>35.000000</td>
      <td>45.000000</td>
      <td>49.000000</td>
      <td>1555.000000</td>
      <td>1555.000000</td>
      <td>1555.000000</td>
      <td>1555.00000</td>
      <td>7546.000000</td>
      <td>4365.000000</td>
      <td>4076.000000</td>
      <td>4061.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# It is also observed that the recharge date and the recharge value are missing together which means the customer didn't recharge
churn.loc[churn.total_rech_data_6.isnull() & churn.date_of_last_rech_data_6.isnull(), ["total_rech_data_6", "date_of_last_rech_data_6"]].head(20)
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
      <th>total_rech_data_6</th>
      <th>date_of_last_rech_data_6</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>10</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>12</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>21</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



In the recharge variables where minumum value is 1, we can impute missing values with zeroes since it means customer didn't recharge their numbere that month.


```python
# create a list of recharge columns where we will impute missing values with zeroes
zero_impute = ['total_rech_data_6', 'total_rech_data_7', 'total_rech_data_8', 'total_rech_data_9',
        'av_rech_amt_data_6', 'av_rech_amt_data_7', 'av_rech_amt_data_8', 'av_rech_amt_data_9',
        'max_rech_data_6', 'max_rech_data_7', 'max_rech_data_8', 'max_rech_data_9'
       ]
```


```python
# impute missing values with 0
churn[zero_impute] = churn[zero_impute].apply(lambda x: x.fillna(0))
```


```python
# now, let's make sure values are imputed correctly
print("Missing value ratio:\n")
print(churn[zero_impute].isnull().sum()*100/churn.shape[1])

# summary
print("\n\nSummary statistics\n")
print(churn[zero_impute].describe(include='all'))
```

    Missing value ratio:
    
    total_rech_data_6     0.0
    total_rech_data_7     0.0
    total_rech_data_8     0.0
    total_rech_data_9     0.0
    av_rech_amt_data_6    0.0
    av_rech_amt_data_7    0.0
    av_rech_amt_data_8    0.0
    av_rech_amt_data_9    0.0
    max_rech_data_6       0.0
    max_rech_data_7       0.0
    max_rech_data_8       0.0
    max_rech_data_9       0.0
    dtype: float64
    
    
    Summary statistics
    
           total_rech_data_6  total_rech_data_7  total_rech_data_8  \
    count       99999.000000       99999.000000       99999.000000   
    mean            0.619726           0.681837           0.698517   
    std             1.760541           1.924382           1.963417   
    min             0.000000           0.000000           0.000000   
    25%             0.000000           0.000000           0.000000   
    50%             0.000000           0.000000           0.000000   
    75%             1.000000           1.000000           1.000000   
    max            61.000000          54.000000          60.000000   
    
           total_rech_data_9  av_rech_amt_data_6  av_rech_amt_data_7  \
    count       99999.000000        99999.000000        99999.000000   
    mean            0.632806           48.445409           51.393440   
    std             1.669040          127.743863          132.629365   
    min             0.000000            0.000000            0.000000   
    25%             0.000000            0.000000            0.000000   
    50%             0.000000            0.000000            0.000000   
    75%             1.000000            8.250000           17.000000   
    max            84.000000         7546.000000         4365.000000   
    
           av_rech_amt_data_8  av_rech_amt_data_9  max_rech_data_6  \
    count        99999.000000        99999.000000     99999.000000   
    mean            52.027022           49.961089        31.792048   
    std            131.182609          127.804280        77.248778   
    min              0.000000            0.000000         0.000000   
    25%              0.000000            0.000000         0.000000   
    50%              0.000000            0.000000         0.000000   
    75%             23.000000           17.000000         8.000000   
    max           4076.000000         4061.000000      1555.000000   
    
           max_rech_data_7  max_rech_data_8  max_rech_data_9  
    count     99999.000000     99999.000000     99999.000000  
    mean         32.406314        33.113011        32.387644  
    std          78.342435        78.872739        78.818696  
    min           0.000000         0.000000         0.000000  
    25%           0.000000         0.000000         0.000000  
    50%           0.000000         0.000000         0.000000  
    75%          14.000000        17.000000        17.000000  
    max        1555.000000      1555.000000      1555.000000  



```python
# drop id and date columns
print("Shape before dropping: ", churn.shape)
churn = churn.drop(id_cols + date_cols, axis=1)
print("Shape after dropping: ", churn.shape)
```

    Shape before dropping:  (99999, 226)
    Shape after dropping:  (99999, 212)


## ii) Replace NaN values in categorical variables

We will replace missing values in the categorical values with '-1' where '-1' will be a new category.


```python
# replace missing values with '-1' in categorical columns
churn[cat_cols] = churn[cat_cols].apply(lambda x: x.fillna(-1))
```


```python
# missing value ratio
print("Missing value ratio:\n")
print(churn[cat_cols].isnull().sum()*100/churn.shape[0])
```

    Missing value ratio:
    
    night_pck_user_6    0.0
    night_pck_user_7    0.0
    night_pck_user_8    0.0
    night_pck_user_9    0.0
    fb_user_6           0.0
    fb_user_7           0.0
    fb_user_8           0.0
    fb_user_9           0.0
    dtype: float64


## iii) Drop variables with more than a given threshold of missing values


```python
initial_cols = churn.shape[1]

MISSING_THRESHOLD = 0.7

include_cols = list(churn.apply(lambda column: True if column.isnull().sum()/churn.shape[0] < MISSING_THRESHOLD else False))

drop_missing = pd.DataFrame({'features':churn.columns , 'include': include_cols})
drop_missing.loc[drop_missing.include == True,:]
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
      <th>features</th>
      <th>include</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>loc_og_t2o_mou</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>std_og_t2o_mou</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>loc_ic_t2o_mou</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>arpu_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>arpu_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>arpu_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>arpu_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>onnet_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>8</th>
      <td>onnet_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>9</th>
      <td>onnet_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>10</th>
      <td>onnet_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>11</th>
      <td>offnet_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>12</th>
      <td>offnet_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>13</th>
      <td>offnet_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>14</th>
      <td>offnet_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>15</th>
      <td>roam_ic_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>16</th>
      <td>roam_ic_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>17</th>
      <td>roam_ic_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>18</th>
      <td>roam_ic_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>19</th>
      <td>roam_og_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>20</th>
      <td>roam_og_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>21</th>
      <td>roam_og_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>22</th>
      <td>roam_og_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>23</th>
      <td>loc_og_t2t_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>24</th>
      <td>loc_og_t2t_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>25</th>
      <td>loc_og_t2t_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>26</th>
      <td>loc_og_t2t_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>27</th>
      <td>loc_og_t2m_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>28</th>
      <td>loc_og_t2m_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>29</th>
      <td>loc_og_t2m_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>30</th>
      <td>loc_og_t2m_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>31</th>
      <td>loc_og_t2f_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>32</th>
      <td>loc_og_t2f_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>33</th>
      <td>loc_og_t2f_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>34</th>
      <td>loc_og_t2f_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>35</th>
      <td>loc_og_t2c_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>36</th>
      <td>loc_og_t2c_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>37</th>
      <td>loc_og_t2c_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>38</th>
      <td>loc_og_t2c_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>39</th>
      <td>loc_og_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>40</th>
      <td>loc_og_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>41</th>
      <td>loc_og_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>42</th>
      <td>loc_og_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>43</th>
      <td>std_og_t2t_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>44</th>
      <td>std_og_t2t_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>45</th>
      <td>std_og_t2t_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>46</th>
      <td>std_og_t2t_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>47</th>
      <td>std_og_t2m_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>48</th>
      <td>std_og_t2m_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>49</th>
      <td>std_og_t2m_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>50</th>
      <td>std_og_t2m_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>51</th>
      <td>std_og_t2f_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>52</th>
      <td>std_og_t2f_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>53</th>
      <td>std_og_t2f_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>54</th>
      <td>std_og_t2f_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>55</th>
      <td>std_og_t2c_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>56</th>
      <td>std_og_t2c_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>57</th>
      <td>std_og_t2c_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>58</th>
      <td>std_og_t2c_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>59</th>
      <td>std_og_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>60</th>
      <td>std_og_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>61</th>
      <td>std_og_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>62</th>
      <td>std_og_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>63</th>
      <td>isd_og_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>64</th>
      <td>isd_og_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>65</th>
      <td>isd_og_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>66</th>
      <td>isd_og_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>67</th>
      <td>spl_og_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>68</th>
      <td>spl_og_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>69</th>
      <td>spl_og_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>70</th>
      <td>spl_og_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>71</th>
      <td>og_others_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>72</th>
      <td>og_others_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>73</th>
      <td>og_others_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>74</th>
      <td>og_others_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>75</th>
      <td>total_og_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>76</th>
      <td>total_og_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>77</th>
      <td>total_og_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>78</th>
      <td>total_og_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>79</th>
      <td>loc_ic_t2t_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>80</th>
      <td>loc_ic_t2t_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>81</th>
      <td>loc_ic_t2t_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>82</th>
      <td>loc_ic_t2t_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>83</th>
      <td>loc_ic_t2m_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>84</th>
      <td>loc_ic_t2m_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>85</th>
      <td>loc_ic_t2m_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>86</th>
      <td>loc_ic_t2m_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>87</th>
      <td>loc_ic_t2f_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>88</th>
      <td>loc_ic_t2f_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>89</th>
      <td>loc_ic_t2f_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>90</th>
      <td>loc_ic_t2f_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>91</th>
      <td>loc_ic_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>92</th>
      <td>loc_ic_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>93</th>
      <td>loc_ic_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>94</th>
      <td>loc_ic_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>95</th>
      <td>std_ic_t2t_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>96</th>
      <td>std_ic_t2t_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>97</th>
      <td>std_ic_t2t_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>98</th>
      <td>std_ic_t2t_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>99</th>
      <td>std_ic_t2m_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>100</th>
      <td>std_ic_t2m_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>101</th>
      <td>std_ic_t2m_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>102</th>
      <td>std_ic_t2m_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>103</th>
      <td>std_ic_t2f_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>104</th>
      <td>std_ic_t2f_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>105</th>
      <td>std_ic_t2f_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>106</th>
      <td>std_ic_t2f_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>107</th>
      <td>std_ic_t2o_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>108</th>
      <td>std_ic_t2o_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>109</th>
      <td>std_ic_t2o_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>110</th>
      <td>std_ic_t2o_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>111</th>
      <td>std_ic_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>112</th>
      <td>std_ic_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>113</th>
      <td>std_ic_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>114</th>
      <td>std_ic_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>115</th>
      <td>total_ic_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>116</th>
      <td>total_ic_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>117</th>
      <td>total_ic_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>118</th>
      <td>total_ic_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>119</th>
      <td>spl_ic_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>120</th>
      <td>spl_ic_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>121</th>
      <td>spl_ic_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>122</th>
      <td>spl_ic_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>123</th>
      <td>isd_ic_mou_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>124</th>
      <td>isd_ic_mou_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>125</th>
      <td>isd_ic_mou_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>126</th>
      <td>isd_ic_mou_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>127</th>
      <td>ic_others_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>128</th>
      <td>ic_others_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>129</th>
      <td>ic_others_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>130</th>
      <td>ic_others_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>131</th>
      <td>total_rech_num_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>132</th>
      <td>total_rech_num_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>133</th>
      <td>total_rech_num_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>134</th>
      <td>total_rech_num_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>135</th>
      <td>total_rech_amt_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>136</th>
      <td>total_rech_amt_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>137</th>
      <td>total_rech_amt_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>138</th>
      <td>total_rech_amt_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>139</th>
      <td>max_rech_amt_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>140</th>
      <td>max_rech_amt_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>141</th>
      <td>max_rech_amt_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>142</th>
      <td>max_rech_amt_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>143</th>
      <td>last_day_rch_amt_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>144</th>
      <td>last_day_rch_amt_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>145</th>
      <td>last_day_rch_amt_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>146</th>
      <td>last_day_rch_amt_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>147</th>
      <td>total_rech_data_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>148</th>
      <td>total_rech_data_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>149</th>
      <td>total_rech_data_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>150</th>
      <td>total_rech_data_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>151</th>
      <td>max_rech_data_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>152</th>
      <td>max_rech_data_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>153</th>
      <td>max_rech_data_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>154</th>
      <td>max_rech_data_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>163</th>
      <td>av_rech_amt_data_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>164</th>
      <td>av_rech_amt_data_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>165</th>
      <td>av_rech_amt_data_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>166</th>
      <td>av_rech_amt_data_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>167</th>
      <td>vol_2g_mb_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>168</th>
      <td>vol_2g_mb_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>169</th>
      <td>vol_2g_mb_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>170</th>
      <td>vol_2g_mb_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>171</th>
      <td>vol_3g_mb_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>172</th>
      <td>vol_3g_mb_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>173</th>
      <td>vol_3g_mb_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>174</th>
      <td>vol_3g_mb_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>183</th>
      <td>night_pck_user_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>184</th>
      <td>night_pck_user_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>185</th>
      <td>night_pck_user_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>186</th>
      <td>night_pck_user_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>187</th>
      <td>monthly_2g_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>188</th>
      <td>monthly_2g_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>189</th>
      <td>monthly_2g_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>190</th>
      <td>monthly_2g_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>191</th>
      <td>sachet_2g_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>192</th>
      <td>sachet_2g_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>193</th>
      <td>sachet_2g_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>194</th>
      <td>sachet_2g_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>195</th>
      <td>monthly_3g_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>196</th>
      <td>monthly_3g_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>197</th>
      <td>monthly_3g_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>198</th>
      <td>monthly_3g_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>199</th>
      <td>sachet_3g_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>200</th>
      <td>sachet_3g_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>201</th>
      <td>sachet_3g_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>202</th>
      <td>sachet_3g_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>203</th>
      <td>fb_user_6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>204</th>
      <td>fb_user_7</td>
      <td>True</td>
    </tr>
    <tr>
      <th>205</th>
      <td>fb_user_8</td>
      <td>True</td>
    </tr>
    <tr>
      <th>206</th>
      <td>fb_user_9</td>
      <td>True</td>
    </tr>
    <tr>
      <th>207</th>
      <td>aon</td>
      <td>True</td>
    </tr>
    <tr>
      <th>208</th>
      <td>aug_vbc_3g</td>
      <td>True</td>
    </tr>
    <tr>
      <th>209</th>
      <td>jul_vbc_3g</td>
      <td>True</td>
    </tr>
    <tr>
      <th>210</th>
      <td>jun_vbc_3g</td>
      <td>True</td>
    </tr>
    <tr>
      <th>211</th>
      <td>sep_vbc_3g</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
# drop columns
churn = churn.loc[:, include_cols]

dropped_cols = churn.shape[1] - initial_cols
print("{0} columns dropped.".format(dropped_cols))
```

    -16 columns dropped.


## iv) imputing using MICE

install fancyimpute package using [this](https://github.com/iskandr/fancyimpute) link and following the install instructions


```python
churn_cols = churn.columns

# using MICE technique to impute missing values in the rest of the columns
from fancyimpute import MICE
churn_imputed = MICE(n_imputations=1).complete(churn)
```

    Using TensorFlow backend.


    [MICE] Completing matrix with shape (99999, 196)
    [MICE] Starting imputation round 1/11, elapsed time 0.887
    [MICE] Starting imputation round 2/11, elapsed time 176.649
    [MICE] Starting imputation round 3/11, elapsed time 343.774
    [MICE] Starting imputation round 4/11, elapsed time 507.450
    [MICE] Starting imputation round 5/11, elapsed time 677.217
    [MICE] Starting imputation round 6/11, elapsed time 839.576
    [MICE] Starting imputation round 7/11, elapsed time 1001.674
    [MICE] Starting imputation round 8/11, elapsed time 1174.182
    [MICE] Starting imputation round 9/11, elapsed time 1369.406
    [MICE] Starting imputation round 10/11, elapsed time 1534.524
    [MICE] Starting imputation round 11/11, elapsed time 1683.410



```python
# convert imputed numpy array to pandas dataframe
churn = pd.DataFrame(churn_imputed, columns=churn_cols)
print(churn.isnull().sum()*100/churn.shape[0])
```

    loc_og_t2o_mou        0.0
    std_og_t2o_mou        0.0
    loc_ic_t2o_mou        0.0
    arpu_6                0.0
    arpu_7                0.0
    arpu_8                0.0
    arpu_9                0.0
    onnet_mou_6           0.0
    onnet_mou_7           0.0
    onnet_mou_8           0.0
    onnet_mou_9           0.0
    offnet_mou_6          0.0
    offnet_mou_7          0.0
    offnet_mou_8          0.0
    offnet_mou_9          0.0
    roam_ic_mou_6         0.0
    roam_ic_mou_7         0.0
    roam_ic_mou_8         0.0
    roam_ic_mou_9         0.0
    roam_og_mou_6         0.0
    roam_og_mou_7         0.0
    roam_og_mou_8         0.0
    roam_og_mou_9         0.0
    loc_og_t2t_mou_6      0.0
    loc_og_t2t_mou_7      0.0
    loc_og_t2t_mou_8      0.0
    loc_og_t2t_mou_9      0.0
    loc_og_t2m_mou_6      0.0
    loc_og_t2m_mou_7      0.0
    loc_og_t2m_mou_8      0.0
    loc_og_t2m_mou_9      0.0
    loc_og_t2f_mou_6      0.0
    loc_og_t2f_mou_7      0.0
    loc_og_t2f_mou_8      0.0
    loc_og_t2f_mou_9      0.0
    loc_og_t2c_mou_6      0.0
    loc_og_t2c_mou_7      0.0
    loc_og_t2c_mou_8      0.0
    loc_og_t2c_mou_9      0.0
    loc_og_mou_6          0.0
    loc_og_mou_7          0.0
    loc_og_mou_8          0.0
    loc_og_mou_9          0.0
    std_og_t2t_mou_6      0.0
    std_og_t2t_mou_7      0.0
    std_og_t2t_mou_8      0.0
    std_og_t2t_mou_9      0.0
    std_og_t2m_mou_6      0.0
    std_og_t2m_mou_7      0.0
    std_og_t2m_mou_8      0.0
    std_og_t2m_mou_9      0.0
    std_og_t2f_mou_6      0.0
    std_og_t2f_mou_7      0.0
    std_og_t2f_mou_8      0.0
    std_og_t2f_mou_9      0.0
    std_og_t2c_mou_6      0.0
    std_og_t2c_mou_7      0.0
    std_og_t2c_mou_8      0.0
    std_og_t2c_mou_9      0.0
    std_og_mou_6          0.0
    std_og_mou_7          0.0
    std_og_mou_8          0.0
    std_og_mou_9          0.0
    isd_og_mou_6          0.0
    isd_og_mou_7          0.0
    isd_og_mou_8          0.0
    isd_og_mou_9          0.0
    spl_og_mou_6          0.0
    spl_og_mou_7          0.0
    spl_og_mou_8          0.0
    spl_og_mou_9          0.0
    og_others_6           0.0
    og_others_7           0.0
    og_others_8           0.0
    og_others_9           0.0
    total_og_mou_6        0.0
    total_og_mou_7        0.0
    total_og_mou_8        0.0
    total_og_mou_9        0.0
    loc_ic_t2t_mou_6      0.0
    loc_ic_t2t_mou_7      0.0
    loc_ic_t2t_mou_8      0.0
    loc_ic_t2t_mou_9      0.0
    loc_ic_t2m_mou_6      0.0
    loc_ic_t2m_mou_7      0.0
    loc_ic_t2m_mou_8      0.0
    loc_ic_t2m_mou_9      0.0
    loc_ic_t2f_mou_6      0.0
    loc_ic_t2f_mou_7      0.0
    loc_ic_t2f_mou_8      0.0
    loc_ic_t2f_mou_9      0.0
    loc_ic_mou_6          0.0
    loc_ic_mou_7          0.0
    loc_ic_mou_8          0.0
    loc_ic_mou_9          0.0
    std_ic_t2t_mou_6      0.0
    std_ic_t2t_mou_7      0.0
    std_ic_t2t_mou_8      0.0
    std_ic_t2t_mou_9      0.0
    std_ic_t2m_mou_6      0.0
    std_ic_t2m_mou_7      0.0
    std_ic_t2m_mou_8      0.0
    std_ic_t2m_mou_9      0.0
    std_ic_t2f_mou_6      0.0
    std_ic_t2f_mou_7      0.0
    std_ic_t2f_mou_8      0.0
    std_ic_t2f_mou_9      0.0
    std_ic_t2o_mou_6      0.0
    std_ic_t2o_mou_7      0.0
    std_ic_t2o_mou_8      0.0
    std_ic_t2o_mou_9      0.0
    std_ic_mou_6          0.0
    std_ic_mou_7          0.0
    std_ic_mou_8          0.0
    std_ic_mou_9          0.0
    total_ic_mou_6        0.0
    total_ic_mou_7        0.0
    total_ic_mou_8        0.0
    total_ic_mou_9        0.0
    spl_ic_mou_6          0.0
    spl_ic_mou_7          0.0
    spl_ic_mou_8          0.0
    spl_ic_mou_9          0.0
    isd_ic_mou_6          0.0
    isd_ic_mou_7          0.0
    isd_ic_mou_8          0.0
    isd_ic_mou_9          0.0
    ic_others_6           0.0
    ic_others_7           0.0
    ic_others_8           0.0
    ic_others_9           0.0
    total_rech_num_6      0.0
    total_rech_num_7      0.0
    total_rech_num_8      0.0
    total_rech_num_9      0.0
    total_rech_amt_6      0.0
    total_rech_amt_7      0.0
    total_rech_amt_8      0.0
    total_rech_amt_9      0.0
    max_rech_amt_6        0.0
    max_rech_amt_7        0.0
    max_rech_amt_8        0.0
    max_rech_amt_9        0.0
    last_day_rch_amt_6    0.0
    last_day_rch_amt_7    0.0
    last_day_rch_amt_8    0.0
    last_day_rch_amt_9    0.0
    total_rech_data_6     0.0
    total_rech_data_7     0.0
    total_rech_data_8     0.0
    total_rech_data_9     0.0
    max_rech_data_6       0.0
    max_rech_data_7       0.0
    max_rech_data_8       0.0
    max_rech_data_9       0.0
    av_rech_amt_data_6    0.0
    av_rech_amt_data_7    0.0
    av_rech_amt_data_8    0.0
    av_rech_amt_data_9    0.0
    vol_2g_mb_6           0.0
    vol_2g_mb_7           0.0
    vol_2g_mb_8           0.0
    vol_2g_mb_9           0.0
    vol_3g_mb_6           0.0
    vol_3g_mb_7           0.0
    vol_3g_mb_8           0.0
    vol_3g_mb_9           0.0
    night_pck_user_6      0.0
    night_pck_user_7      0.0
    night_pck_user_8      0.0
    night_pck_user_9      0.0
    monthly_2g_6          0.0
    monthly_2g_7          0.0
    monthly_2g_8          0.0
    monthly_2g_9          0.0
    sachet_2g_6           0.0
    sachet_2g_7           0.0
    sachet_2g_8           0.0
    sachet_2g_9           0.0
    monthly_3g_6          0.0
    monthly_3g_7          0.0
    monthly_3g_8          0.0
    monthly_3g_9          0.0
    sachet_3g_6           0.0
    sachet_3g_7           0.0
    sachet_3g_8           0.0
    sachet_3g_9           0.0
    fb_user_6             0.0
    fb_user_7             0.0
    fb_user_8             0.0
    fb_user_9             0.0
    aon                   0.0
    aug_vbc_3g            0.0
    jul_vbc_3g            0.0
    jun_vbc_3g            0.0
    sep_vbc_3g            0.0
    dtype: float64


# filter high-value customers

### calculate total data recharge amount


```python
# calculate the total data recharge amount for June and July --> number of recharges * average recharge amount
churn['total_data_rech_6'] = churn.total_rech_data_6 * churn.av_rech_amt_data_6
churn['total_data_rech_7'] = churn.total_rech_data_7 * churn.av_rech_amt_data_7
```

### add total data recharge and total recharge to get total combined recharge amount for a month


```python
# calculate total recharge amount for June and July --> call recharge amount + data recharge amount
churn['amt_data_6'] = churn.total_rech_amt_6 + churn.total_data_rech_6
churn['amt_data_7'] = churn.total_rech_amt_7 + churn.total_data_rech_7
```


```python
# calculate average recharge done by customer in June and July
churn['av_amt_data_6_7'] = (churn.amt_data_6 + churn.amt_data_7)/2
```


```python
# look at the 70th percentile recharge amount
print("Recharge amount at 70th percentile: {0}".format(churn.av_amt_data_6_7.quantile(0.7)))
```

    Recharge amount at 70th percentile: 478.0



```python
# retain only those customers who have recharged their mobiles with more than or equal to 70th percentile amount
churn_filtered = churn.loc[churn.av_amt_data_6_7 >= churn.av_amt_data_6_7.quantile(0.7), :]
churn_filtered = churn_filtered.reset_index(drop=True)
churn_filtered.shape
```




    (30001, 201)




```python
# delete variables created to filter high-value customers
churn_filtered = churn_filtered.drop(['total_data_rech_6', 'total_data_rech_7',
                                      'amt_data_6', 'amt_data_7', 'av_amt_data_6_7'], axis=1)
churn_filtered.shape
```




    (30001, 196)



We're left with 30,001 rows after selecting the customers who have provided recharge value of more than or equal to the recharge value of the 70th percentile customer.

# derive churn


```python
# calculate total incoming and outgoing minutes of usage
churn_filtered['total_calls_mou_9'] = churn_filtered.total_ic_mou_9 + churn_filtered.total_og_mou_9
```


```python
# calculate 2g and 3g data consumption
churn_filtered['total_internet_mb_9'] =  churn_filtered.vol_2g_mb_9 + churn_filtered.vol_3g_mb_9
```


```python
# create churn variable: those who have not used either calls or internet in the month of September are customers who have churned

# 0 - not churn, 1 - churn
churn_filtered['churn'] = churn_filtered.apply(lambda row: 1 if (row.total_calls_mou_9 == 0 and row.total_internet_mb_9 == 0) else 0, axis=1)
```


```python
# delete derived variables
churn_filtered = churn_filtered.drop(['total_calls_mou_9', 'total_internet_mb_9'], axis=1)
```


```python
# change data type to category
churn_filtered.churn = churn_filtered.churn.astype("category")

# print churn ratio
print("Churn Ratio:")
print(churn_filtered.churn.value_counts()*100/churn_filtered.shape[0])
```

    Churn Ratio:
    0    91.863605
    1     8.136395
    Name: churn, dtype: float64


# Calculate difference between 8th and previous months

Let's derive some variables. The most important feature, in this situation, can be the difference between the 8th month and the previous months. The difference can be in patterns such as usage difference or recharge value difference. Let's calculate difference variable as the difference between 8th month and the average of 6th and 7th month.


```python
churn_filtered['arpu_diff'] = churn_filtered.arpu_8 - ((churn_filtered.arpu_6 + churn_filtered.arpu_7)/2)

churn_filtered['onnet_mou_diff'] = churn_filtered.onnet_mou_8 - ((churn_filtered.onnet_mou_6 + churn_filtered.onnet_mou_7)/2)

churn_filtered['offnet_mou_diff'] = churn_filtered.offnet_mou_8 - ((churn_filtered.offnet_mou_6 + churn_filtered.offnet_mou_7)/2)

churn_filtered['roam_ic_mou_diff'] = churn_filtered.roam_ic_mou_8 - ((churn_filtered.roam_ic_mou_6 + churn_filtered.roam_ic_mou_7)/2)

churn_filtered['roam_og_mou_diff'] = churn_filtered.roam_og_mou_8 - ((churn_filtered.roam_og_mou_6 + churn_filtered.roam_og_mou_7)/2)

churn_filtered['loc_og_mou_diff'] = churn_filtered.loc_og_mou_8 - ((churn_filtered.loc_og_mou_6 + churn_filtered.loc_og_mou_7)/2)

churn_filtered['std_og_mou_diff'] = churn_filtered.std_og_mou_8 - ((churn_filtered.std_og_mou_6 + churn_filtered.std_og_mou_7)/2)

churn_filtered['isd_og_mou_diff'] = churn_filtered.isd_og_mou_8 - ((churn_filtered.isd_og_mou_6 + churn_filtered.isd_og_mou_7)/2)

churn_filtered['spl_og_mou_diff'] = churn_filtered.spl_og_mou_8 - ((churn_filtered.spl_og_mou_6 + churn_filtered.spl_og_mou_7)/2)

churn_filtered['total_og_mou_diff'] = churn_filtered.total_og_mou_8 - ((churn_filtered.total_og_mou_6 + churn_filtered.total_og_mou_7)/2)

churn_filtered['loc_ic_mou_diff'] = churn_filtered.loc_ic_mou_8 - ((churn_filtered.loc_ic_mou_6 + churn_filtered.loc_ic_mou_7)/2)

churn_filtered['std_ic_mou_diff'] = churn_filtered.std_ic_mou_8 - ((churn_filtered.std_ic_mou_6 + churn_filtered.std_ic_mou_7)/2)

churn_filtered['isd_ic_mou_diff'] = churn_filtered.isd_ic_mou_8 - ((churn_filtered.isd_ic_mou_6 + churn_filtered.isd_ic_mou_7)/2)

churn_filtered['spl_ic_mou_diff'] = churn_filtered.spl_ic_mou_8 - ((churn_filtered.spl_ic_mou_6 + churn_filtered.spl_ic_mou_7)/2)

churn_filtered['total_ic_mou_diff'] = churn_filtered.total_ic_mou_8 - ((churn_filtered.total_ic_mou_6 + churn_filtered.total_ic_mou_7)/2)

churn_filtered['total_rech_num_diff'] = churn_filtered.total_rech_num_8 - ((churn_filtered.total_rech_num_6 + churn_filtered.total_rech_num_7)/2)

churn_filtered['total_rech_amt_diff'] = churn_filtered.total_rech_amt_8 - ((churn_filtered.total_rech_amt_6 + churn_filtered.total_rech_amt_7)/2)

churn_filtered['max_rech_amt_diff'] = churn_filtered.max_rech_amt_8 - ((churn_filtered.max_rech_amt_6 + churn_filtered.max_rech_amt_7)/2)

churn_filtered['total_rech_data_diff'] = churn_filtered.total_rech_data_8 - ((churn_filtered.total_rech_data_6 + churn_filtered.total_rech_data_7)/2)

churn_filtered['max_rech_data_diff'] = churn_filtered.max_rech_data_8 - ((churn_filtered.max_rech_data_6 + churn_filtered.max_rech_data_7)/2)

churn_filtered['av_rech_amt_data_diff'] = churn_filtered.av_rech_amt_data_8 - ((churn_filtered.av_rech_amt_data_6 + churn_filtered.av_rech_amt_data_7)/2)

churn_filtered['vol_2g_mb_diff'] = churn_filtered.vol_2g_mb_8 - ((churn_filtered.vol_2g_mb_6 + churn_filtered.vol_2g_mb_7)/2)

churn_filtered['vol_3g_mb_diff'] = churn_filtered.vol_3g_mb_8 - ((churn_filtered.vol_3g_mb_6 + churn_filtered.vol_3g_mb_7)/2)
```


```python
# let's look at summary of one of the difference variables
churn_filtered['total_og_mou_diff'].describe()
```




    count    30001.000000
    mean       -67.437337
    std        502.630069
    min      -7213.410000
    25%       -168.025000
    50%        -14.625000
    75%         67.915000
    max      12768.705000
    Name: total_og_mou_diff, dtype: float64



## delete columns that belong to the churn month (9th month)


```python
# delete all variables relating to 9th month
churn_filtered = churn_filtered.filter(regex='[^9]$', axis=1)
churn_filtered.shape
```




    (30001, 173)




```python
# extract all names that end with 9
col_9_names = churn.filter(regex='9$', axis=1).columns

# update num_cols and cat_cols column name list
cat_cols = [col for col in cat_cols if col not in col_9_names]
cat_cols.append('churn')
num_cols = [col for col in churn_filtered.columns if col not in cat_cols]
```

## visualise data


```python
# change columns types
churn_filtered[num_cols] = churn_filtered[num_cols].apply(pd.to_numeric)
churn_filtered[cat_cols] = churn_filtered[cat_cols].apply(lambda column: column.astype("category"), axis=0)
```


```python
# create plotting functions
def data_type(variable):
    if variable.dtype == np.int64 or variable.dtype == np.float64:
        return 'numerical'
    elif variable.dtype == 'category':
        return 'categorical'
    
def univariate(variable, stats=True):
    
    if data_type(variable) == 'numerical':
        sns.distplot(variable)
        if stats == True:
            print(variable.describe())
    
    elif data_type(variable) == 'categorical':
        sns.countplot(variable)
        if stats == True:
            print(variable.value_counts())
            
    else:
        print("Invalid variable passed: either pass a numeric variable or a categorical vairable.")
        
def bivariate(var1, var2):
    if data_type(var1) == 'numerical' and data_type(var2) == 'numerical':
        sns.regplot(var1, var2)
    elif (data_type(var1) == 'categorical' and data_type(var2) == 'numerical') or (data_type(var1) == 'numerical' and data_type(var2) == 'categorical'):        
        sns.boxplot(var1, var2)
```

## Univariate EDA


```python
univariate(churn.arpu_6)
```

    count    99999.000000
    mean       282.987358
    std        328.439770
    min      -2258.709000
    25%         93.411500
    50%        197.704000
    75%        371.060000
    max      27731.088000
    Name: arpu_6, dtype: float64



    
![png](solution_telecom_churn_files/solution_telecom_churn_57_1.png)
    



```python
univariate(churn.loc_og_t2o_mou)
```

    count    99999.000000
    mean        -0.000002
    std          0.000312
    min         -0.009873
    25%          0.000000
    50%          0.000000
    75%          0.000000
    max          0.009702
    Name: loc_og_t2o_mou, dtype: float64



    
![png](solution_telecom_churn_files/solution_telecom_churn_58_1.png)
    



```python
univariate(churn.std_og_t2o_mou)
```

    count    9.999900e+04
    mean    -9.957627e-07
    std      3.136615e-04
    min     -1.085887e-02
    25%      0.000000e+00
    50%      0.000000e+00
    75%      0.000000e+00
    max      9.418004e-03
    Name: std_og_t2o_mou, dtype: float64



    
![png](solution_telecom_churn_files/solution_telecom_churn_59_1.png)
    



```python
univariate(churn.onnet_mou_8)
```

    count    99999.000000
    mean       125.972580
    std        302.822628
    min       -700.923704
    25%          5.510000
    50%         30.760000
    75%        109.400000
    max      10752.560000
    Name: onnet_mou_8, dtype: float64



    
![png](solution_telecom_churn_files/solution_telecom_churn_60_1.png)
    



```python
univariate(churn.offnet_mou_9)
```

    count    99999.000000
    mean       176.085292
    std        311.955151
    min      -1407.015438
    25%         21.903023
    50%         78.360000
    75%        204.270000
    max      10310.760000
    Name: offnet_mou_9, dtype: float64



    
![png](solution_telecom_churn_files/solution_telecom_churn_61_1.png)
    


Variables are very **skewed** towards the left.

## Bivariate EDA


```python
bivariate(churn_filtered.churn, churn_filtered.aon)
```


    
![png](solution_telecom_churn_files/solution_telecom_churn_64_0.png)
    



```python
bivariate(churn_filtered.sep_vbc_3g, churn_filtered.churn)
```


    
![png](solution_telecom_churn_files/solution_telecom_churn_65_0.png)
    



```python
bivariate(churn_filtered.spl_og_mou_8, churn_filtered.churn)
```


    
![png](solution_telecom_churn_files/solution_telecom_churn_66_0.png)
    



```python
pd.crosstab(churn_filtered.churn, churn_filtered.night_pck_user_8, normalize='columns')*100
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
      <th>night_pck_user_8</th>
      <th>-1.0</th>
      <th>0.0</th>
      <th>1.0</th>
    </tr>
    <tr>
      <th>churn</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>85.89123</td>
      <td>97.117602</td>
      <td>97.360704</td>
    </tr>
    <tr>
      <th>1</th>
      <td>14.10877</td>
      <td>2.882398</td>
      <td>2.639296</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.crosstab(churn_filtered.churn, churn_filtered.sachet_3g_8)
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
      <th>sachet_3g_8</th>
      <th>0.0</th>
      <th>1.0</th>
      <th>2.0</th>
      <th>3.0</th>
      <th>4.0</th>
      <th>5.0</th>
      <th>6.0</th>
      <th>7.0</th>
      <th>8.0</th>
      <th>9.0</th>
      <th>10.0</th>
      <th>11.0</th>
      <th>12.0</th>
      <th>13.0</th>
      <th>14.0</th>
      <th>15.0</th>
      <th>16.0</th>
      <th>17.0</th>
      <th>18.0</th>
      <th>19.0</th>
      <th>20.0</th>
      <th>21.0</th>
      <th>23.0</th>
      <th>25.0</th>
      <th>27.0</th>
      <th>29.0</th>
      <th>30.0</th>
      <th>38.0</th>
      <th>41.0</th>
    </tr>
    <tr>
      <th>churn</th>
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
      <th>0</th>
      <td>24972</td>
      <td>1609</td>
      <td>399</td>
      <td>184</td>
      <td>106</td>
      <td>86</td>
      <td>43</td>
      <td>35</td>
      <td>28</td>
      <td>19</td>
      <td>15</td>
      <td>8</td>
      <td>11</td>
      <td>10</td>
      <td>6</td>
      <td>6</td>
      <td>2</td>
      <td>2</td>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>3</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2369</td>
      <td>48</td>
      <td>5</td>
      <td>8</td>
      <td>4</td>
      <td>2</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



### Cap outliers in all numeric variables with k-sigma technique


```python
def cap_outliers(array, k=3):
    upper_limit = array.mean() + k*array.std()
    lower_limit = array.mean() - k*array.std()
    array[array<lower_limit] = lower_limit
    array[array>upper_limit] = upper_limit
    return array
```


```python
# example of capping
sample_array = list(range(100))

# add outliers to the data
sample_array[0] = -9999
sample_array[99] = 9999

# cap outliers
sample_array = np.array(sample_array)
print("Array after capping outliers: \n", cap_outliers(sample_array, k=2))
```

    Array after capping outliers: 
     [-2780     1     2     3     4     5     6     7     8     9    10    11
        12    13    14    15    16    17    18    19    20    21    22    23
        24    25    26    27    28    29    30    31    32    33    34    35
        36    37    38    39    40    41    42    43    44    45    46    47
        48    49    50    51    52    53    54    55    56    57    58    59
        60    61    62    63    64    65    66    67    68    69    70    71
        72    73    74    75    76    77    78    79    80    81    82    83
        84    85    86    87    88    89    90    91    92    93    94    95
        96    97    98  2877]



```python
# cap outliers in the numeric columns
churn_filtered[num_cols] = churn_filtered[num_cols].apply(cap_outliers, axis=0)
```

# Modelling

## i) Making predictions


```python
# import required libraries
from sklearn.model_selection import train_test_split
from sklearn.pipeline import Pipeline
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import FeatureUnion
from sklearn.base import BaseEstimator, TransformerMixin
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report
from sklearn.metrics import roc_auc_score
from imblearn.metrics import sensitivity_specificity_support
from sklearn.model_selection import StratifiedKFold
from sklearn.model_selection import cross_val_score
from sklearn.metrics import confusion_matrix
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier
from sklearn.ensemble import GradientBoostingClassifier
from sklearn.svm import SVC
```

## Preprocessing data


```python
# change churn to numeric
churn_filtered['churn'] = pd.to_numeric(churn_filtered['churn'])
```

### Train Test split


```python
# divide data into train and test
X = churn_filtered.drop("churn", axis = 1)
y = churn_filtered.churn
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.25, random_state = 4, stratify = y)
```


```python
# print shapes of train and test sets
X_train.shape
y_train.shape
X_test.shape
y_test.shape
```




    (22500, 172)






    (22500,)






    (7501, 172)






    (7501,)



## Aggregating the categorical columns


```python
train = pd.concat([X_train, y_train], axis=1)

# aggregate the categorical variables
train.groupby('night_pck_user_6').churn.mean()
train.groupby('night_pck_user_7').churn.mean()
train.groupby('night_pck_user_8').churn.mean()
train.groupby('fb_user_6').churn.mean()
train.groupby('fb_user_7').churn.mean()
train.groupby('fb_user_8').churn.mean()
```




    night_pck_user_6
    -1.0    0.099165
     0.0    0.066797
     1.0    0.087838
    Name: churn, dtype: float64






    night_pck_user_7
    -1.0    0.115746
     0.0    0.055494
     1.0    0.051282
    Name: churn, dtype: float64






    night_pck_user_8
    -1.0    0.141108
     0.0    0.029023
     1.0    0.016194
    Name: churn, dtype: float64






    fb_user_6
    -1.0    0.099165
     0.0    0.069460
     1.0    0.067124
    Name: churn, dtype: float64






    fb_user_7
    -1.0    0.115746
     0.0    0.059305
     1.0    0.055082
    Name: churn, dtype: float64






    fb_user_8
    -1.0    0.141108
     0.0    0.066887
     1.0    0.024463
    Name: churn, dtype: float64




```python
# replace categories with aggregated values in each categorical column
mapping = {'night_pck_user_6' : {-1: 0.099165, 0: 0.066797, 1: 0.087838},
           'night_pck_user_7' : {-1: 0.115746, 0: 0.055494, 1: 0.051282},
           'night_pck_user_8' : {-1: 0.141108, 0: 0.029023, 1: 0.016194},
           'fb_user_6'        : {-1: 0.099165, 0: 0.069460, 1: 0.067124},
           'fb_user_7'        : {-1: 0.115746, 0: 0.059305, 1: 0.055082},
           'fb_user_8'        : {-1: 0.141108, 0: 0.066887, 1: 0.024463}
          }
X_train.replace(mapping, inplace = True)
X_test.replace(mapping, inplace = True)
```


```python
# check data type of categorical columns - make sure they are numeric
X_train[[col for col in cat_cols if col not in ['churn']]].info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 22500 entries, 4525 to 22754
    Data columns (total 6 columns):
    night_pck_user_6    22500 non-null float64
    night_pck_user_7    22500 non-null float64
    night_pck_user_8    22500 non-null float64
    fb_user_6           22500 non-null float64
    fb_user_7           22500 non-null float64
    fb_user_8           22500 non-null float64
    dtypes: float64(6)
    memory usage: 1.2 MB


## PCA


```python
# apply pca to train data
pca = Pipeline([('scaler', StandardScaler()), ('pca', PCA())])
```


```python
pca.fit(X_train)
churn_pca = pca.fit_transform(X_train)
```




    Pipeline(memory=None,
         steps=[('scaler', StandardScaler(copy=True, with_mean=True, with_std=True)), ('pca', PCA(copy=True, iterated_power='auto', n_components=None, random_state=None,
      svd_solver='auto', tol=0.0, whiten=False))])




```python
# extract pca model from pipeline
pca = pca.named_steps['pca']

# look at explainded variance of PCA components
print(pd.Series(np.round(pca.explained_variance_ratio_.cumsum(), 4)*100))
```

    0       10.91
    1       19.80
    2       25.31
    3       29.95
    4       33.80
    5       37.30
    6       39.90
    7       42.33
    8       44.51
    9       46.52
    10      48.42
    11      50.23
    12      51.91
    13      53.54
    14      55.03
    15      56.40
    16      57.70
    17      58.95
    18      60.19
    19      61.41
    20      62.54
    21      63.65
    22      64.71
    23      65.72
    24      66.70
    25      67.61
    26      68.49
    27      69.34
    28      70.17
    29      71.00
    30      71.77
    31      72.54
    32      73.30
    33      74.05
    34      74.77
    35      75.46
    36      76.15
    37      76.82
    38      77.49
    39      78.15
    40      78.79
    41      79.42
    42      80.04
    43      80.65
    44      81.23
    45      81.80
    46      82.36
    47      82.89
    48      83.43
    49      83.94
    50      84.45
    51      84.95
    52      85.45
    53      85.93
    54      86.40
    55      86.85
    56      87.30
    57      87.75
    58      88.19
    59      88.61
    60      89.02
    61      89.41
    62      89.78
    63      90.13
    64      90.47
    65      90.81
    66      91.13
    67      91.45
    68      91.75
    69      92.05
    70      92.34
    71      92.62
    72      92.89
    73      93.16
    74      93.43
    75      93.69
    76      93.93
    77      94.17
    78      94.41
    79      94.64
    80      94.86
    81      95.05
    82      95.25
    83      95.43
    84      95.62
    85      95.80
    86      95.97
    87      96.15
    88      96.31
    89      96.48
    90      96.64
    91      96.80
    92      96.96
    93      97.11
    94      97.25
    95      97.39
    96      97.53
    97      97.66
    98      97.78
    99      97.90
    100     98.02
    101     98.14
    102     98.25
    103     98.34
    104     98.43
    105     98.52
    106     98.60
    107     98.68
    108     98.76
    109     98.83
    110     98.90
    111     98.95
    112     99.01
    113     99.06
    114     99.12
    115     99.17
    116     99.22
    117     99.26
    118     99.30
    119     99.34
    120     99.38
    121     99.42
    122     99.45
    123     99.48
    124     99.51
    125     99.53
    126     99.56
    127     99.58
    128     99.61
    129     99.63
    130     99.65
    131     99.67
    132     99.69
    133     99.71
    134     99.72
    135     99.74
    136     99.76
    137     99.77
    138     99.79
    139     99.80
    140     99.82
    141     99.83
    142     99.84
    143     99.85
    144     99.86
    145     99.87
    146     99.88
    147     99.89
    148     99.90
    149     99.91
    150     99.92
    151     99.92
    152     99.93
    153     99.94
    154     99.94
    155     99.95
    156     99.95
    157     99.96
    158     99.97
    159     99.97
    160     99.97
    161     99.98
    162     99.98
    163     99.98
    164     99.99
    165     99.99
    166     99.99
    167    100.00
    168    100.00
    169    100.00
    170    100.00
    171    100.00
    dtype: float64


~ 60 components explain 90% variance

~ 80 components explain 95% variance


```python
# plot feature variance
features = range(pca.n_components_)
cumulative_variance = np.round(np.cumsum(pca.explained_variance_ratio_)*100, decimals=4)
plt.figure(figsize=(175/20,100/20)) # 100 elements on y-axis; 175 elements on x-axis; 20 is normalising factor
plt.plot(cumulative_variance)
```




    <Figure size 630x360 with 0 Axes>






    [<matplotlib.lines.Line2D at 0x2b6027981d0>]




    
![png](solution_telecom_churn_files/solution_telecom_churn_90_2.png)
    


## PCA and Logistic Regression


```python
# create pipeline
PCA_VARS = 60
steps = [('scaler', StandardScaler()),
         ("pca", PCA(n_components=PCA_VARS)),
         ("logistic", LogisticRegression(class_weight='balanced'))
        ]
pipeline = Pipeline(steps)
```


```python
# fit model
pipeline.fit(X_train, y_train)

# check score on train data
pipeline.score(X_train, y_train)
```




    Pipeline(memory=None,
         steps=[('scaler', StandardScaler(copy=True, with_mean=True, with_std=True)), ('pca', PCA(copy=True, iterated_power='auto', n_components=60, random_state=None,
      svd_solver='auto', tol=0.0, whiten=False)), ('logistic', LogisticRegression(C=1.0, class_weight='balanced', dual=False,
              fit_intercept=True, intercept_scaling=1, max_iter=100,
              multi_class='ovr', n_jobs=1, penalty='l2', random_state=None,
              solver='liblinear', tol=0.0001, verbose=0, warm_start=False))])






    0.8205333333333333



### Evaluate on test data


```python
# predict churn on test data
y_pred = pipeline.predict(X_test)

# create onfusion matrix
cm = confusion_matrix(y_test, y_pred)
print(cm)

# check sensitivity and specificity
sensitivity, specificity, _ = sensitivity_specificity_support(y_test, y_pred, average='binary')
print("Sensitivity: \t", round(sensitivity, 2), "\n", "Specificity: \t", round(specificity, 2), sep='')

# check area under curve
y_pred_prob = pipeline.predict_proba(X_test)[:, 1]
print("AUC:    \t", round(roc_auc_score(y_test, y_pred_prob),2))
```

    [[5613 1278]
     [  91  519]]
    Sensitivity: 	0.85
    Specificity: 	0.81
    AUC:    	 0.9


### Hyperparameter tuning - PCA and Logistic Regression


```python
# class imbalance
y_train.value_counts()/y_train.shape
```




    0    0.918622
    1    0.081378
    Name: churn, dtype: float64




```python
# PCA
pca = PCA()

# logistic regression - the class weight is used to handle class imbalance - it adjusts the cost function
logistic = LogisticRegression(class_weight={0:0.1, 1: 0.9})

# create pipeline
steps = [("scaler", StandardScaler()), 
         ("pca", pca),
         ("logistic", logistic)
        ]

# compile pipeline
pca_logistic = Pipeline(steps)

# hyperparameter space
params = {'pca__n_components': [60, 80], 'logistic__C': [0.1, 0.5, 1, 2, 3, 4, 5, 10], 'logistic__penalty': ['l1', 'l2']}

# create 5 folds
folds = StratifiedKFold(n_splits = 5, shuffle = True, random_state = 4)

# create gridsearch object
model = GridSearchCV(estimator=pca_logistic, cv=folds, param_grid=params, scoring='roc_auc', n_jobs=-1, verbose=1)
```


```python
# fit model
model.fit(X_train, y_train)
```

    Fitting 5 folds for each of 32 candidates, totalling 160 fits


    [Parallel(n_jobs=-1)]: Done  42 tasks      | elapsed:  3.0min
    [Parallel(n_jobs=-1)]: Done 160 out of 160 | elapsed: 10.3min finished





    GridSearchCV(cv=StratifiedKFold(n_splits=5, random_state=4, shuffle=True),
           error_score='raise',
           estimator=Pipeline(memory=None,
         steps=[('scaler', StandardScaler(copy=True, with_mean=True, with_std=True)), ('pca', PCA(copy=True, iterated_power='auto', n_components=None, random_state=None,
      svd_solver='auto', tol=0.0, whiten=False)), ('logistic', LogisticRegression(C=1.0, class_weight={0: ...y='l2', random_state=None,
              solver='liblinear', tol=0.0001, verbose=0, warm_start=False))]),
           fit_params=None, iid=True, n_jobs=-1,
           param_grid={'pca__n_components': [60, 80], 'logistic__C': [0.1, 0.5, 1, 2, 3, 4, 5, 10], 'logistic__penalty': ['l1', 'l2']},
           pre_dispatch='2*n_jobs', refit=True, return_train_score='warn',
           scoring='roc_auc', verbose=1)




```python
# cross validation results
pd.DataFrame(model.cv_results_)
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
      <th>mean_fit_time</th>
      <th>std_fit_time</th>
      <th>mean_score_time</th>
      <th>std_score_time</th>
      <th>param_logistic__C</th>
      <th>param_logistic__penalty</th>
      <th>param_pca__n_components</th>
      <th>params</th>
      <th>split0_test_score</th>
      <th>split1_test_score</th>
      <th>split2_test_score</th>
      <th>split3_test_score</th>
      <th>split4_test_score</th>
      <th>mean_test_score</th>
      <th>std_test_score</th>
      <th>rank_test_score</th>
      <th>split0_train_score</th>
      <th>split1_train_score</th>
      <th>split2_train_score</th>
      <th>split3_train_score</th>
      <th>split4_train_score</th>
      <th>mean_train_score</th>
      <th>std_train_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>14.310691</td>
      <td>3.601207</td>
      <td>0.082182</td>
      <td>0.026817</td>
      <td>0.1</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 0.1, 'logistic__penalty': 'l1'...</td>
      <td>0.893424</td>
      <td>0.896388</td>
      <td>0.879455</td>
      <td>0.879650</td>
      <td>0.889877</td>
      <td>0.887759</td>
      <td>0.007011</td>
      <td>31</td>
      <td>0.892666</td>
      <td>0.891376</td>
      <td>0.896544</td>
      <td>0.895234</td>
      <td>0.892728</td>
      <td>0.893710</td>
      <td>0.001890</td>
    </tr>
    <tr>
      <th>1</th>
      <td>16.386900</td>
      <td>4.125111</td>
      <td>0.097794</td>
      <td>0.029306</td>
      <td>0.1</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 0.1, 'logistic__penalty': 'l1'...</td>
      <td>0.897337</td>
      <td>0.900268</td>
      <td>0.880970</td>
      <td>0.884409</td>
      <td>0.891970</td>
      <td>0.890991</td>
      <td>0.007363</td>
      <td>4</td>
      <td>0.896789</td>
      <td>0.895300</td>
      <td>0.901144</td>
      <td>0.899414</td>
      <td>0.897095</td>
      <td>0.897948</td>
      <td>0.002071</td>
    </tr>
    <tr>
      <th>2</th>
      <td>13.135526</td>
      <td>3.310098</td>
      <td>0.077551</td>
      <td>0.012029</td>
      <td>0.1</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 0.1, 'logistic__penalty': 'l2'...</td>
      <td>0.893687</td>
      <td>0.897616</td>
      <td>0.878130</td>
      <td>0.881052</td>
      <td>0.887659</td>
      <td>0.887629</td>
      <td>0.007347</td>
      <td>32</td>
      <td>0.893948</td>
      <td>0.892525</td>
      <td>0.897778</td>
      <td>0.896400</td>
      <td>0.893911</td>
      <td>0.894912</td>
      <td>0.001901</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12.918391</td>
      <td>1.810922</td>
      <td>0.065158</td>
      <td>0.020049</td>
      <td>0.1</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 0.1, 'logistic__penalty': 'l2'...</td>
      <td>0.898398</td>
      <td>0.902419</td>
      <td>0.879356</td>
      <td>0.885687</td>
      <td>0.888061</td>
      <td>0.890785</td>
      <td>0.008454</td>
      <td>12</td>
      <td>0.898696</td>
      <td>0.897261</td>
      <td>0.903302</td>
      <td>0.901211</td>
      <td>0.899328</td>
      <td>0.899960</td>
      <td>0.002098</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11.820128</td>
      <td>1.256941</td>
      <td>0.080447</td>
      <td>0.017170</td>
      <td>0.5</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 0.5, 'logistic__penalty': 'l1'...</td>
      <td>0.893679</td>
      <td>0.897867</td>
      <td>0.878308</td>
      <td>0.882753</td>
      <td>0.887484</td>
      <td>0.888018</td>
      <td>0.007090</td>
      <td>27</td>
      <td>0.894088</td>
      <td>0.892613</td>
      <td>0.897908</td>
      <td>0.896497</td>
      <td>0.893941</td>
      <td>0.895010</td>
      <td>0.001916</td>
    </tr>
    <tr>
      <th>5</th>
      <td>13.521796</td>
      <td>2.146524</td>
      <td>0.073405</td>
      <td>0.027843</td>
      <td>0.5</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 0.5, 'logistic__penalty': 'l1'...</td>
      <td>0.898683</td>
      <td>0.902399</td>
      <td>0.880324</td>
      <td>0.886327</td>
      <td>0.888062</td>
      <td>0.891159</td>
      <td>0.008165</td>
      <td>1</td>
      <td>0.899092</td>
      <td>0.897484</td>
      <td>0.903248</td>
      <td>0.901630</td>
      <td>0.899408</td>
      <td>0.900172</td>
      <td>0.002028</td>
    </tr>
    <tr>
      <th>6</th>
      <td>12.641425</td>
      <td>1.906088</td>
      <td>0.099816</td>
      <td>0.026067</td>
      <td>0.5</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 0.5, 'logistic__penalty': 'l2'...</td>
      <td>0.893508</td>
      <td>0.899112</td>
      <td>0.879066</td>
      <td>0.881703</td>
      <td>0.887790</td>
      <td>0.888236</td>
      <td>0.007390</td>
      <td>21</td>
      <td>0.894371</td>
      <td>0.893142</td>
      <td>0.897970</td>
      <td>0.896631</td>
      <td>0.894203</td>
      <td>0.895263</td>
      <td>0.001767</td>
    </tr>
    <tr>
      <th>7</th>
      <td>14.712002</td>
      <td>2.578477</td>
      <td>0.084825</td>
      <td>0.015302</td>
      <td>0.5</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 0.5, 'logistic__penalty': 'l2'...</td>
      <td>0.898306</td>
      <td>0.903206</td>
      <td>0.878682</td>
      <td>0.885838</td>
      <td>0.887425</td>
      <td>0.890692</td>
      <td>0.008867</td>
      <td>15</td>
      <td>0.898902</td>
      <td>0.897928</td>
      <td>0.903264</td>
      <td>0.901740</td>
      <td>0.899956</td>
      <td>0.900358</td>
      <td>0.001926</td>
    </tr>
    <tr>
      <th>8</th>
      <td>13.321897</td>
      <td>2.116156</td>
      <td>0.058245</td>
      <td>0.004616</td>
      <td>1</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 1, 'logistic__penalty': 'l1', ...</td>
      <td>0.893752</td>
      <td>0.898875</td>
      <td>0.878751</td>
      <td>0.881968</td>
      <td>0.888902</td>
      <td>0.888450</td>
      <td>0.007390</td>
      <td>17</td>
      <td>0.893867</td>
      <td>0.893071</td>
      <td>0.897947</td>
      <td>0.896748</td>
      <td>0.893701</td>
      <td>0.895067</td>
      <td>0.001919</td>
    </tr>
    <tr>
      <th>9</th>
      <td>19.162462</td>
      <td>3.309108</td>
      <td>0.110470</td>
      <td>0.019740</td>
      <td>1</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 1, 'logistic__penalty': 'l1', ...</td>
      <td>0.898415</td>
      <td>0.902568</td>
      <td>0.879834</td>
      <td>0.885961</td>
      <td>0.886980</td>
      <td>0.890752</td>
      <td>0.008423</td>
      <td>13</td>
      <td>0.899063</td>
      <td>0.897616</td>
      <td>0.903631</td>
      <td>0.901452</td>
      <td>0.900046</td>
      <td>0.900361</td>
      <td>0.002059</td>
    </tr>
    <tr>
      <th>10</th>
      <td>15.568770</td>
      <td>2.484354</td>
      <td>0.118456</td>
      <td>0.030634</td>
      <td>1</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 1, 'logistic__penalty': 'l2', ...</td>
      <td>0.893823</td>
      <td>0.898972</td>
      <td>0.878438</td>
      <td>0.882174</td>
      <td>0.887813</td>
      <td>0.888244</td>
      <td>0.007476</td>
      <td>19</td>
      <td>0.894258</td>
      <td>0.893140</td>
      <td>0.898050</td>
      <td>0.896597</td>
      <td>0.893891</td>
      <td>0.895187</td>
      <td>0.001840</td>
    </tr>
    <tr>
      <th>11</th>
      <td>16.555754</td>
      <td>3.087109</td>
      <td>0.093842</td>
      <td>0.048670</td>
      <td>1</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 1, 'logistic__penalty': 'l2', ...</td>
      <td>0.898471</td>
      <td>0.902412</td>
      <td>0.879082</td>
      <td>0.886062</td>
      <td>0.887175</td>
      <td>0.890641</td>
      <td>0.008561</td>
      <td>16</td>
      <td>0.899074</td>
      <td>0.897885</td>
      <td>0.903625</td>
      <td>0.901875</td>
      <td>0.899692</td>
      <td>0.900430</td>
      <td>0.002057</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13.754140</td>
      <td>2.333608</td>
      <td>0.088560</td>
      <td>0.007758</td>
      <td>2</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 2, 'logistic__penalty': 'l1', ...</td>
      <td>0.893921</td>
      <td>0.898779</td>
      <td>0.878671</td>
      <td>0.881348</td>
      <td>0.888282</td>
      <td>0.888201</td>
      <td>0.007515</td>
      <td>23</td>
      <td>0.894323</td>
      <td>0.892967</td>
      <td>0.898030</td>
      <td>0.896559</td>
      <td>0.893820</td>
      <td>0.895140</td>
      <td>0.001871</td>
    </tr>
    <tr>
      <th>13</th>
      <td>15.155681</td>
      <td>3.357157</td>
      <td>0.089516</td>
      <td>0.022169</td>
      <td>2</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 2, 'logistic__penalty': 'l1', ...</td>
      <td>0.898966</td>
      <td>0.902460</td>
      <td>0.879081</td>
      <td>0.886981</td>
      <td>0.887136</td>
      <td>0.890925</td>
      <td>0.008578</td>
      <td>7</td>
      <td>0.899210</td>
      <td>0.897953</td>
      <td>0.903529</td>
      <td>0.901783</td>
      <td>0.899590</td>
      <td>0.900413</td>
      <td>0.001988</td>
    </tr>
    <tr>
      <th>14</th>
      <td>12.302505</td>
      <td>1.781586</td>
      <td>0.127977</td>
      <td>0.023032</td>
      <td>2</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 2, 'logistic__penalty': 'l2', ...</td>
      <td>0.893610</td>
      <td>0.898709</td>
      <td>0.878416</td>
      <td>0.881756</td>
      <td>0.888094</td>
      <td>0.888117</td>
      <td>0.007443</td>
      <td>25</td>
      <td>0.894469</td>
      <td>0.892913</td>
      <td>0.897664</td>
      <td>0.896557</td>
      <td>0.894084</td>
      <td>0.895137</td>
      <td>0.001727</td>
    </tr>
    <tr>
      <th>15</th>
      <td>13.454204</td>
      <td>1.996481</td>
      <td>0.105238</td>
      <td>0.037208</td>
      <td>2</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 2, 'logistic__penalty': 'l2', ...</td>
      <td>0.898268</td>
      <td>0.902804</td>
      <td>0.878351</td>
      <td>0.886818</td>
      <td>0.887299</td>
      <td>0.890709</td>
      <td>0.008751</td>
      <td>14</td>
      <td>0.899081</td>
      <td>0.897445</td>
      <td>0.903544</td>
      <td>0.901784</td>
      <td>0.899959</td>
      <td>0.900362</td>
      <td>0.002119</td>
    </tr>
    <tr>
      <th>16</th>
      <td>12.951000</td>
      <td>1.979778</td>
      <td>0.093143</td>
      <td>0.010151</td>
      <td>3</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 3, 'logistic__penalty': 'l1', ...</td>
      <td>0.893289</td>
      <td>0.898527</td>
      <td>0.878555</td>
      <td>0.881916</td>
      <td>0.887464</td>
      <td>0.887950</td>
      <td>0.007284</td>
      <td>28</td>
      <td>0.894148</td>
      <td>0.893027</td>
      <td>0.897980</td>
      <td>0.896552</td>
      <td>0.894248</td>
      <td>0.895191</td>
      <td>0.001805</td>
    </tr>
    <tr>
      <th>17</th>
      <td>16.619931</td>
      <td>1.967224</td>
      <td>0.109135</td>
      <td>0.021637</td>
      <td>3</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 3, 'logistic__penalty': 'l1', ...</td>
      <td>0.898628</td>
      <td>0.902376</td>
      <td>0.879450</td>
      <td>0.886585</td>
      <td>0.887318</td>
      <td>0.890872</td>
      <td>0.008414</td>
      <td>9</td>
      <td>0.899131</td>
      <td>0.897616</td>
      <td>0.903484</td>
      <td>0.901767</td>
      <td>0.900087</td>
      <td>0.900417</td>
      <td>0.002042</td>
    </tr>
    <tr>
      <th>18</th>
      <td>14.536846</td>
      <td>0.380587</td>
      <td>0.117486</td>
      <td>0.021496</td>
      <td>3</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 3, 'logistic__penalty': 'l2', ...</td>
      <td>0.893738</td>
      <td>0.899123</td>
      <td>0.879517</td>
      <td>0.882033</td>
      <td>0.887556</td>
      <td>0.888394</td>
      <td>0.007261</td>
      <td>18</td>
      <td>0.894177</td>
      <td>0.893071</td>
      <td>0.898210</td>
      <td>0.896649</td>
      <td>0.894126</td>
      <td>0.895247</td>
      <td>0.001891</td>
    </tr>
    <tr>
      <th>19</th>
      <td>13.380017</td>
      <td>1.889265</td>
      <td>0.095545</td>
      <td>0.035354</td>
      <td>3</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 3, 'logistic__penalty': 'l2', ...</td>
      <td>0.898866</td>
      <td>0.902649</td>
      <td>0.879416</td>
      <td>0.886365</td>
      <td>0.887815</td>
      <td>0.891023</td>
      <td>0.008525</td>
      <td>3</td>
      <td>0.899471</td>
      <td>0.897775</td>
      <td>0.903534</td>
      <td>0.901900</td>
      <td>0.899861</td>
      <td>0.900508</td>
      <td>0.002003</td>
    </tr>
    <tr>
      <th>20</th>
      <td>11.994451</td>
      <td>1.352483</td>
      <td>0.094948</td>
      <td>0.028318</td>
      <td>4</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 4, 'logistic__penalty': 'l1', ...</td>
      <td>0.893966</td>
      <td>0.898911</td>
      <td>0.877446</td>
      <td>0.881802</td>
      <td>0.887219</td>
      <td>0.887869</td>
      <td>0.007810</td>
      <td>30</td>
      <td>0.894261</td>
      <td>0.893171</td>
      <td>0.897827</td>
      <td>0.896871</td>
      <td>0.894177</td>
      <td>0.895261</td>
      <td>0.001773</td>
    </tr>
    <tr>
      <th>21</th>
      <td>16.723633</td>
      <td>3.029306</td>
      <td>0.072407</td>
      <td>0.014462</td>
      <td>4</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 4, 'logistic__penalty': 'l1', ...</td>
      <td>0.898528</td>
      <td>0.902414</td>
      <td>0.879355</td>
      <td>0.886375</td>
      <td>0.887431</td>
      <td>0.890821</td>
      <td>0.008444</td>
      <td>10</td>
      <td>0.899230</td>
      <td>0.897626</td>
      <td>0.903557</td>
      <td>0.901756</td>
      <td>0.900330</td>
      <td>0.900500</td>
      <td>0.002041</td>
    </tr>
    <tr>
      <th>22</th>
      <td>13.356528</td>
      <td>1.939683</td>
      <td>0.080708</td>
      <td>0.020965</td>
      <td>4</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 4, 'logistic__penalty': 'l2', ...</td>
      <td>0.893570</td>
      <td>0.899281</td>
      <td>0.878542</td>
      <td>0.881920</td>
      <td>0.887885</td>
      <td>0.888240</td>
      <td>0.007542</td>
      <td>20</td>
      <td>0.894357</td>
      <td>0.893352</td>
      <td>0.898209</td>
      <td>0.896745</td>
      <td>0.894083</td>
      <td>0.895349</td>
      <td>0.001828</td>
    </tr>
    <tr>
      <th>23</th>
      <td>13.483160</td>
      <td>0.887052</td>
      <td>0.072303</td>
      <td>0.021712</td>
      <td>4</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 4, 'logistic__penalty': 'l2', ...</td>
      <td>0.898560</td>
      <td>0.902273</td>
      <td>0.880646</td>
      <td>0.886212</td>
      <td>0.887150</td>
      <td>0.890969</td>
      <td>0.008114</td>
      <td>6</td>
      <td>0.899205</td>
      <td>0.897528</td>
      <td>0.903465</td>
      <td>0.901573</td>
      <td>0.900341</td>
      <td>0.900422</td>
      <td>0.002022</td>
    </tr>
    <tr>
      <th>24</th>
      <td>13.005043</td>
      <td>0.337982</td>
      <td>0.062641</td>
      <td>0.030045</td>
      <td>5</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 5, 'logistic__penalty': 'l1', ...</td>
      <td>0.893744</td>
      <td>0.898476</td>
      <td>0.878238</td>
      <td>0.882186</td>
      <td>0.887586</td>
      <td>0.888046</td>
      <td>0.007376</td>
      <td>26</td>
      <td>0.894411</td>
      <td>0.893062</td>
      <td>0.898179</td>
      <td>0.896843</td>
      <td>0.894250</td>
      <td>0.895349</td>
      <td>0.001874</td>
    </tr>
    <tr>
      <th>25</th>
      <td>12.976811</td>
      <td>1.922245</td>
      <td>0.077721</td>
      <td>0.020494</td>
      <td>5</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 5, 'logistic__penalty': 'l1', ...</td>
      <td>0.898684</td>
      <td>0.902680</td>
      <td>0.879432</td>
      <td>0.886790</td>
      <td>0.886881</td>
      <td>0.890894</td>
      <td>0.008531</td>
      <td>8</td>
      <td>0.899308</td>
      <td>0.897690</td>
      <td>0.903725</td>
      <td>0.901742</td>
      <td>0.900332</td>
      <td>0.900560</td>
      <td>0.002063</td>
    </tr>
    <tr>
      <th>26</th>
      <td>13.359467</td>
      <td>1.099991</td>
      <td>0.066575</td>
      <td>0.013857</td>
      <td>5</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 5, 'logistic__penalty': 'l2', ...</td>
      <td>0.893511</td>
      <td>0.899640</td>
      <td>0.877654</td>
      <td>0.881537</td>
      <td>0.887154</td>
      <td>0.887900</td>
      <td>0.007942</td>
      <td>29</td>
      <td>0.893813</td>
      <td>0.893291</td>
      <td>0.898381</td>
      <td>0.896782</td>
      <td>0.893886</td>
      <td>0.895230</td>
      <td>0.001996</td>
    </tr>
    <tr>
      <th>27</th>
      <td>18.301420</td>
      <td>2.926647</td>
      <td>0.069415</td>
      <td>0.011399</td>
      <td>5</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 5, 'logistic__penalty': 'l2', ...</td>
      <td>0.898790</td>
      <td>0.902698</td>
      <td>0.879715</td>
      <td>0.885569</td>
      <td>0.887328</td>
      <td>0.890820</td>
      <td>0.008576</td>
      <td>11</td>
      <td>0.899473</td>
      <td>0.897398</td>
      <td>0.903409</td>
      <td>0.901805</td>
      <td>0.900378</td>
      <td>0.900493</td>
      <td>0.002042</td>
    </tr>
    <tr>
      <th>28</th>
      <td>13.718045</td>
      <td>2.878132</td>
      <td>0.083402</td>
      <td>0.010016</td>
      <td>10</td>
      <td>l1</td>
      <td>60</td>
      <td>{'logistic__C': 10, 'logistic__penalty': 'l1',...</td>
      <td>0.893552</td>
      <td>0.899799</td>
      <td>0.878114</td>
      <td>0.881440</td>
      <td>0.887733</td>
      <td>0.888128</td>
      <td>0.007884</td>
      <td>24</td>
      <td>0.894107</td>
      <td>0.892989</td>
      <td>0.897929</td>
      <td>0.896469</td>
      <td>0.894097</td>
      <td>0.895118</td>
      <td>0.001807</td>
    </tr>
    <tr>
      <th>29</th>
      <td>15.753566</td>
      <td>3.101451</td>
      <td>0.057845</td>
      <td>0.011195</td>
      <td>10</td>
      <td>l1</td>
      <td>80</td>
      <td>{'logistic__C': 10, 'logistic__penalty': 'l1',...</td>
      <td>0.899132</td>
      <td>0.903060</td>
      <td>0.879106</td>
      <td>0.886311</td>
      <td>0.887259</td>
      <td>0.890974</td>
      <td>0.008821</td>
      <td>5</td>
      <td>0.899526</td>
      <td>0.897728</td>
      <td>0.903472</td>
      <td>0.901738</td>
      <td>0.899985</td>
      <td>0.900490</td>
      <td>0.001963</td>
    </tr>
    <tr>
      <th>30</th>
      <td>15.261619</td>
      <td>1.881416</td>
      <td>0.095370</td>
      <td>0.018967</td>
      <td>10</td>
      <td>l2</td>
      <td>60</td>
      <td>{'logistic__C': 10, 'logistic__penalty': 'l2',...</td>
      <td>0.894180</td>
      <td>0.898879</td>
      <td>0.878283</td>
      <td>0.881726</td>
      <td>0.887941</td>
      <td>0.888202</td>
      <td>0.007618</td>
      <td>22</td>
      <td>0.894552</td>
      <td>0.893295</td>
      <td>0.898006</td>
      <td>0.896677</td>
      <td>0.894319</td>
      <td>0.895370</td>
      <td>0.001717</td>
    </tr>
    <tr>
      <th>31</th>
      <td>12.812690</td>
      <td>4.119737</td>
      <td>0.078192</td>
      <td>0.011503</td>
      <td>10</td>
      <td>l2</td>
      <td>80</td>
      <td>{'logistic__C': 10, 'logistic__penalty': 'l2',...</td>
      <td>0.898581</td>
      <td>0.902501</td>
      <td>0.880538</td>
      <td>0.886811</td>
      <td>0.887148</td>
      <td>0.891116</td>
      <td>0.008143</td>
      <td>2</td>
      <td>0.899398</td>
      <td>0.897750</td>
      <td>0.903282</td>
      <td>0.901800</td>
      <td>0.900202</td>
      <td>0.900486</td>
      <td>0.001913</td>
    </tr>
  </tbody>
</table>
</div>




```python
# print best hyperparameters
print("Best AUC: ", model.best_score_)
print("Best hyperparameters: ", model.best_params_)
```

    Best AUC:  0.8911594701125283
    Best hyperparameters:  {'logistic__C': 0.5, 'logistic__penalty': 'l1', 'pca__n_components': 80}



```python
# predict churn on test data
y_pred = model.predict(X_test)

# create onfusion matrix
cm = confusion_matrix(y_test, y_pred)
print(cm)

# check sensitivity and specificity
sensitivity, specificity, _ = sensitivity_specificity_support(y_test, y_pred, average='binary')
print("Sensitivity: \t", round(sensitivity, 2), "\n", "Specificity: \t", round(specificity, 2), sep='')

# check area under curve
y_pred_prob = model.predict_proba(X_test)[:, 1]
print("AUC:    \t", round(roc_auc_score(y_test, y_pred_prob),2))
```

    [[5864 1027]
     [ 107  503]]
    Sensitivity: 	0.82
    Specificity: 	0.85
    AUC:    	 0.91


### Random Forest


```python
# random forest - the class weight is used to handle class imbalance - it adjusts the cost function
forest = RandomForestClassifier(class_weight={0:0.1, 1: 0.9}, n_jobs = -1)

# hyperparameter space
params = {"criterion": ['gini', 'entropy'], "max_features": ['auto', 0.4]}

# create 5 folds
folds = StratifiedKFold(n_splits = 5, shuffle = True, random_state = 4)

# create gridsearch object
model = GridSearchCV(estimator=forest, cv=folds, param_grid=params, scoring='roc_auc', n_jobs=-1, verbose=1)
```


```python
# fit model
model.fit(X_train, y_train)
```

    Fitting 5 folds for each of 4 candidates, totalling 20 fits


    [Parallel(n_jobs=-1)]: Done  20 out of  20 | elapsed:   51.8s finished





    GridSearchCV(cv=StratifiedKFold(n_splits=5, random_state=4, shuffle=True),
           error_score='raise',
           estimator=RandomForestClassifier(bootstrap=True, class_weight={0: 0.1, 1: 0.9},
                criterion='gini', max_depth=None, max_features='auto',
                max_leaf_nodes=None, min_impurity_decrease=0.0,
                min_impurity_split=None, min_samples_leaf=1,
                min_samples_split=2, min_weight_fraction_leaf=0.0,
                n_estimators=10, n_jobs=-1, oob_score=False, random_state=None,
                verbose=0, warm_start=False),
           fit_params=None, iid=True, n_jobs=-1,
           param_grid={'criterion': ['gini', 'entropy'], 'max_features': ['auto', 0.4]},
           pre_dispatch='2*n_jobs', refit=True, return_train_score='warn',
           scoring='roc_auc', verbose=1)




```python
# print best hyperparameters
print("Best AUC: ", model.best_score_)
print("Best hyperparameters: ", model.best_params_)
```

    Best AUC:  0.8821281027498742
    Best hyperparameters:  {'criterion': 'entropy', 'max_features': 0.4}



```python
# predict churn on test data
y_pred = model.predict(X_test)

# create onfusion matrix
cm = confusion_matrix(y_test, y_pred)
print(cm)

# check sensitivity and specificity
sensitivity, specificity, _ = sensitivity_specificity_support(y_test, y_pred, average='binary')
print("Sensitivity: \t", round(sensitivity, 2), "\n", "Specificity: \t", round(specificity, 2), sep='')

# check area under curve
y_pred_prob = model.predict_proba(X_test)[:, 1]
print("AUC:    \t", round(roc_auc_score(y_test, y_pred_prob),2))
```

    [[6771  120]
     [ 328  282]]
    Sensitivity: 	0.46
    Specificity: 	0.98
    AUC:    	 0.89


Poor sensitivity. The best model is PCA along with Logistic regression.

## ii) Choosing best features


```python
# run a random forest model on train data
max_features = int(round(np.sqrt(X_train.shape[1])))    # number of variables to consider to split each node
print(max_features)

rf_model = RandomForestClassifier(n_estimators=100, max_features=max_features, class_weight={0:0.1, 1: 0.9}, oob_score=True, random_state=4, verbose=1)
```

    13



```python
# fit model
rf_model.fit(X_train, y_train)
```

    [Parallel(n_jobs=1)]: Done 100 out of 100 | elapsed:   28.4s finished





    RandomForestClassifier(bootstrap=True, class_weight={0: 0.1, 1: 0.9},
                criterion='gini', max_depth=None, max_features=13,
                max_leaf_nodes=None, min_impurity_decrease=0.0,
                min_impurity_split=None, min_samples_leaf=1,
                min_samples_split=2, min_weight_fraction_leaf=0.0,
                n_estimators=100, n_jobs=1, oob_score=True, random_state=4,
                verbose=1, warm_start=False)




```python
# OOB score
rf_model.oob_score_
```




    0.9426666666666667




```python
# predict churn on test data
y_pred = rf_model.predict(X_test)

# create onfusion matrix
cm = confusion_matrix(y_test, y_pred)
print(cm)

# check sensitivity and specificity
sensitivity, specificity, _ = sensitivity_specificity_support(y_test, y_pred, average='binary')
print("Sensitivity: \t", round(sensitivity, 2), "\n", "Specificity: \t", round(specificity, 2), sep='')

# check area under curve
y_pred_prob = rf_model.predict_proba(X_test)[:, 1]
print("ROC:    \t", round(roc_auc_score(y_test, y_pred_prob),2))
```

    [Parallel(n_jobs=1)]: Done 100 out of 100 | elapsed:    0.3s finished


    [[6792   99]
     [ 329  281]]
    Sensitivity: 	0.46
    Specificity: 	0.99
    ROC:    	 0.93


    [Parallel(n_jobs=1)]: Done 100 out of 100 | elapsed:    0.3s finished


### Feature Importance


```python
# predictors
features = churn_filtered.drop('churn', axis=1).columns

# feature_importance
importance = rf_model.feature_importances_

# create dataframe
feature_importance = pd.DataFrame({'variables': features, 'importance_percentage': importance*100})
feature_importance = feature_importance[['variables', 'importance_percentage']]

# sort features
feature_importance = feature_importance.sort_values('importance_percentage', ascending=False).reset_index(drop=True)
print("Sum of importance=", feature_importance.importance_percentage.sum())
feature_importance
```

    Sum of importance= 99.99999999999999





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
      <th>variables</th>
      <th>importance_percentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>total_ic_mou_8</td>
      <td>7.051799</td>
    </tr>
    <tr>
      <th>1</th>
      <td>total_og_mou_8</td>
      <td>4.029977</td>
    </tr>
    <tr>
      <th>2</th>
      <td>last_day_rch_amt_8</td>
      <td>3.217914</td>
    </tr>
    <tr>
      <th>3</th>
      <td>arpu_8</td>
      <td>3.112591</td>
    </tr>
    <tr>
      <th>4</th>
      <td>total_rech_amt_diff</td>
      <td>2.908439</td>
    </tr>
    <tr>
      <th>5</th>
      <td>loc_ic_mou_8</td>
      <td>2.801836</td>
    </tr>
    <tr>
      <th>6</th>
      <td>roam_og_mou_8</td>
      <td>2.618070</td>
    </tr>
    <tr>
      <th>7</th>
      <td>loc_ic_t2m_mou_8</td>
      <td>2.574123</td>
    </tr>
    <tr>
      <th>8</th>
      <td>max_rech_amt_8</td>
      <td>2.565527</td>
    </tr>
    <tr>
      <th>9</th>
      <td>total_rech_amt_8</td>
      <td>2.479779</td>
    </tr>
    <tr>
      <th>10</th>
      <td>arpu_diff</td>
      <td>2.433597</td>
    </tr>
    <tr>
      <th>11</th>
      <td>roam_ic_mou_8</td>
      <td>2.313062</td>
    </tr>
    <tr>
      <th>12</th>
      <td>loc_ic_t2t_mou_8</td>
      <td>2.272950</td>
    </tr>
    <tr>
      <th>13</th>
      <td>total_rech_num_diff</td>
      <td>1.684547</td>
    </tr>
    <tr>
      <th>14</th>
      <td>total_ic_mou_diff</td>
      <td>1.616509</td>
    </tr>
    <tr>
      <th>15</th>
      <td>total_og_mou_diff</td>
      <td>1.515810</td>
    </tr>
    <tr>
      <th>16</th>
      <td>loc_og_mou_8</td>
      <td>1.407685</td>
    </tr>
    <tr>
      <th>17</th>
      <td>av_rech_amt_data_8</td>
      <td>1.341360</td>
    </tr>
    <tr>
      <th>18</th>
      <td>std_og_mou_diff</td>
      <td>1.297516</td>
    </tr>
    <tr>
      <th>19</th>
      <td>roam_ic_mou_diff</td>
      <td>1.295492</td>
    </tr>
    <tr>
      <th>20</th>
      <td>loc_ic_mou_diff</td>
      <td>1.231582</td>
    </tr>
    <tr>
      <th>21</th>
      <td>roam_og_mou_diff</td>
      <td>1.196602</td>
    </tr>
    <tr>
      <th>22</th>
      <td>loc_og_t2m_mou_8</td>
      <td>0.927088</td>
    </tr>
    <tr>
      <th>23</th>
      <td>loc_og_t2t_mou_8</td>
      <td>0.918190</td>
    </tr>
    <tr>
      <th>24</th>
      <td>offnet_mou_8</td>
      <td>0.835193</td>
    </tr>
    <tr>
      <th>25</th>
      <td>offnet_mou_diff</td>
      <td>0.787708</td>
    </tr>
    <tr>
      <th>26</th>
      <td>vol_2g_mb_8</td>
      <td>0.767465</td>
    </tr>
    <tr>
      <th>27</th>
      <td>std_ic_mou_8</td>
      <td>0.756777</td>
    </tr>
    <tr>
      <th>28</th>
      <td>total_ic_mou_7</td>
      <td>0.755680</td>
    </tr>
    <tr>
      <th>29</th>
      <td>std_og_t2m_mou_8</td>
      <td>0.750015</td>
    </tr>
    <tr>
      <th>30</th>
      <td>max_rech_amt_diff</td>
      <td>0.727545</td>
    </tr>
    <tr>
      <th>31</th>
      <td>fb_user_8</td>
      <td>0.726221</td>
    </tr>
    <tr>
      <th>32</th>
      <td>night_pck_user_8</td>
      <td>0.693271</td>
    </tr>
    <tr>
      <th>33</th>
      <td>onnet_mou_diff</td>
      <td>0.682034</td>
    </tr>
    <tr>
      <th>34</th>
      <td>aon</td>
      <td>0.657394</td>
    </tr>
    <tr>
      <th>35</th>
      <td>max_rech_data_8</td>
      <td>0.614868</td>
    </tr>
    <tr>
      <th>36</th>
      <td>loc_og_mou_diff</td>
      <td>0.606564</td>
    </tr>
    <tr>
      <th>37</th>
      <td>std_og_mou_8</td>
      <td>0.593622</td>
    </tr>
    <tr>
      <th>38</th>
      <td>onnet_mou_8</td>
      <td>0.575225</td>
    </tr>
    <tr>
      <th>39</th>
      <td>total_rech_amt_7</td>
      <td>0.528601</td>
    </tr>
    <tr>
      <th>40</th>
      <td>loc_ic_t2m_mou_6</td>
      <td>0.518464</td>
    </tr>
    <tr>
      <th>41</th>
      <td>total_rech_data_8</td>
      <td>0.518115</td>
    </tr>
    <tr>
      <th>42</th>
      <td>arpu_7</td>
      <td>0.512462</td>
    </tr>
    <tr>
      <th>43</th>
      <td>std_ic_mou_diff</td>
      <td>0.502147</td>
    </tr>
    <tr>
      <th>44</th>
      <td>std_og_mou_7</td>
      <td>0.492795</td>
    </tr>
    <tr>
      <th>45</th>
      <td>loc_og_mou_7</td>
      <td>0.491933</td>
    </tr>
    <tr>
      <th>46</th>
      <td>total_rech_num_8</td>
      <td>0.488850</td>
    </tr>
    <tr>
      <th>47</th>
      <td>total_ic_mou_6</td>
      <td>0.473363</td>
    </tr>
    <tr>
      <th>48</th>
      <td>loc_ic_t2m_mou_7</td>
      <td>0.466724</td>
    </tr>
    <tr>
      <th>49</th>
      <td>total_og_mou_7</td>
      <td>0.465682</td>
    </tr>
    <tr>
      <th>50</th>
      <td>loc_og_t2m_mou_6</td>
      <td>0.465483</td>
    </tr>
    <tr>
      <th>51</th>
      <td>loc_ic_mou_7</td>
      <td>0.463715</td>
    </tr>
    <tr>
      <th>52</th>
      <td>vol_2g_mb_diff</td>
      <td>0.461875</td>
    </tr>
    <tr>
      <th>53</th>
      <td>arpu_6</td>
      <td>0.459183</td>
    </tr>
    <tr>
      <th>54</th>
      <td>std_og_t2t_mou_8</td>
      <td>0.457876</td>
    </tr>
    <tr>
      <th>55</th>
      <td>vol_3g_mb_8</td>
      <td>0.454195</td>
    </tr>
    <tr>
      <th>56</th>
      <td>spl_og_mou_diff</td>
      <td>0.445280</td>
    </tr>
    <tr>
      <th>57</th>
      <td>offnet_mou_6</td>
      <td>0.445082</td>
    </tr>
    <tr>
      <th>58</th>
      <td>loc_ic_t2t_mou_7</td>
      <td>0.444555</td>
    </tr>
    <tr>
      <th>59</th>
      <td>av_rech_amt_data_diff</td>
      <td>0.443252</td>
    </tr>
    <tr>
      <th>60</th>
      <td>offnet_mou_7</td>
      <td>0.441294</td>
    </tr>
    <tr>
      <th>61</th>
      <td>loc_ic_mou_6</td>
      <td>0.438766</td>
    </tr>
    <tr>
      <th>62</th>
      <td>loc_og_t2m_mou_7</td>
      <td>0.433585</td>
    </tr>
    <tr>
      <th>63</th>
      <td>loc_og_mou_6</td>
      <td>0.427759</td>
    </tr>
    <tr>
      <th>64</th>
      <td>max_rech_data_diff</td>
      <td>0.421121</td>
    </tr>
    <tr>
      <th>65</th>
      <td>loc_og_t2t_mou_7</td>
      <td>0.420918</td>
    </tr>
    <tr>
      <th>66</th>
      <td>loc_ic_t2t_mou_6</td>
      <td>0.417714</td>
    </tr>
    <tr>
      <th>67</th>
      <td>total_rech_amt_6</td>
      <td>0.416888</td>
    </tr>
    <tr>
      <th>68</th>
      <td>onnet_mou_7</td>
      <td>0.397039</td>
    </tr>
    <tr>
      <th>69</th>
      <td>total_rech_num_7</td>
      <td>0.395627</td>
    </tr>
    <tr>
      <th>70</th>
      <td>std_ic_t2t_mou_8</td>
      <td>0.381641</td>
    </tr>
    <tr>
      <th>71</th>
      <td>std_ic_t2m_mou_8</td>
      <td>0.377689</td>
    </tr>
    <tr>
      <th>72</th>
      <td>total_rech_num_6</td>
      <td>0.370274</td>
    </tr>
    <tr>
      <th>73</th>
      <td>std_og_mou_6</td>
      <td>0.369188</td>
    </tr>
    <tr>
      <th>74</th>
      <td>std_ic_mou_6</td>
      <td>0.366826</td>
    </tr>
    <tr>
      <th>75</th>
      <td>loc_og_t2t_mou_6</td>
      <td>0.366003</td>
    </tr>
    <tr>
      <th>76</th>
      <td>std_ic_t2m_mou_7</td>
      <td>0.356541</td>
    </tr>
    <tr>
      <th>77</th>
      <td>isd_ic_mou_diff</td>
      <td>0.354723</td>
    </tr>
    <tr>
      <th>78</th>
      <td>onnet_mou_6</td>
      <td>0.351645</td>
    </tr>
    <tr>
      <th>79</th>
      <td>loc_ic_t2f_mou_8</td>
      <td>0.348421</td>
    </tr>
    <tr>
      <th>80</th>
      <td>roam_ic_mou_7</td>
      <td>0.347550</td>
    </tr>
    <tr>
      <th>81</th>
      <td>spl_ic_mou_diff</td>
      <td>0.340279</td>
    </tr>
    <tr>
      <th>82</th>
      <td>std_og_t2m_mou_7</td>
      <td>0.339827</td>
    </tr>
    <tr>
      <th>83</th>
      <td>vol_3g_mb_diff</td>
      <td>0.338704</td>
    </tr>
    <tr>
      <th>84</th>
      <td>total_og_mou_6</td>
      <td>0.336792</td>
    </tr>
    <tr>
      <th>85</th>
      <td>std_og_t2m_mou_6</td>
      <td>0.336494</td>
    </tr>
    <tr>
      <th>86</th>
      <td>std_og_t2t_mou_7</td>
      <td>0.332075</td>
    </tr>
    <tr>
      <th>87</th>
      <td>aug_vbc_3g</td>
      <td>0.328900</td>
    </tr>
    <tr>
      <th>88</th>
      <td>loc_ic_t2f_mou_7</td>
      <td>0.328640</td>
    </tr>
    <tr>
      <th>89</th>
      <td>std_ic_mou_7</td>
      <td>0.324208</td>
    </tr>
    <tr>
      <th>90</th>
      <td>spl_og_mou_7</td>
      <td>0.316932</td>
    </tr>
    <tr>
      <th>91</th>
      <td>std_og_t2t_mou_6</td>
      <td>0.315337</td>
    </tr>
    <tr>
      <th>92</th>
      <td>max_rech_amt_7</td>
      <td>0.313147</td>
    </tr>
    <tr>
      <th>93</th>
      <td>isd_ic_mou_8</td>
      <td>0.308535</td>
    </tr>
    <tr>
      <th>94</th>
      <td>loc_og_t2f_mou_8</td>
      <td>0.307020</td>
    </tr>
    <tr>
      <th>95</th>
      <td>std_ic_t2m_mou_6</td>
      <td>0.303577</td>
    </tr>
    <tr>
      <th>96</th>
      <td>total_rech_data_diff</td>
      <td>0.303365</td>
    </tr>
    <tr>
      <th>97</th>
      <td>max_rech_amt_6</td>
      <td>0.293195</td>
    </tr>
    <tr>
      <th>98</th>
      <td>loc_ic_t2f_mou_6</td>
      <td>0.290351</td>
    </tr>
    <tr>
      <th>99</th>
      <td>spl_og_mou_6</td>
      <td>0.288099</td>
    </tr>
    <tr>
      <th>100</th>
      <td>roam_og_mou_7</td>
      <td>0.285888</td>
    </tr>
    <tr>
      <th>101</th>
      <td>last_day_rch_amt_6</td>
      <td>0.278386</td>
    </tr>
    <tr>
      <th>102</th>
      <td>last_day_rch_amt_7</td>
      <td>0.276803</td>
    </tr>
    <tr>
      <th>103</th>
      <td>av_rech_amt_data_7</td>
      <td>0.275718</td>
    </tr>
    <tr>
      <th>104</th>
      <td>loc_og_t2f_mou_6</td>
      <td>0.269368</td>
    </tr>
    <tr>
      <th>105</th>
      <td>spl_og_mou_8</td>
      <td>0.266655</td>
    </tr>
    <tr>
      <th>106</th>
      <td>std_ic_t2t_mou_6</td>
      <td>0.266636</td>
    </tr>
    <tr>
      <th>107</th>
      <td>loc_og_t2f_mou_7</td>
      <td>0.263393</td>
    </tr>
    <tr>
      <th>108</th>
      <td>vol_2g_mb_6</td>
      <td>0.257802</td>
    </tr>
    <tr>
      <th>109</th>
      <td>std_ic_t2t_mou_7</td>
      <td>0.254425</td>
    </tr>
    <tr>
      <th>110</th>
      <td>vol_3g_mb_7</td>
      <td>0.243538</td>
    </tr>
    <tr>
      <th>111</th>
      <td>vol_2g_mb_7</td>
      <td>0.240131</td>
    </tr>
    <tr>
      <th>112</th>
      <td>av_rech_amt_data_6</td>
      <td>0.236701</td>
    </tr>
    <tr>
      <th>113</th>
      <td>roam_og_mou_6</td>
      <td>0.233235</td>
    </tr>
    <tr>
      <th>114</th>
      <td>roam_ic_mou_6</td>
      <td>0.228482</td>
    </tr>
    <tr>
      <th>115</th>
      <td>og_others_6</td>
      <td>0.227395</td>
    </tr>
    <tr>
      <th>116</th>
      <td>vol_3g_mb_6</td>
      <td>0.218148</td>
    </tr>
    <tr>
      <th>117</th>
      <td>max_rech_data_7</td>
      <td>0.214674</td>
    </tr>
    <tr>
      <th>118</th>
      <td>loc_og_t2c_mou_8</td>
      <td>0.210770</td>
    </tr>
    <tr>
      <th>119</th>
      <td>isd_ic_mou_6</td>
      <td>0.205554</td>
    </tr>
    <tr>
      <th>120</th>
      <td>jul_vbc_3g</td>
      <td>0.204624</td>
    </tr>
    <tr>
      <th>121</th>
      <td>isd_og_mou_diff</td>
      <td>0.204362</td>
    </tr>
    <tr>
      <th>122</th>
      <td>spl_ic_mou_6</td>
      <td>0.201601</td>
    </tr>
    <tr>
      <th>123</th>
      <td>ic_others_7</td>
      <td>0.199106</td>
    </tr>
    <tr>
      <th>124</th>
      <td>std_ic_t2f_mou_8</td>
      <td>0.191354</td>
    </tr>
    <tr>
      <th>125</th>
      <td>spl_ic_mou_8</td>
      <td>0.186443</td>
    </tr>
    <tr>
      <th>126</th>
      <td>isd_ic_mou_7</td>
      <td>0.186243</td>
    </tr>
    <tr>
      <th>127</th>
      <td>std_ic_t2f_mou_7</td>
      <td>0.180216</td>
    </tr>
    <tr>
      <th>128</th>
      <td>jun_vbc_3g</td>
      <td>0.178941</td>
    </tr>
    <tr>
      <th>129</th>
      <td>ic_others_8</td>
      <td>0.176169</td>
    </tr>
    <tr>
      <th>130</th>
      <td>ic_others_6</td>
      <td>0.176027</td>
    </tr>
    <tr>
      <th>131</th>
      <td>loc_og_t2c_mou_6</td>
      <td>0.172089</td>
    </tr>
    <tr>
      <th>132</th>
      <td>sep_vbc_3g</td>
      <td>0.171285</td>
    </tr>
    <tr>
      <th>133</th>
      <td>max_rech_data_6</td>
      <td>0.170704</td>
    </tr>
    <tr>
      <th>134</th>
      <td>loc_og_t2c_mou_7</td>
      <td>0.164413</td>
    </tr>
    <tr>
      <th>135</th>
      <td>total_rech_data_7</td>
      <td>0.150091</td>
    </tr>
    <tr>
      <th>136</th>
      <td>std_ic_t2f_mou_6</td>
      <td>0.146022</td>
    </tr>
    <tr>
      <th>137</th>
      <td>isd_og_mou_6</td>
      <td>0.145912</td>
    </tr>
    <tr>
      <th>138</th>
      <td>std_ic_t2o_mou_8</td>
      <td>0.139639</td>
    </tr>
    <tr>
      <th>139</th>
      <td>std_og_t2f_mou_7</td>
      <td>0.137777</td>
    </tr>
    <tr>
      <th>140</th>
      <td>isd_og_mou_7</td>
      <td>0.126929</td>
    </tr>
    <tr>
      <th>141</th>
      <td>total_rech_data_6</td>
      <td>0.124994</td>
    </tr>
    <tr>
      <th>142</th>
      <td>og_others_8</td>
      <td>0.117843</td>
    </tr>
    <tr>
      <th>143</th>
      <td>spl_ic_mou_7</td>
      <td>0.114016</td>
    </tr>
    <tr>
      <th>144</th>
      <td>sachet_2g_7</td>
      <td>0.108001</td>
    </tr>
    <tr>
      <th>145</th>
      <td>isd_og_mou_8</td>
      <td>0.105353</td>
    </tr>
    <tr>
      <th>146</th>
      <td>sachet_2g_8</td>
      <td>0.101112</td>
    </tr>
    <tr>
      <th>147</th>
      <td>std_og_t2f_mou_6</td>
      <td>0.098533</td>
    </tr>
    <tr>
      <th>148</th>
      <td>sachet_2g_6</td>
      <td>0.087329</td>
    </tr>
    <tr>
      <th>149</th>
      <td>std_og_t2f_mou_8</td>
      <td>0.083208</td>
    </tr>
    <tr>
      <th>150</th>
      <td>sachet_3g_7</td>
      <td>0.082937</td>
    </tr>
    <tr>
      <th>151</th>
      <td>sachet_3g_6</td>
      <td>0.078567</td>
    </tr>
    <tr>
      <th>152</th>
      <td>monthly_2g_7</td>
      <td>0.058376</td>
    </tr>
    <tr>
      <th>153</th>
      <td>monthly_3g_6</td>
      <td>0.055064</td>
    </tr>
    <tr>
      <th>154</th>
      <td>fb_user_7</td>
      <td>0.053158</td>
    </tr>
    <tr>
      <th>155</th>
      <td>monthly_3g_7</td>
      <td>0.052559</td>
    </tr>
    <tr>
      <th>156</th>
      <td>night_pck_user_7</td>
      <td>0.051557</td>
    </tr>
    <tr>
      <th>157</th>
      <td>monthly_3g_8</td>
      <td>0.050323</td>
    </tr>
    <tr>
      <th>158</th>
      <td>std_og_t2c_mou_6</td>
      <td>0.049699</td>
    </tr>
    <tr>
      <th>159</th>
      <td>sachet_3g_8</td>
      <td>0.047272</td>
    </tr>
    <tr>
      <th>160</th>
      <td>og_others_7</td>
      <td>0.045714</td>
    </tr>
    <tr>
      <th>161</th>
      <td>std_og_t2c_mou_8</td>
      <td>0.040714</td>
    </tr>
    <tr>
      <th>162</th>
      <td>night_pck_user_6</td>
      <td>0.039921</td>
    </tr>
    <tr>
      <th>163</th>
      <td>monthly_2g_6</td>
      <td>0.039866</td>
    </tr>
    <tr>
      <th>164</th>
      <td>fb_user_6</td>
      <td>0.039001</td>
    </tr>
    <tr>
      <th>165</th>
      <td>monthly_2g_8</td>
      <td>0.033863</td>
    </tr>
    <tr>
      <th>166</th>
      <td>std_ic_t2o_mou_6</td>
      <td>0.029129</td>
    </tr>
    <tr>
      <th>167</th>
      <td>std_ic_t2o_mou_7</td>
      <td>0.019845</td>
    </tr>
    <tr>
      <th>168</th>
      <td>std_og_t2o_mou</td>
      <td>0.015844</td>
    </tr>
    <tr>
      <th>169</th>
      <td>loc_og_t2o_mou</td>
      <td>0.011197</td>
    </tr>
    <tr>
      <th>170</th>
      <td>std_og_t2c_mou_7</td>
      <td>0.006985</td>
    </tr>
    <tr>
      <th>171</th>
      <td>loc_ic_t2o_mou</td>
      <td>0.006427</td>
    </tr>
  </tbody>
</table>
</div>



### Extracting top 30 features


```python
# extract top 'n' features
top_n = 30
top_features = feature_importance.variables[0:top_n]
```


```python
# plot feature correlation
import seaborn as sns
plt.rcParams["figure.figsize"] =(10,10)
mycmap = sns.diverging_palette(199, 359, s=99, center="light", as_cmap=True)
sns.heatmap(data=X_train[top_features].corr(), center=0.0, cmap=mycmap)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x2b602a162e8>




    
![png](solution_telecom_churn_files/solution_telecom_churn_118_1.png)
    



```python
top_features = ['total_ic_mou_8', 'total_rech_amt_diff', 'total_og_mou_8', 'arpu_8', 'roam_ic_mou_8', 'roam_og_mou_8', 
                'std_ic_mou_8', 'av_rech_amt_data_8', 'std_og_mou_8']
X_train = X_train[top_features]
X_test = X_test[top_features]
```


```python
# logistic regression
steps = [('scaler', StandardScaler()), 
         ("logistic", LogisticRegression(class_weight={0:0.1, 1:0.9}))
        ]

# compile pipeline
logistic = Pipeline(steps)

# hyperparameter space
params = {'logistic__C': [0.1, 0.5, 1, 2, 3, 4, 5, 10], 'logistic__penalty': ['l1', 'l2']}

# create 5 folds
folds = StratifiedKFold(n_splits = 5, shuffle = True, random_state = 4)

# create gridsearch object
model = GridSearchCV(estimator=logistic, cv=folds, param_grid=params, scoring='roc_auc', n_jobs=-1, verbose=1)
```


```python
# fit model
model.fit(X_train, y_train)
```

    Fitting 5 folds for each of 16 candidates, totalling 80 fits


    [Parallel(n_jobs=-1)]: Done  42 tasks      | elapsed:   10.1s
    [Parallel(n_jobs=-1)]: Done  80 out of  80 | elapsed:   14.2s finished





    GridSearchCV(cv=StratifiedKFold(n_splits=5, random_state=4, shuffle=True),
           error_score='raise',
           estimator=Pipeline(memory=None,
         steps=[('scaler', StandardScaler(copy=True, with_mean=True, with_std=True)), ('logistic', LogisticRegression(C=1.0, class_weight={0: 0.1, 1: 0.9}, dual=False,
              fit_intercept=True, intercept_scaling=1, max_iter=100,
              multi_class='ovr', n_jobs=1, penalty='l2', random_state=None,
              solver='liblinear', tol=0.0001, verbose=0, warm_start=False))]),
           fit_params=None, iid=True, n_jobs=-1,
           param_grid={'logistic__C': [0.1, 0.5, 1, 2, 3, 4, 5, 10], 'logistic__penalty': ['l1', 'l2']},
           pre_dispatch='2*n_jobs', refit=True, return_train_score='warn',
           scoring='roc_auc', verbose=1)




```python
# print best hyperparameters
print("Best AUC: ", model.best_score_)
print("Best hyperparameters: ", model.best_params_)
```

    Best AUC:  0.8728895343145171
    Best hyperparameters:  {'logistic__C': 10, 'logistic__penalty': 'l1'}



```python
# predict churn on test data
y_pred = model.predict(X_test)

# create onfusion matrix
cm = confusion_matrix(y_test, y_pred)
print(cm)

# check sensitivity and specificity
sensitivity, specificity, _ = sensitivity_specificity_support(y_test, y_pred, average='binary')
print("Sensitivity: \t", round(sensitivity, 2), "\n", "Specificity: \t", round(specificity, 2), sep='')

# check area under curve
y_pred_prob = model.predict_proba(X_test)[:, 1]
print("ROC:    \t", round(roc_auc_score(y_test, y_pred_prob),2))
```

    [[5758 1133]
     [ 121  489]]
    Sensitivity: 	0.8
    Specificity: 	0.84
    ROC:    	 0.88


### Extract the intercept and the coefficients from the logistic model 


```python
logistic_model = model.best_estimator_.named_steps['logistic']
```


```python
# intercept
intercept_df = pd.DataFrame(logistic_model.intercept_.reshape((1,1)), columns = ['intercept'])
```


```python
# coefficients
coefficients = logistic_model.coef_.reshape((9, 1)).tolist()
coefficients = [val for sublist in coefficients for val in sublist]
coefficients = [round(coefficient, 3) for coefficient in coefficients]

logistic_features = list(X_train.columns)
coefficients_df = pd.DataFrame(logistic_model.coef_, columns=logistic_features)
```


```python
# concatenate dataframes
coefficients = pd.concat([intercept_df, coefficients_df], axis=1)
coefficients
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
      <th>intercept</th>
      <th>total_ic_mou_8</th>
      <th>total_rech_amt_diff</th>
      <th>total_og_mou_8</th>
      <th>arpu_8</th>
      <th>roam_ic_mou_8</th>
      <th>roam_og_mou_8</th>
      <th>std_ic_mou_8</th>
      <th>av_rech_amt_data_8</th>
      <th>std_og_mou_8</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.46353</td>
      <td>-1.191866</td>
      <td>-0.684758</td>
      <td>-1.096099</td>
      <td>0.179667</td>
      <td>0.066651</td>
      <td>0.16906</td>
      <td>0.025026</td>
      <td>-0.795034</td>
      <td>0.58883</td>
    </tr>
  </tbody>
</table>
</div>



## Business Insights

* Telecom company needs to pay attention to the roaming rates. They need to provide good offers to the customers who are using services from a roaming zone.
* The company needs to focus on the STD and ISD rates. Perhaps, the rates are too high. Provide them with some kind of STD and ISD packages.
* To look into both of the issues stated above, it is desired that the telecom company collects customer query and complaint data and work on their services according to the needs of customers. 


```python

```
