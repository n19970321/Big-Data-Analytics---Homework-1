# CS5124701-Homework-1

# 資料來源

本次作業，透過向Twitter申請的Key，在決定關鍵字之後，我們可以使用Python搭配範例程式（經過些微修改，修改部份詳見本文最後一部分「範例程式的修改」）撈取Twitter上的Tweet。值得注意的是，Twitter限制了固定時段內可以撈取的資料量，幸虧範例程式擁有在一定時間之後再次嘗試撈取的功能，減少了撈取上的困擾與困難。

# 撈取資料的關鍵字

2016年發生許多值得關注的大事，其中之一便是美國總統大選。許多人士投入了民主黨與共和黨的黨內初選，其中，在台灣較廣為人知的候選人當屬民主黨的希拉蕊克林頓（Hillary Clinton）以及共和黨的唐納川普（Donald Trump）。

在本次作業，我們將使用各候選人的名字作為關鍵字，包括五位候選人，分別為民主黨的希拉蕊克林頓（Hillary Clinton）、伯尼桑德斯（Bernie Sanders）；共和黨的唐納川普（Donald Trump）、泰德克魯茲（Ted Cruz）、約翰卡西奇（John Kasich），其中並不包括已經宣布退選的候選人。

# 資料的欄位

以下說明參考Twitter官方的說明[備註1]，然而因為部分field的值與官方說明產生出入，故以下說明將比對"撈取的資料"與"官方說明"的差異，並且進行描述。

1. contributors: 類型為Objects，此field描述發佈Tweet的人，此field可以是空的。
2. truncated: 類型為Boolean。在Tweet被Retweet的時候，如果某Tweet超過140個字元，那麼將以"..."省略部分文字，該field則表示Tweet是否被省略。
3. text: 類型為String，Tweet的內容，字元編碼為UTF-8。
4. is_quote_status（官方的說明並無此field）:描述該Tweet是否被引用，如果否，則為False。
5. in_reply_to_status_id: 類型為Int64，如果該Tweet是一篇回覆，則此field便是發佈原始Tweet的使用者的ID，此field可以是空的。
6. id: 類型為Int64，發佈Tweet的使用者的ID。
7. favorite_count: 類型為Integer，對該Tweet表示“liked”的使用者人數人，此field可以是空的。
8. entities: 類型為Entities，包括多種field，如id、indices、id_str等，詳見[備註2]。
9. retweeted: 類型為Boolean，該Tweet是否被Retweet，如果否，則為False。
10. coordinates: 類型為Collection of Float，該Tweet被發佈地點的經緯度。
11. source: 類型為String，被用來發佈該Tweet的，工具程式。
12. in_reply_to_screen_name: 類型為String，如果該Tweet是一篇回覆，那麼該field顯示發佈原始Tweet的使用者在用戶端顯示的名稱，此field可以是空的。
13. in_reply_to_user_id: 類型為Int64，如果該Tweet是一篇回覆，那麼該field顯示發佈原始Tweet的使用者的ID，此field可以是空的。
14. retweet_count: 類型為Int，該Tweet被Retweet的次數。

# 範例程式的修改

1. 因為使用Anaconda2，所以將import的module從urllib修改為urlparse。
2. 因為程式沒有使用mongo db的需要，所以將mongo db相關的語法刪除。
3. 將searchTwitter的argument進行修改，提升撈取資料的速度，將max_res修改為1000。
4. 將searchTwitter的迴圈修改為while 1。
5. 將getTweets中的argument wait_period修改為1。
6. 為了在程式運行的時候察覺目前的工作狀態，添加以下代碼：print 'trying to access Twitter..'、print e、print 'start...'、print 'stop...'。
7. 將searchTwitter中的if len(statuses) > max_results的迴圈刪除。

# 備註

1. https://dev.twitter.com/overview/api/tweets
2. https://dev.twitter.com/overview/api/entities-in-twitter-objects
