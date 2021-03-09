
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