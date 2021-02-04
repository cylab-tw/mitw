#	Track#5 - 病理影像
* **說明:** 此賽道主要目的在於測試病理影像儲存管理主機(Source)以及顯示端(Consumer)能依照DICOMWeb標準查詢與調閱，超大尺寸數位病理影像，並能正確顯示。在影像標記註解部分，透過影像與標記標準化，用來解決全幅(Whole Slide)數位病理影像互通性的問題。標註格式可能是影像分割形式的點陣圖型、透過座標定義輪廓之向量圖型等，本賽道主要針對註解標示影像的關注區(regions of interest, ROIs)的標準化進行驗證。亦希望參加者能提供簡單的標記，作為標準化病理影像的示範案例，提供異質性系統互通，作為加速數位病理影像標準化。
* **預期效益:** 隨著人工智慧與機器學習(AI/ML)的快速發展，需要加快標準化的醫學影像分析工作流程的軟體開發流程(SDLC)，以及採取更加敏捷的開發方法。參加單位可使用實際或是產品雛型參加此賽道，由於這需要大量的前期開發工作，因此參加者需要具備較高的技術門檻。這也鼓勵參加單位早期投資，希望此標準足夠成熟，進而早期布局，以證明投資的合理性。早日切入數位病理影像市場。為了簡化標準化開發流程並鼓勵產業早期實施和測試。MISAT鼓勵醫學影像分析專家、軟體工程師、開源工作者參加，並投入開發開源試驗，建立提供數位病理影像標準化系統的產品概念驗證(Proof ofConcept)

## **範圍** 
### 病理影像
* 針對DICOM數位病理影像(DICOM Whole Slide Imaging - Supplement 145)存取調閱、並能正確顯示
* 產生DICOM數位病理影像並透過DICOM標準協定上傳至PACS Server

### 標記註解
* 對現有上述標準化DICOM數位病理影像進行分析，產生標記註解
* 產生TID 1500結構化報告作為標記註解格式
* 可使用JavaScript以及Python作為影像顯示與影像分析

## **聯測要求**:
### 參與角色
* **顯示系統(Display systems)**
  - 畫標記
  - 將標記轉換成結構化報告格式(DICOM SR) 
  - 解析DICOM SEG並呈現在影像上
  - 傳輸(Store)、查詢與調閱(Query/Retrieve)影像與標記
* **分析系統(Analysis systems)**
  - 解析標記用分析
  - 將分析結果(AI Results)儲存成結構化報告格式(DICOM SR)
  - 傳輸(Store)、查詢與調閱(Query/Retrieve)影像與標記

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

## 參考標準
1. [DICOM Whole Slide Imaging (WSI)](http://dicom.nema.org/Dicom/DICOMWSI/)
2. DICOM Suuplement 222: Whole Slide Microscopy Bulk Annotations Storage SOP Class:  [PDF](https://www.dicomstandard.org/docs/librariesprovider2/dicomdocuments/sup222_pc_wsiannotations88f52878-287c-4356-b3bb-72dbbb1dad89.pdf?sfvrsn=328ca8a7_3) [PPT](https://www.dicomstandard.org/docs/librariesprovider2/dicomdocuments/sup222_pc_wsiannotations.pptxd1c5a37c-21fb-4ce0-bedb-b3c228c1f204.pptx?sfvrsn=df464d75_3) [Word](https://www.dicomstandard.org/docs/librariesprovider2/dicomdocuments/sup222_pc_wsiannotations.docx8791a4cf-8031-4d78-94f5-1fd951f90639.docx?sfvrsn=84dbb85f_3) - 徵求公開意見中
3. [DICOMWeb](https://www.dicomstandard.org/dicomweb)
4. [FHIR Observation](https://www.hl7.org/fhir/observation.html)