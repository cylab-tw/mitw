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