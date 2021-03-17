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

表格1 WSI影像包含的Tags(必須:M、非必須:U)

| IE                                        | Module                                                   | Reference | Usage                                                               |   |
|-------------------------------------------|----------------------------------------------------------|-----------|---------------------------------------------------------------------|---|
| Patient                                   | Patient                                                  | C.7.1.1   | M                                                                   |   |
|                                           | Specimen                                                 | C.7.1.2   | U                                                                   |   |
|                                           | Clinical Trial Subject                                   | C.7.1.3   | U                                                                   |   |
| Study                                     | General Study                                            | C.7.2.1   | M                                                                   |   |
|                                           | Patient Study                                            | C.7.2.2   | U                                                                   |   |
|                                           | Clinical Trial Study                                     | C.7.2.3   | U                                                                   |   |
| Series                                    | General Series                                           | C.7.3.1   | M                                                                   |   |
|                                           | Whole Slide Microscopy Bulk Annotations Series (見表格2) | C.8.Y1.1  | M                                                                   |   |
|                                           | Clinical Trial Series                                    | C.7.3.2   | U                                                                   |   |
| Frame of Reference                        | Frame of Reference                                       | C.7.4.1   | M                                                                   |   |
| Equipment                                 | General Equipment                                        | C.7.5.1   | M                                                                   |   |
|                                           | Enhanced General Equipment                               | C.7.5.2   | M                                                                   |   |
| Whole Slide Microscopy   Bulk Annotations | Whole Slide Microscopy Bulk Annotations (見表格3)        | C.8.Y1.2  | M                                                                   |   |
|                                           | ICC Profile色碼表                                        |           | C – 如果存在Recommended Display CIELab Value (0062,000D)   則為必須 |   |
|                                           | Common Instance Reference                                | C.12.2    | M                                                                   |   |
|                                           | SOP Common                                               | C.12.1    | M                                                                   |   |
| Whole Slide Microscopy Image  | Total Pixel Matrix Columns (0048,0006)                   |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Total Pixel Matrix Rows (0048,0007)                      |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Imaged Volume Width(0048,0001)                           |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Imaged Volume Height (0048,0002)                         |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Rows(0028,0010)                                          |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Columns(0028,0010)                                       |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Pixel Spacing (0028,0030)                                |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Spacing Between Slices (0018,0088)                       |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Slice Thickness (0018,0050)                              |           | M                                                                   |   |
| Whole Slide Microscopy Image  | Image Orientation (0048,0102)                            |           | M                                                                   |   |ientation (0048,0102) 


表格2  Whole Slide Microscopy Bulk Annotations Series包含的Tags(影像的顯示儲存方式)

|                          Attribute Name                          |    Tag   | Type |         Attribute   Description         |
|:----------------------------------------------------------------:|:--------:|:----:|:---------------------------------------:|
|                             Modality                             |  -80,060 |   1  |        最初取得影像數據的設備類型       |
|                           Series Number                          | -200,011 |   1  | A number that   identifies this Series. |
|           Referenced Performed Procedure Step Sequence           |  -81,111 |  1C  |            對照的SOP Instance           |
| >Include Table 10-11 “SOP   Instance Reference Macro Attributes” |          |      |                                         |


表格3  Whole Slide Microscopy Bulk Annotations包含的Tags(記錄病理影像的儀器玻片相關資訊)

|                            Attribute Name                           |     Tag     | Type |                                Attribute   Description                               |
|:-------------------------------------------------------------------:|:-----------:|:----:|:------------------------------------------------------------------------------------:|
|   Include Table 10-12 “Content   Identification Macro Attributes”   |             |      |                                          　                                          |
|                             Content Date                            |   -80,023   |   1  |                                  內容開始建立的日期                                  |
|                             Content Time                            |   -80,033   |   1  |                                  內容開始建立的時間                                  |
|                      Annotation Group Sequence                      | (gggg,eee1) |   1  |                  具有共同特徵(例如圖形類型，屬性或度量)的標記群組。                  |
|                        >Annotation Group UID                        | (gggg,ee19) |   1  |                             標記群組的Unique   identifier                            |
|                       >Annotation Group Number                      | (gggg,eee2) |   1  |     標記群組的Unique   identifier，在這個SOP中是唯一的，從1開始，每隔一個增加1。     |
|                       >Annotation Group Label                       | (gggg,eee3) |   1  |                           識別此標記群組的使用者定義標籤。                           |
|                    >Annotation Group Description                    | (gggg,eee4) |   3  |                             此標記群組的使用者定義描述。                             |
|                 >Annotation   Group Generation Type                 | (gggg,ee13) |   1  |                            生成此標記的演算法類型，包含：                            |
|                                                                     |             |      |                                 自動：由演算法生成。                                 |
|                                                                     |             |      |                        半自動：由演算法在標註者的輔助下生成。                        |
|                                                                     |             |      |                                 手動：由標註者生成。                                 |
|            >Annotation Algorithm Identification Sequence            | (gggg,ee12) |  1C  | 建立此標記的演算法，如果Annotation   Group Generation Type是自動或半自動，則為必須。 |
| >>Include Table 10-19   “Algorithm Identification Macro Attributes” |             |      |                            No Baseline   CIDs are defined.                           |


表格4  WS的ROI標記包含的Tags(必須:M、非必須:U)

|    IE    |                           Module                          | Reference | Usage |
|:--------:|:---------------------------------------------------------:|:---------:|:-----:|
| Whole Slide Microscopy Image |              ROI Display   Color (3006,002A)              |     　    |   U   |
| Whole Slide Microscopy Image |     Recommended   Display Grayscale Value (0062,000C)     |     　    |   U   |
| Whole Slide Microscopy Image |       Recommended   Display CIELab Value(0062,000D)       |     　    |   U   |
| Whole Slide Microscopy Image |               Contour   Sequence (3006,0040)              |     　    |   M   |
| Whole Slide Microscopy Image |            Referenced ROI   Number (3006,0084)            |     　    |   M   |
| Whole Slide Microscopy Image |                 Content   Date(0008,0023)                 |     　    |   M   |
| Whole Slide Microscopy Image |                 Content   Time(0008,0033)                 |     　    |   M   |
| Whole Slide Microscopy Image |           Annotation   Group Sequence(gggg,eee1)          |     　    |   M   |
| Whole Slide Microscopy Image |             Annotation   Group UID(gggg,ee19)             |     　    |   M   |
| Whole Slide Microscopy Image |            Annotation   Group Number(gggg,eee2)           |     　    |   M   |
| Whole Slide Microscopy Image |            Annotation   Group Label(gggg,eee3)            |     　    |   M   |
| Whole Slide Microscopy Image |       Annotation   Group Generation Type(gggg,ee13)       |     　    |   M   |
| Whole Slide Microscopy Image | Annotation   Algorithm Identification Sequence(gggg,ee12) |     　    |   U   |

## 情境2 標記調閱與檢視
* 使用DICOMWeb階層式查詢方式查詢DICOMWeb主機，並依照DICOM階層式架構回傳結果
* 調閱使用WADO-URI或WADO-RS

## 參考標準
1. [DICOM Whole Slide Imaging (WSI)](http://dicom.nema.org/Dicom/DICOMWSI/)
2. DICOM Suuplement 222: Whole Slide Microscopy Bulk Annotations Storage SOP Class:  [PDF](https://www.dicomstandard.org/docs/librariesprovider2/dicomdocuments/sup222_pc_wsiannotations88f52878-287c-4356-b3bb-72dbbb1dad89.pdf?sfvrsn=328ca8a7_3) [PPT](https://www.dicomstandard.org/docs/librariesprovider2/dicomdocuments/sup222_pc_wsiannotations.pptxd1c5a37c-21fb-4ce0-bedb-b3c228c1f204.pptx?sfvrsn=df464d75_3) [Word](https://www.dicomstandard.org/docs/librariesprovider2/dicomdocuments/sup222_pc_wsiannotations.docx8791a4cf-8031-4d78-94f5-1fd951f90639.docx?sfvrsn=84dbb85f_3) - 徵求公開意見中
3. [DICOMWeb](https://www.dicomstandard.org/dicomweb)
4. [FHIR Observation](https://www.hl7.org/fhir/observation.html)



                                         M