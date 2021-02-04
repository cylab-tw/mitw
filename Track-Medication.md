
# Track#3 - 用藥處方及用藥紀錄
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
