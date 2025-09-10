# **BladderCancer_Survival Analysis: 膀胱癌之存活分析**

## **專題介紹**
膀胱是我們日常生活中非常重要的器官，而膀胱癌的確切成因還尚未被了解，本專題是透過簡單的存活分析來了解那些因素會影響膀胱癌病患的存活，以及最後是否有滿足模型的假設。

---

## **資料介紹**

### **資料來源**
本專題的資料是來自於MSK癌症中心2023年的臨床數據，原始資料總共有526筆。

### **變數介紹**
- Cancer.Type.Detailed : 此為癌症類別主要分為以下三種。 
  - Bladder Urothelial Carcinoma(膀胱尿路上皮癌)，占總數76.4%  
  - Upper Tract Urothelial Carcinoma(上泌尿道尿路上皮癌)，占總數21.5%  
  - Urethral Urothelial Carcinoma(尿道尿路上皮癌)，占總數1.9%  
- Age : 診斷時的年紀，範圍落在19~90
- Fraction.Genome.Altered(FGA) : 拷貝數受影響的比例，範圍落在0~0.7016    
- MSI.Score : 微星體不穩定分數，範圍落在-1~32
- Mutation.Count : 基因突變數量，範圍落在1~101(除了某一病患為414)  
- TMB : 腫瘤突變負荷量，範圍落在0~84.16989(除了某一病患為405.19)
- Sex : 性別，男性265位與女性126位(部分病患沒有此資訊)
- Overall.Survival.Months : 存活時間(月)，範圍落在0~105.29
- Overall.Survival.Status : 1事件發生(280位)，0(250位)

## **存活分析應用及解釋**

### 1. **存活率分析**
- Kaplan Meier S(t)  
- Nelson Aalen H(t)  
- 透過以上兩種方式畫圖去了解整個病患的狀況(存活率)。

### 2. **癌症種類分析**
Log-rank test : 判斷三種類別的膀胱癌是否存活有差別，檢定結果是三者沒有顯著差別。

### 3. **模型分析**
Cox proportional hazards model : 利用Cox模型判斷變數與存活的關聯，最終顯著影響的變數為Age、FGA、Mutation.Count

### 4. **模型基本假設**
- Breslow's baseline cumulative hazard function  
- Schonfeld residuals  
- Cox-snell residuals  
- 以上檢定說明此模型是有符合PH model的假設

---

## **結語**
1. 最終模型走滿足Cox PH model 的模型假設。  
2. Age增加，風險也是增加的，大部分疾病都會符合此結果。  
3. FGA增加，風險也是增加的，而且其係數較大。  
4. Mutation增加，風險反而是降低的，這部分可能需要進一步透過其他資料集來判斷是否合理。  

---

## **參考資料**
- [FGA介紹](https://www.thehyve.nl/articles/fraction-of-genome-altered-total-mutations-cbioportal)
- [TMB介紹](https://geneonline.news/tmb-in-prostate-cancer/)
- [膀胱癌介紹](https://heal-oncology.com/cancer/%E8%86%80%E8%83%B1%E7%99%8C/)
- [上泌尿道尿路上皮癌](https://bladdercancercanada.org/en/patients/educational-resources/guidebooks/guidebook-translations/%E4%B8%8A%E6%B3%8C%E5%B0%BF%E9%81%93%E5%B0%BF%E8%B7%AF%E4%B8%8A%E7%9A%AE%E7%99%8C-utuc-%E6%82%A3%E8%80%85%E6%8C%87%E5%8D%97/)

---  

## **結構**
BladderCancer_Survival_Analysis    
│── README.md  
│── Survival_analysis_main.pdf # 書面報告  
│── Survival_analysis_code.Rmd # 程式碼  
│── Survival_analysis_reort.pdf  # 簡報  
│── bladder.csv #資料集