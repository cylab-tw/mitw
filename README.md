# MI-TW (Medical Imformatics Conectathon Tawain) 2021 聯測說明
活動詳情: https://mitw.dicom.org.tw/

## MI-TW Connectathon 目標
* 醫學資訊標準是健康醫療系統整合應用、系統商品化的基礎。 醫資標準化系統之建置與推行有一套嚴謹的步驟； 從標準確立、準備測試案例、實做系統、聯測、及推展，以此有系統、有制度化地去推行。 MI-TW 聯測基於 HL7 FHIR 及 DICOMWeb 國際標準，將逐年逐步地輔導廠商、醫療機構、學術單位之研發單位參與研發，參與醫資系統標準化整合互通聯測。 
## MI-TW Connectathon效益
* 發展合乎標準之醫資系統或醫療儀器、利於健康醫療系統整合應用、跨系統資料交換、也利於發展的系統在全球銷售。 

# MI-TW測試情境項目
## Track#1 病人基本資料互通
* 兩大要求: 「基本資料跨系統互通」以及「資安授權機制」
* 三種使用情境(Scenarios)涵蓋個人健康管理系統(Personal Health Record, PHR)應用或院內系統 FHIR Patient Resources互通
*  根據參加機構系統使用情境，需包含以下至少新增、刪除、修改、查詢四大功能
* **互通要求** 
  - 基本資料，包含: 身分證字號、中文姓名、住址和電話等資訊
  -  PHR匿名病人資料互通
* **資安授權機制**
  - 支援JWT機制
  - 支援權限控管機制

### **情境1 院內系統** 
  - **#情境1-1 院內系統 - 病人身分確認用**
    - 說明: 執行各項護理技術、檢查、治療、手術等醫療處置前對病人做身分確認，例如：在診療前，醫護人員請病人提供基本資訊如姓名、生日用以核對病人身分是否正確
  - **#情境1-1 院內系統 - 聯繫病人用**
    - 聯絡方式如手機、email…用以聯絡病人
    - 通訊地址如住家地址、工作地址…
    - 範例1:病人掛號完成後的看診時間、叫號時間等提醒
    - 範例2:醫院在病人掛號完成時或在看診半小時前寄簡訊通知
  - 兩種用途的病人資料將共用相同的識別碼如身分證、護照、居留證、病歷號
   - **聯測要求**: 調閱資料後，測試系統要能將回傳的JSON文件使用自行定義的UI恰當呈現病人資料

### **情境2 院外系統 - PHR** 
  - PHR Patient 規格 => 匿名化
     - 情境：病人保有自己的PHR Patient ID，可透過PHR的授權機制授權醫護人員調用個人的健康資訊
     - 範例：病人就醫時提供個人的PHR Patient ID，並授權醫護人員可對此ID對應的PHR個案資料調用和操作
  - **聯測要求**: 測試系統要能使用PHR Patient ID串接其他三種Resource資料並適當的呈現出來
### 技術規格
* https://mitw.dicom.org.tw/preconnectathon1.html

## Track#2 - 生理量測數據互通(mHealth-play-athon)
* **數據格式要求** 
  - 生命徵象 (Vital signs): 身高、體重、血壓、體溫、脈搏、握力
  - 檢驗資訊: 血糖
  - 造影結果: 骨骼密度
  - 臨床發現: abdominal tenderness
  - 儀器量測: 心電圖
* **聯測要求**: 同一病人一系列之血壓、體溫、脈搏等生理量測資訊可在照護者端系統洽當呈現

* **資安授權機制**
  - 支援JWT機制
  - 支援權限控管機制

### **情境1 生理量測數據上傳 (Source)** 
### **情境2 生理量測數據顯示 (Consumer)** 
### 技術規格:
* https://mitw.dicom.org.tw/preconnectathon2.html

##	Track#3 - 用藥處方及用藥紀錄
* **數據格式要求**:  常用藥物，詳見參考範例
* **聯測要求**:
  - 可透過介面建立用藥處方，以及資料查詢
  - 可透過介面建立用藥紀錄，以及資料查詢
  - 用藥處方及用藥紀錄可於聯測系統之間做資料交換
* 包含角色
  - **MedicationRequest Creator:** 處方開立單位系統，通常為醫師所屬之醫療機構。
  - **MedicationRequest Consumer:** 處方使用單位系統，可包含: 醫療照護機構、藥局、第三方健康照護應用、個人等。
  - **MedicationAdministration Creator:** 用藥記錄建檔單位系統，可包含: 醫療照護機構、第三方健康照護應用、個人等。
  - **MedicationAdministration Consumer:** 用藥記錄使用單位系統，可包含: 醫療照護機構、藥局、第三方健康照護應用、個人等。

* **資安授權機制**
  - 支援JWT機制
  - 支援權限控管機制

### **情境1 Create MedicationRequest (Source)** 
  - medicationReference
  - medicationCodeableConcept
  - update MedicationRequest

### **情境2 Retrieve MedicationRequest (Consumer)** 
  - Get all MedicationRequest by patient id
  - Get MedicationRequest by patient id and status
  - Get MedicationRequest by patient id and medication code
  - Get MedicationRequest by patient id and organization

### **情境3 Create MedicationAdministration (Source)** 
  - Create MedicationAdministration

### **情境4 Retrieve MedicationAdministration (Consumer)** 
  - Get all MedicationAdministration by patient id
  - Get MedicationAdministration by patient id and request
  - Get MedicationAdministration by patient id and effectivePeriod
  - Get MedicationAdministration by patient id and practitioner’s organization

### 技術規格:
* https://mitw.dicom.org.tw/preconnectathon3.html

##	Track#4 - 影像與AI結果互通
* 此項目採用互通性聯測機制，同一情境測試項目需滿足IHE聯測規範，即需三家不同公司或是機構進行交互驗證方可通過聯測
* 目的在於測試影像與標記跨系統間的查詢與調閱，能符合DICOM以及FHIR標準
* **聯測要求**:
  -  查詢影像與標記 (Query)
       - DICOMWeb: QIDO階層式查詢 – Studies-Series-Instances
       - DICOM Query: C-FIND
       - FHIR ImagingStudy
       - FHIR Observation SVG annotation
  -  調閱影像與標記 (Retrieve)
       - DICOMWeb: WADO-RS
       - DICOMWeb: WADO-URI
       - DICOM Retrieve C-MOVE (待討論)
       - FHIR Observation SVG annotation
  - 影像與標記顯示一致性
       - 顯示標準格式標記跨系統之間呈現確保影像與標記呈現一致性
       - 標記格式包含: RTSS, GSPS, OVerlay, DICOM SR等
  - 影像檢查流程(Scheduled Workflow) 
      - Query Modality Worklist [RAD-5]
      - Modality Images Stored [RAD-8]
      - 開單作業(ADT)

* **資安授權機制 (DICOMWeb/FHIR)**
  - 支援JWT機制
  - 支援權限控管機制

### 情境1 DICOM Q/R
  - 使用傳統DICOM Network查詢與調閱影像與標記

### 情境2 Web Access
  - 使用DICOMWeb階層式查詢方式查詢DICOMWeb主機，並依照DICOM階層式架構回傳結果
  - 調閱使用WADO-URI或WADO-RS    

### 情境3 Integration with FHIR
  - 查詢FHIR ImagingStudy Resources
  - 使用WADO-URI或WADO-RS調閱影像以及標記
  - 或使用FHIR REST API調閱FHIR Observation SVG annotation

### 情境4 影像檢查流程(Scheduled Workflow)
  - 參加機構扮演各種影像檢查流程之系統角色
  - 使用HL7, DICOM或是DICOMWeb等標準協定

### 技術規格:
* https://mitw.dicom.org.tw/preconnectathon4.html

##	Track#5 - 病理影像
* 目的在於測試病理影像儲存管理主機(Source)以及顯示端(Consumer)能依照DICOMWeb標準查詢與調閱，超大尺寸數位病理影像，並能正確顯示

* **聯測要求**:
 -  查詢影像與標記 (Query)
       - DICOMWeb: QIDO階層式查詢 – Studies-Series-Instances
       - FHIR ImagingStudy
       - FHIR Observation SVG annotation
  -  調閱影像與標記 (Retrieve)
       - DICOMWeb: WADO-RS
       - DICOMWeb: WADO-URI
       - FHIR Observation SVG annotation
  - 影像與標記顯示一致性
       - 顯示標準格式標記跨系統之間呈現確保影像與標記呈現一致性

### 情境1 病理影像調閱與檢視
  - 使用DICOMWeb階層式查詢方式查詢DICOMWeb主機，並依照DICOM階層式架構回傳結果
  - 調閱使用WADO-URI或WADO-RS   

### 情境2 標記調閱與檢視
  - 使用DICOMWeb階層式查詢方式查詢DICOMWeb主機，並依照DICOM階層式架構回傳結果
  - 調閱使用WADO-URI或WADO-RS

### 技術規格 (尚未公開):
* https://mitw.dicom.org.tw/preconnectathon5.html

##	Track#6 - Genomic (尚未公開)
### 技術規格 (尚未公開):
* https://mitw.dicom.org.tw/preconnectathon6.html


