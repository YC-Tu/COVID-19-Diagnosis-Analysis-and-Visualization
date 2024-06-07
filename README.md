# COVID-19確診數數據分析與視覺化
新冠疫情自2020年爆發以來，對臺灣社會造成了巨幅的影響，當時疫情爆發時人心惶惶，至今已4年了，疫情也已緩和，讓人不禁想知道當時的確診數變化，因此本專案收集疾病管制署2020年開始到2024年6月4日的臺灣COVID確診數資料，並使用Python進行數據分析與視覺化。
## 資料取得與處理
本分析從疾病管制署資料開放平台[[1](#ref1)]取得COVID確診數資料，分別有2023年3月19日前後的資料，合併之後進行以下的前處理：縣市、鄉鎮有空值者為境外移入，予以排除；鄉鎮為「其他」者因僅一筆而予以排除；性別非男女的資料因為比例極小（小於0.1%）亦予以排除；將年齡層為0、1、2、3、4歲者合併為「0-4」，配合其它年齡段皆以5歲為一個區間。
## 分析項目與結果
本專案會針對各縣市累計病例數、各縣市每日新增病例數進行分析，也會探究性別、年齡與確定病例數三者的關係。
### 分析一：各縣市累計病例數
本分析以縣市為x軸，累計病例數為y軸繪製長條圖；再繪製臺灣地圖，以縣市為邊界，以顏色呈現呈現累計確診人數，如下。 \
<img src="img/01_臺灣Covid 19各縣市累計病例數長條圖.png" alt="01_臺灣Covid 19各縣市累計病例數長條圖" width="600"> \
<img src="img/02_臺灣各縣市Covid 19累計病例數分佈圖.png" alt="02_臺灣各縣市Covid 19累計病例數分佈圖" width="600"> \
從兩圖中可以看到，新北市的累計確診人數最多，達211萬人，其次依序是台中市、高雄市、桃園市、台北市，約為新北市累計確診人數的一半，再來是台南市，約為新北市累計確診人數的三分之一，六都以外縣市的確診人數都在新北市的四分之一以下。由次可見確診人數受到縣市繁榮程度、人口密度的影響。 \
接著繪製台南地圖，以鄉鎮為邊界，以顏色呈現呈現累計確診人數，如下。 \
<img src="img/03_臺南市各行政區Covid 19累計病例數分佈圖.png" alt="03_臺南市各行政區Covid 19累計病例數分佈圖" width="600"> \
圖中也顯示出：病例數較高的地區通常為市區，以永康區最高，其次是安南區，再來是東區、北區、南區，皆為靠近縣市合併前的臺南市區域。

### 分析二：各縣市累計病例數在時間上的變化
本分析以發病日為x軸，累計確診人數為y軸，縣市為顏色繪製直線圖，如下圖。 \
<img src="img/04_臺灣Covid 19各縣市累計病例數趨勢圖.png" alt="04_臺灣Covid 19各縣市累計病例數趨勢圖" width="600"> \
從圖中可以看到累計確診人數的爬升速度，從快到慢依序為新北市、台中市、高雄市、桃園市、台北市、台南市，與分析一相對應。

### 分析三：各縣市每日新增病例數
本分析首先以發病年為x軸，縣市為y軸，確定病例數為顏色繪製熱圖；再以發病日為x軸，每日新增病例數為y軸，縣市為顏色繪製線圖，如下。 \
<img src="img/05_臺灣Covid 19各縣市每年確診人數熱圖.png" alt="05_臺灣Covid 19各縣市每年確診人數熱圖" width="600"> \
<img src="img/06_臺灣Covid 19各縣市每日新增病例數趨勢圖.png" alt="06_臺灣Covid 19各縣市每日新增病例數趨勢圖" width="600"> \
從熱圖中可以看到，確診主要的發生時間在2022年，六都在2023年仍尚有不少的確診案例。在線圖中可以看到，2021年5月後有一小波確診，但真正每日新增病例數的高峰在一年後的2022年5月開始，之後到2023年4月前還有依序遞減的兩波高峰，可以看出Covid大量的傳播持續了快一年。 \
接下來再聚焦在2022年4月到2023年4月的線圖。 \
<img src="img/07_臺灣Covid 19各縣市每日確定病例數趨勢圖202204-202304.png" alt="07_臺灣Covid 19各縣市每日確定病例數趨勢圖202204-202304" width="600"> \
圖形顯示：第一波高峰大約在2022年4月到2022年7月，第二波高峰大約在2022年9月到2022年11月，第二波高峰大約在2022年12月到2023年3月。每日新增病例數上，新北市大部分的時間都位居首位，台北市、桃園市僅在第一波高峰時為第二、第三名交替，但是第一次高峰後，就開始與台中市、高雄市差不多，甚至是低於台中市與高雄市。事實上到後期六都的差距都變小，尤其是除了新北市的五都。

### 分析四：性別、年齡與確定病例數
首先以性別為x軸，確定病例數為y軸繪製長條圖，如下。 \
<img src="img/08_臺灣Covid 19累計確定病例男女人數.png" alt="08_臺灣Covid 19累計確定病例男女人數" width="600"> \
從圖中可以看到整體的確定病例數當中，女性（53.42%）大於男性（46.58%）。

接著先計算各年齡層確定病例數的標準z分數，並以該z分數為x軸，年齡層為y軸繪製分向長條圖，如下。 \
<img src="img/09_各年齡層Covid 19病例數分向長條圖.png" alt="09_各年齡層Covid 19病例數分向長條圖" width="600"> \
分向長條圖顯示25到44歲區間的染疫人數超過一個標準差，可能是青年人口因為工作需求有較多人與人接觸的結果。另外60到69歲區間與4歲以前人口的確診數是接近或低於負一個標準差，可能是因為這些區間本來的人數就少，再加上他們也不是高社交的族群。 \

最後來看不同性別、不同年齡層在確定病例數上的分布，並以該年齡層為x軸，確定病例數為y軸，性別為顏色繪製交互作用圖，如下。
<img src="img/10_Covid 19確定病例數在年齡與性別的交互作用折線圖.png" alt="10_Covid 19確定病例數在年齡與性別的交互作用折線圖" width="600"> \
從交互作用圖來看，青壯年整體的確定病例數最多，幼年、老年的確定病例數較少，值得注意的是70歲以上的數據明顯提升較可能是因為缺乏更細緻的區間分別（如：資料本身沒有細分70-74、75-79歲區間等等）所造成的合併結果。另外有趣的是，20-24區間出現交叉，19歲以前都是男性的確定病例數高於女性，但是到20歲以後則出現顛倒的趨勢，女性高於男性，細究原因可能是成年男性較不會因為身體異樣而去看醫生[[2](#ref2)][[3](#ref3)]，而沒有篩檢就沒有確診，因此確定病例數較低。
## 結論
總結來看，COVID-19確診數據揭示了疫情對不同地區、不同性別、不同年齡層的影響差異，例如確診數多集中在人口聚集地，又如女性成人的確診人數高於男性。這些結果可以為未來公共衛生政策提供參考，針對不同區域和人口群體制定更為精確的防疫措施和資源分配策略，讓國人在往後面對疫情能更有效地應對。
## 參考資料
<span id="ref1"></span>[1] https://data.cdc.gov.tw/ \
<span id="ref2"></span>[2] Gagnon, G. (2023). Men Tend to Avoid the Doctor: And Why It Can Be Deadly. In: Schmidt, C. (eds) The Invisible Hand of Cancer. Springer, Cham. https://doi.org/10.1007/978-3-031-45774-6_8 \
<span id="ref3"></span>[3] Gast, J., & Peak, T. (2010). “It Used to Be That if It Weren’t Broken and Bleeding Profusely, I Would Never Go to the Doctor”: Men, Masculinity, and Health. American Journal of Men’s Health, 5(4), 318–331. doi:10.1177/1557988310377926
