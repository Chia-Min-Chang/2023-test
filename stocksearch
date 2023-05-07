import streamlit as st
import pandas as pd
import altair as alt

# read data, 讀取資料
df=pd.read_csv("data/TWSE_TW-1.csv")
df.fillna('', inplace=True)

# set up Streamlit app, 建立應用程式
st.title("TWSE Stock Search, 台灣股票代號查詢")

# add search box and dropdown, 增加搜尋選擇欄位
search_term = st.text_input("Enter search term, 輸入查詢資料:")
search_by = st.selectbox("Search by column:", options=['Symbol 公司代碼', 'Name 公司名稱'])

# search for matching rows, 搜尋並列印結果
if search_term:
    if search_by == 'Symbol 公司代碼':
        result = df[df['Symbol'].str.contains(search_term)]
    elif search_by == 'Name 公司名稱':
        result = df[df['Name'].str.contains(search_term)]
    else:
        result = pd.DataFrame()
    
    # show the search result as a chart, 顯示圖表
    chart = alt.Chart(result).mark_bar().encode(
        x='Symbol',
        y='Price'
    ).properties(
        width=600,
        height=400
    )
    
    st.write('Search ',search_term,' by ', search_by )
    st.altair_chart(chart, use_container_width=True)
    st.write(result)
