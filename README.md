# Big-Data-Analytics---Homework-2

# 資料來源

本次作業，透過向Twitter申請的Key，在決定關鍵字之後，我們可以使用Python撈取Twitter上的Tweet。值得注意的是，Twitter限制了15分鐘可以撈取的資料量，幸虧範例程式擁有在一定時間之後再次嘗試撈取的功能，減少了撈取上的困擾與困難。

# 撈取資料的關鍵字

2016年發生許多值得關注的大事，其中之一便是美國總統大選。許多人士投入了民主黨與共和黨的黨內初選，其中，在台灣較廣為人知的候選人當屬民主黨的希拉蕊克林頓（Hillary Clinton）以及共和黨的唐納川普（Donald Trump）。

在本次作業，我們將使用各候選人的名字作為關鍵字，包括五位候選人，分別為民主黨的希拉蕊克林頓（Hillary Clinton）、伯尼桑德斯（Bernie Sanders）；共和黨的唐納川普（Donald Trump）、泰德克魯茲（Ted Cruz）、約翰卡西奇（John Kasich），其中並不包括已經宣布退選的候選人。

# 資料的欄位

# 範例程式的修改

1. 因為使用Anaconda2，所以將import的module從urllib修改為urlparse。
2. 因為程式沒有使用mongo db的需要，所以將mongo db相關的語法刪除。
3. 將searchTwitter的argument進行修改，提升撈取資料的速度，將max_res修改為1000。
4. 將searchTwitter的迴圈修改為while 1。
5. 將getTweets中的argument wait_period修改為1。
6. 為了在程式運行的時候察覺目前的工作狀態，添加以下代碼：print 'trying to access Twitter..'、print e、print 'start...'、print 'stop...'。
7. 將searchTwitter中的if len(statuses) > max_results的迴圈刪除。
