# Track#6 - Genomics

### 聯測要求

* Support the sending of the MolecularSequence resource/genetics profiles
* Support the receiving and processing of the MolecularSequence resource/genetics profiles
* Operations: create, delete, search and update.

### 資安授權機制
  - 支援JWT機制
  - 支援權限控管機制

### Role

* MolecularSequence Creator
* MolecularSequence Consumer
* Genetics profile Creator
* Genetics profile Consumer


### Scenarios

#### Scenario 1 Create a New MolecularSequence and Observation (Source)

* Action: (FHIR Client) Create a sequence instance and a genetic-profile-based observation instance to represent genetics data and interpretations (DNA variant, RNA sequence, structural variant, etc).
* Precondition: The sequence instance and observation instance do not exist in service prior to action.
* Success Criteria: Sequence and observation instances created correctly on server and in the desired format.


#### Scenario 2 Retrieve Clinical Sequencing - Germline Testing (Consumer)

* Action: (FHIR Client) Search target genetic-profile-based observation with given patient ID.
* Precondition: Relevant patient and observations have been created.
* Success Criteria: A bundle of genetics observations from germline analysis of that patient are returned.
* Bonus point: More parameters can be added for searching

### 公開技術規格 : https://mitw.dicom.org.tw/preconnectathon6.html
