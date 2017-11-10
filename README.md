# Day 1

## Taiwan's Opportunities in the AI-First World
```
In this talk, I will attempt to explore several topics/directions that Taiwan can leverage and explore.
```

- AlphaGo Zero start from scratch.
    - 只是一個 AI 的引爆點
    - AI 應該要把焦點放在世界化、AI 只是一個包裝詞，會用這個包裝詞把 digitl service 散佈到世界各個角落
- Image recognition 是一個目前最好的 AI 應用
    - 醫療：13 萬張視網膜拍照的圖片、乳房攝影
    - Self-Driving car 是讓大家最印象深刻的應用與研究 (computer vision on self-driving car)
        - 人 v.s. 電腦開車：人開車的死亡率應該是比電腦高的，只是電腦開車，當第一例死亡出現，大家開始懷疑機器是否可以取代人類
- 台灣運用 open-source platform 的能力不足
    - 用 open-source 取代自建平台
    - 不要在展場找使用者，要在馬路上找使用者
    - 用 MVP 概念找到 user、驗證 concept 後，fast iterator 前進
- 全世界都在投資 AI，要找到自己在地的優勢
- 2000 年後，台灣收回對網路的繼續投資，一個 missing 就錯過 15 年
    - 中國、印度進步最快的 15 年
    - 台灣創新的都在半導體、網路投資卻無聲無息
    - 台灣在 google play 上世界前五大市場，也許是全世界花在手機上時間最多的國家，但政府、研究者、企業卻沒有感受到
    - Gaming 應該有很大的內需，但我們卻沒有 strong gaming industry
    - Behavior is convergin
        - TV -> PC -> Mobile -> App
        - Maybe mobile is not important now
        - 硬體不再重要：使用者需要的服務（拍照、聊天）不再是由硬體商提供，而是服務本身
- 新經濟(Digital)成功方程式
    - User、user、user(人口紅利、大國崛起)
    - Data(智慧服務基礎)
    - Winner take all
    - Disruptive bussines model(垂直整合) -> 每拿到一個 kindle 後，Amazon 可以賺到 1400 多美金 -> kindle 用送的都划算
- 2010 年到 2017，上網人口增加一倍
    - 19 億 -> ~ 38億
    - 不在中國，在東南亞
- 世界百大企業集中在 11 個國家，台灣僅有台積電一家
- Trends
    - Hardward accelerate AI
        - 手機 as supercomputer
        - AI 晶片
    - AI at Home
        - 智慧音箱：Amazon 預估 2017 年有 24M 台，可以進入發展期 v.s. AR/VR 全年不過幾百萬個 device，還在觀察期
        - As home collect data 的第一步
    - self-driving car
    - Drone
        - Camera follows you
        - 飛行的機器人
- Taiwan 的機會
    - AI 硬體有優勢、AI 應用要把握
    - 美國的網路業者、中國的網路業者都需要新的硬體服務
    - 台灣 AI 的服務不可能遍地開花的，人口數不夠
    - 台灣應該做什麼？軟硬整合：台灣做的軟體應該要做軟硬整合。EX: Gogoro、AI 技術 on chip

### Ref
- [Google 簡立峰：AI 時代，如果你家有兩個小孩，一個出國賺錢，另一個把家裡照顧好](https://www.inside.com.tw/2017/09/27/ai-industry)


## Deeper text mining (deep learning in text mining application)

- Text mining process/issues
    - 傳統：一篇文章由專家做關鍵字標著，使用者用關鍵字蒐集
    - 問題：一字多義、一義多字
    - 流程
        - 蒐集資料
        - 前處理：停用字、斷字、entity recognition、基礎統計
            - 暴力解：不斷字，n-gram 丟下去
            - 基本統計：算 co-occurence、算 PMI、算 two layer PMI
        - 做模型
        - 驗證
    - 前兩個流程通常在 text mining 是花很多時間的地方
- deep learning 如何改進
    - CRF-based named entity recognition
        - 如何識別一個 name entity？
        - 可視為擷取的問題
        - Precision Medicine(精準醫療)
            - 透過比較精準的資料蒐集，可以在醫療行為上做比較個人化、精準的診斷
            - Taiwan BioBank 在做這一塊
            - NIPS 2017 比賽：透過切片報告，做九大類癌症的分類，以前人工分，比賽想要用機器進行分類
                - Data source: 醫學文字報告
                - 基本解：丟 bow 暴力建模型
                - 進階想法：抓出關鍵字，找出關鍵字和類別的關聯(蛋白質 ... etc)
                - 疾病關鍵字擷取的困難
                    - 沒有疾病的字典
                    - 疾病名稱的 diversity 很高
                - CRF 概念：一句話丟進來，會先人工標注幾個 tag
                    - BIEO 四個 tag
                    - Bigin、indise、end、outside
                    - 人工取的 features
                        - POS
                        - terminalogy
                        - vowel
                        - abbreviation
                        - dic lookup
                        - morphology
                    - 以上取的 feature 花相當多的時間
                    - 也有拿掉這些人工 feature，暴力用 deep learn 去解，結果相當接近
                        - Auto generation of CRF features
                        - Word-based emdedding -> character-based embedding
                    - DNN 的 model 可解釋性不足，但效果不錯
    - rumor dection/stance classification
        - 某個訊息在 user 上，信心度的改變
    - sentiment-aware chatbot
        - 用 CNN 跑 sentiment classification 

Q:
1. 在醫學資料上如果 training data 很難取得，或是要找出剛剛 CRF 的 feature 很辛苦，有沒有辦法用 CRF 找出的 feature 丟到 NN model 裡面做出更高品質的 training data (transfer learning)
2. 醫學領域在做 word embedding 的時候，training corpus 該怎麼來？

- BioCreative 比賽

- ACL rumor detection



## 從資料競賽看應用實務 - KKV data game 17.06 1st place winner solution

- 根據 2016/6~2016/10個月的使用者觀看 kktv 資料，預測下個月使用者看最長 tv 的哪部
- data source
    - time
    - title
    - watch time
- 分析問題
    - 此問題是否是推薦問題？
    - 先做資料探索
        - 只有 18% 的 user 會看過去沒看過的劇
        - 平均一個 user 會看一部劇看幾次？
            - 用 boxplot 
            - min: 3.6 max:11.1，百分 50 以上都有看 8.x 多部劇，使用者看劇會有連續性
        - IDEA 提交最後一部劇當作答案
            - 結果：public leaderboard 27.2%
        - 改善
            - 使用轉移矩陣：看了月薪嬌妻再看深夜食堂的機率
        - user 最後看了劇 -> 會再看什麼劇 -> 答案提交
            - 結果：27.4%
        - 再找更多規則
            - 觀察前 40 觀看量 dominate 70% 的瀏覽量
            - 縮減 Y 為 41 類：前 40 名 + others，縮減 Y 後，來訓練一個分類模型
        - 訓練
            - 用 cross-validation
            - XBoost
            - 被分到 others 就沒辦法猜：因為 others 有 3xx 部劇
                - 解法：如果被預測到 others 的，結合之前的轉移矩陣，目標：找到一個門檻值，決定要猜的是模型的結果，或是要用轉移矩陣的結果
        - 結果：0.28562, 1st
    - 模型學到了什麼？
        - 最後一部劇看了什麼
        - 過去看過幾部劇
    - 還能怎麼做？
        - 第二名和第三名用 deep learning
- 從競賽看應用
    - 找到問題
    - 翻譯問題
        - 要怎麼把問題翻譯成機器學習可以解的問題
            - 了解算法
            - 多看資料：到 kaggle 上看哪些資料丟上去
    - 解決問題
        - 經典算法
            - 比賽上可能會調很多奇怪的參數
        - 好的資料
            - 實務上都想辦法做出更好的資料
    - 評量指標真的要預測這麼準嗎？
        - 比賽的指標很單純，越準越好
        - 實務上不一定只推薦最熱門、最好的商品，可能可以考慮推薦多個商品，或是推薦的多元化 (diversity)
    - 資料探索重要嗎？
        - 有 user 用 random-forest 去解，不斷地調參數，最後只有 0.25
        - 但我們只丟最後一部劇，就有 0.27 了
    - model 準確度 v.s. 模型的可解釋性要做取捨
        - NN 準確度可能比較高，但預測錯誤時怎麼解釋？怎麼調整？
        - tree-based 或 regression 的可解釋性高
        - 要自己做取捨
- 總結
    - 「數據和特徵決定機器學習的上限，而模型和算法只是逼近這個上限而已。」

## Representation Learning on Big and Small Data

- At google 的心得
    - Google 內部在用的 search engine 的在初期是否是否要用 n^2 的方法？
        - 不一定，因為新的網站上線時，n^2 訓練太久，儘管很準，但不需要(沒有緊急性)
        - n 的算法就夠用了

    - Google 的心得
        - 資料夠多，不需要用很複雜的模型
        - SIGIR paper 都說自己的演算法很好，但拿到實務用，並沒有比較好

- Why Big data？
    - AlexNet 的參數有 300000 萬個，不可能用一個簡單的線性計算來解決
        - Big data 是必須要有的，不然不可能解決這麼困難的問題
- Scale ML algorithm
    - 近似 + 暴力
    - 把 N^2 -> NP 問題
- 1.5 billion user APP 才可能賺錢
    - 要清楚自己台灣的定位
- 醫療現在都是 proactive mode
    - user 不會主動找醫生


## Amazing GANs

- Introduce four GANs models

## 從雛形到千台連網相機的挑戰

- Motivation
    - 全世界只有 1% 的攝影機後有人在看
    - 一個人最多只能看 7 個 screens
- 流程
    - video acquisition
    - cloud vision
    - alert
- Semantic segmentation
    - 初期：Fast-RCNN
    - 使用 COCO dataset
        - 資料主要來自於 Flickr 拍攝良好的照片，有些無法 detect 的 case 可能來自於 coco dataset 沒有的特徵
            - EX: 真實世界的資料可能來自於停車場，是黑白、模糊的
- Go to production 的工程挑戰
    - 今天不會著墨
- Computer vision learning
    - Data is our gold
    - 氣候、時間很重要
        - EX: 訓練資料中出現 human 的時間點可能只有白天，但半夜才是最需要做影像辨識的時間
    - Training data 怎麼 label
        - 取 on-site labeler
        - MTurker
        - 3rd party
    - 不是每一張攝影機傳回的照片都要做標著，而是標注重要的資料
        - 解決方法-> 如何挑重要的照片來 label
            - Domain adoption:想要區分白天/晚上中的人，能否先把分類器對白天/晚上的feature降低->學一個分類器，把彩色和紅外線圖片壓縮在一起
            - semantic segmentation
                - Bayesian segnet: 預測時，會給定給個預測值的信心程度，最後要挑出來標記的資料，只拿信心程度低的拿出來標記，信心程度高的就不用再標記了
            - Geometric set-cover based active selection
                - 做資料選擇，只挑照片中有人的圖片
                - paper：2x appromation greedy search: 每次挑選都挑離現在最遠的點
        - common 

Q: 您們在使用 coco 資料集建模型時，做 image segmentation 建模型的時候，除了蒐集更多的資料外，對於影像有做 data aumentation 或是想辦法加入雜訊嗎？如果有的話，效果如何？沒有的話是為什麼？
- RGB -> IR 資料用 data augmentation 效果不好，甚至使用 pixel to pixel 的模型去 training 時效果也不好

## 音樂檢索與歌聲抽取

- Music informtion retrieve
    - Content-based search
        - melody(主旋律)
        - mood(歌曲想表達的情緒)
        - genre(曲風)
        - instrument(樂器)
        - chords(和弦)
        - cover songs(翻唱歌、口水歌)
    - Metadata-based search
        - 標題、標籤、歌手、作曲者 ... etc
- Sining voice recognition
    - To reconstruct audio sources from monaural(single channel) recording
        - 在影像辨識就像把所有的圖片疊加起來要辨識出裡面有什麼動物
        - recognition: 辨識裡面有什麼動物
        - reconstruction: 從疊加的影像中重新還原為原始的影像
        - 在音樂辨識中，就像一個 channel 中有各種聲音，要單獨把人聲抽取出來
    - 抽取人聲後應用
        - Vocal pitch tracking
            - cover song identification
            - 哼唱選歌
            - 唱歌評分
        - Artist identification
        - Lyrics recognition/alignment
        - Singing assistance/scoring
    - Our approach
        - DNN
            - input: 音樂 + 人聲
            - output: 音樂的 spectrum、人聲的 spectrum
            - DNN + Domain knowledge
                - use phase infomation
                - use pre-trained for better initial weight
                    - melogy 在 initial weight 上必須要符合一些規則
                - objective function 可以調整為具有「清脆」的方向前進：incorporate of clarity into DNN error measure for better SVS
    - easy for human
    - diff from ICA(independent component analysis) since ICA requires multiple-channel recording

## Defect Inspection with Deep Learning(深度學習在瑕疵檢測上遇到的挑戰)

- 基本上是基於 CNN Model
- Fully convolution neural network image segmentation
    - CNN training 出來後的 feature map 後面可以再接任何的分類器 or decoder
- Label data collection
    - X: image
    - Y: pixel level classification
- Deal with imbalance data
    - data aumentation


# Day 2

## AlphaGo－深度學習與強化學習的勝利

## CGI and CGI

## The Interplay of Big Data, Machine Learning, and Artificial Intelligence

## 時空軌跡分析技術於人流與載具預估

## 深度學習之智慧型對話機器人 Deep Learning for Intelligent Conversational Bots 

## 小 App 背後的大數據與人工智慧

## 大數據情緒分析的經驗分享

## Quantitative Trading from Zero to One: From Rule-based to Artificial Intelligence