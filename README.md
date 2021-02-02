<img src="https://mitw.dicom.org.tw/img/logo.png" align="left" width=175 />
<h1>MI-TW (Medical Informatics) Connectathon </h1>

MI-TW ((Medical Informatics) 2021 聯測基於國際醫學資訊標準，例如: HL7 FHIR、DICOM、ISO/IEEE 11073等，採用規範標準化資訊互通介面，進行跨系統資訊互通聯測松(Connectathon)。發展及推行支援標準化之系統，以利於系之整合應用，以及系統複製、擴散、商品化應用。
  
## 活動詳情: https://mitw.dicom.org.tw/

# 徵求聯測主題 (Call for Porposal)
## 如果有興趣新增其他主題，請於2/28以前與我們聯絡，將以專案處理

### 聯測時程說明: 
* **Pre-Connectathon:** 面對面聯測前兩個月將提供線上測試資料以及測試主機，讓參加單位進行驗證，最為面對面聯測之準備。線上遇到問題時，將提供線上諮詢服務，並排除技術問題。
* **面對面聯測:** 參加單位將在三天內與其他參加單位以實際的網路連線進行系統介接測試，在三天內須完成指定的規範與測試資料，符合通過標準者，將提供產品通過證書。
* **成果展示:** 參加者通過聯測後，將提供成果展示活動，包含實體論壇、線上EDM以及網站公告等方式，展示聯測成果。成果亦將作為醫院採購產品之參考依據。


# 目標
* 醫學資訊標準是健康醫療系統整合應用、系統商品化的基礎。 醫資標準化系統之建置與推行有一套嚴謹的步驟； 從標準確立、準備測試案例、實做系統、聯測、及推展，以此有系統、有制度化地去推行。 MI-TW 聯測基於 HL7 FHIR 及 DICOMWeb 國際標準，將逐年逐步地輔導廠商、醫療機構、學術單位之研發單位參與研發，參與醫資系統標準化整合互通聯測。 

# 效益
* 發展合乎標準之醫資系統或醫療儀器、利於健康醫療系統整合應用、跨系統資料交換、也利於發展的系統在全球銷售。 

# 測試情境項目

## Track#1 病人基本資料互通

### 兩大要求: 「基本資料跨系統互通」以及「資安授權機制」
* 三種使用情境(Scenarios)涵蓋個人健康管理系統(Personal Health Record, PHR)應用或院內系統 FHIR Patient Resources互通
* 根據參加機構系統使用情境，需包含以下至少新增、刪除、修改、查詢四大功能

### 互通要求 
* 基本資料，包含: 身分證字號、中文姓名、住址和電話等資訊
* PHR匿名病人資料互通

### 資安授權機制
* 支援JWT機制
* 支援權限控管機制

## **情境1 院內系統** 

### 情境1-1 院內系統 - 病人身分確認用
* *說明: 執行各項護理技術、檢查、治療、手術等醫療處置前對病人做身分確認，例如：在診療前，醫護人員請病人提供基本資訊如姓名、生日用以核對病人身分是否正確

### 情境1-1 院內系統 - 聯繫病人用
* 聯絡方式如手機、email…用以聯絡病人
* 通訊地址如住家地址、工作地址…
  - **範例1:** 病人掛號完成後的看診時間、叫號時間等提醒
  - **範例2:** 醫院在病人掛號完成時或在看診半小時前寄簡訊通知
* 兩種用途的病人資料將共用相同的識別碼如身分證、護照、居留證、病歷號

### **聯測要求**: <u>調閱資料後，測試系統要能將回傳的JSON文件使用自行定義的UI恰當呈現病人資料</U>

## 情境2 院外系統 - 個人健康管理系統(Personal Health Record, PHR)
* PHR Patient 規格 => 匿名化
  - **情境：** 病人保有自己的PHR Patient ID，可透過PHR的授權機制授權醫護人員調用個人的健康資訊
  - **範例：** 病人就醫時提供個人的PHR Patient ID，並授權醫護人員可對此ID對應的PHR個案資料調用和操作

### 聯測要求: <u>測試系統要能使用PHR Patient ID串接其他三種Resource資料並適當的呈現出來</U>

### 公開技術規格: https://mitw.dicom.org.tw/preconnectathon1.html

# Track#2 - 生理量測數據互通(mHealth-plug-athon)

## 數據格式要求
* 生命徵象 (Vital signs): 身高、體重、血壓、體溫、脈搏、握力
* 檢驗資訊: 血糖
* 造影結果: 骨骼密度
/ 臨床發現: abdominal tenderness
* 儀器量測: 心電圖

### 聯測要求: <u>同一病人一系列之血壓、體溫、脈搏等生理量測資訊可在照護者端系統洽當呈現</u>

###　資安授權機制
* 支援JWT機制
* 支援權限控管機制

## 情境1 生理量測數據上傳 (Source) 

## 情境2 生理量測數據顯示 (Consumer) 

### 公開技術規格: https://mitw.dicom.org.tw/preconnectathon2.html

#	Track#3 - 用藥處方及用藥紀錄
### 數據格式要求:  常用藥物，詳見參考範例

### 聯測要求
* 可透過介面建立用藥處方，以及資料查詢
* 可透過介面建立用藥紀錄，以及資料查詢
* 用藥處方及用藥紀錄可於聯測系統之間做資料交換

### 包含角色
* **MedicationRequest Creator:** 處方開立單位系統，通常為醫師所屬之醫療機構。
* ***MedicationRequest Consumer:** 處方使用單位系統，可包含: 醫療照護機構、藥局、第三方健康照護應用、個人等。
* ***MedicationAdministration Creator:** 用藥記錄建檔單位系統，可包含: 醫療照護機構、第三方健康照護應用、個人等。
* ***MedicationAdministration Consumer:** 用藥記錄使用單位系統，可包含: 醫療照護機構、藥局、第三方健康照護應用、個人等。

###　資安授權機制
* 支援JWT機制
* 支援權限控管機制

## 情境1 Create MedicationRequest (Source)
* medicationReference
* medicationCodeableConcept
* update MedicationRequest

## 情境2 Retrieve MedicationRequest (Consumer)
* Get all MedicationRequest by patient id
* Get MedicationRequest by patient id and status
* Get MedicationRequest by patient id and medication code
* Get MedicationRequest by patient id and organization

## **情境3 Create MedicationAdministration (Source)** 
* Create MedicationAdministration

### **情境4 Retrieve MedicationAdministration (Consumer)** 
* Get all MedicationAdministration by patient id
* Get MedicationAdministration by patient id and request
* Get MedicationAdministration by patient id and effectivePeriod
* Get MedicationAdministration by patient id and practitioner’s organization

### 公開技術規格: https://mitw.dicom.org.tw/preconnectathon3.html

#	Track#4 - 影像與AI結果互通
* 此項目採用互通性聯測機制，同一情境測試項目需滿足IHE聯測規範，即需三家不同公司或是機構進行交互驗證方可通過聯測
* 目的在於測試影像與標記跨系統間的查詢與調閱，能符合DICOM以及FHIR標準

## 聯測要求:

### 查詢影像與標記 (Query)
* DICOMWeb: QIDO階層式查詢 – Studies-Series-Instances
* DICOM Query: C-FIND
* FHIR ImagingStudy
  - FHIR Observation SVG annotation

### 調閱影像與標記 (Retrieve)
* DICOMWeb: WADO-RS
* DICOMWeb: WADO-URI
* DICOM Retrieve C-MOVE
* FHIR Observation SVG annotation
* 影像與標記顯示一致性
  - 顯示標準格式標記跨系統之間呈現確保影像與標記呈現一致性
  - 標記格式包含: RTSS, GSPS, OVerlay, DICOM SR等

### **資安授權機制 (DICOMWeb/FHIR)**
  - 支援JWT機制
  - 支援權限控管機制

### 情境1 DICOM Q/R
* 使用傳統DICOM Network查詢與調閱影像與標記

### 情境2 Web Access
* 使用DICOMWeb階層式查詢方式查詢DICOMWeb主機，並依照DICOM階層式架構回傳結果
* 調閱使用WADO-URI或WADO-RS    

### 情境3 Integration with FHIR
  - 查詢FHIR ImagingStudy Resources
  - 使用WADO-URI或WADO-RS調閱影像以及標記
  - 或使用FHIR REST API調閱FHIR Observation SVG annotation

### 公開技術規格: https://mitw.dicom.org.tw/preconnectathon4.html

#	Track#5 - 病理影像
* 目的在於測試病理影像儲存管理主機(Source)以及顯示端(Consumer)能依照DICOMWeb標準查詢與調閱，超大尺寸數位病理影像，並能正確顯示

## **聯測要求**:

### 查詢影像與標記 (Query)
* DICOMWeb: QIDO階層式查詢 – Studies-Series-Instances
  - FHIR ImagingStudy
  - FHIR Observation SVG annotation

### 調閱影像與標記 (Retrieve)
* DICOMWeb: WADO-RS
* DICOMWeb: WADO-URI
* FHIR Observation SVG annotation
* 影像與標記顯示一致性
  - 顯示標準格式標記跨系統之間呈現確保影像與標記呈現一致性

## 情境1 病理影像調閱與檢視
* 使用DICOMWeb階層式查詢方式查詢DICOMWeb主機，並依照DICOM階層式架構回傳結果
* 調閱使用WADO-URI或WADO-RS   

## 情境2 標記調閱與檢視
* 使用DICOMWeb階層式查詢方式查詢DICOMWeb主機，並依照DICOM階層式架構回傳結果
* 調閱使用WADO-URI或WADO-RS

### 公開技術規格 (尚未公開): https://mitw.dicom.org.tw/preconnectathon5.html

#	Track#6 - Genomic (尚未公開)
### 公開技術規格 (尚未公開): https://mitw.dicom.org.tw/preconnectathon6.html

# Track 7 影像檢查流程(Scheduled Workflow) 
## 說明
* 提供場域針對DICOM相關的醫療儀器與HIS、PACS互通之應用驗證。
  - **例如:** 國內廠商自行研發超音波儀器，但苦於現有PACS與HIS廠商進行驗證，每次需要都需要在個別的醫院進行介接測試，此track域提供一個良好的技術交流場域，讓國內外多家廠商聯合測試，已證明產品符合國際醫學資訊標準規範
* 主要測試IHE Scheduled Worflow.b，作為明年IHE-Taiwan聯測準備演練
* 此Track主要與Track 4結合，主要針對HIS以及儀器製造商進行互通驗證

## 參與角色

### HIS:
* 針對HIS開立影像檢查單，以標準化的方式(HL7)，提供造影工作清單(Worklist)上的造影檢查單之新增、刪除、修改等功能。
* 針對影像調閱至門診或是HIS系統，以DICOMWeb方式調閱影像並呈現在HIS系統。
  - 如果HIS廠商參加此Track,則亦可參加 **#Track 4** 之影像調閱情境。

### PACS/RIS: 
* 針對PACS產品包含: Modality Worklist, Image Manager, Image Archive, Image Display等功能進行驗證，與醫療儀器廠商針對影像上傳，例如: C-STORE, STOW, 等方式進行介接測試驗證

### 影像AI公司
* 針對AI影像軟體業者產生的標準化之DICOM AI結果，例如: PS, RTSS, SEG等，上傳至Image Archive，並提供影像檢視之驗證
* 驗證包含: 格式驗證以及傳輸協定驗證(請參考 <u>儀器製造商</u>章節說明)

### 儀器製造商:
* 參加對象以國內外醫療儀器製造商在台灣銷售為主，包含: 超音波、心電圖、X光機、內視鏡等。
* 主要驗證儀器是否符合DICOM以下規格
  - **影像格式驗證:** 針對儀器製造商提供之符合性宣稱(Conformance Statement)，針對儀器端產生之DICOM物件進行格式驗證，以符合DICOM PS 3.3 SOP Class UID定義的格式規範。
    - **例如:** 產生的超音波影像是否符合DICOM格式、具備必要欄位、儲存的數值符合欄位規範、OID與UID之正確性等。
  - **傳輸協定驗證:** 針對儀器製造商提供之符合性宣稱(Conformance Statement)，驗證傳輸功能是否符合DICOM規範，例如: C-STORE, Storag　Commitment, MPPS, C-FIND-MWL等功能。

### 參考規格 (IHE Scheduled Worflfow.b)
* 開單作業(ADT)
* Query Modality Worklist [RAD-5]
* Modality Images Stored [RAD-8]
* 其他
