# Software Requirements Specification - BlueJay

Author
:&emsp;Philip Wu  
Version
:&emsp;0.01  
Date
:&emsp;April 12, 2024  

### Copyright &copy; 2022-2024, AIxMed Inc.

### [Contents]
1. [Introduction](#1.)  
1.1. [Purpose](#1.1.)  
1.2. [Intended use and target audience](#1.2.)  
1.3. [Product scope](#1.3.)  
2. [General description](#2.)  
2.1. [User requirements](#2.1.)  
2.2. [Gap analysis](#2.2.)  
2.3. [Product limitations and constraints](#2.3.)  
2.4. [Assumptions and dependencies](#2.4.)  
3. [Features and requirements](#3.)  
3.1. [Features](#3.1.)   
3.2. [Functional](#3.2.)  
3.3. [External interface](#3.3.)  
3.4. [Non-functional](#3.4.)  
4. [Supporting information](#4.)  
- Appendix A.	[References](#0.1.)  
- Appendix B.	[Throughput time of Hscan vesion 0](#0.2.)  

## 1. Introduction <a class="anchor" id="1."></a>
Hscan (an abbreviation for Heuristic Scanning software) is a scanning software to deploy AIxMed patent technology on scanner platform of digital microscopy instrument.  At present, Hscan version 0 is an engineering software for the purpose of internal analysis and field trial.
### 1.1. Purpose <a class="anchor" id="1.1."></a>
Hscan aims for producing good quality of whole slide images available to AIxMed inhouse AI model inference by the implementation of the heuristic scan method as disclosed in [AIxMED patent US11416990B1]
### 1.2. Intended use and target audience <a class="anchor" id="1.2."></a>
This document introduces the gaps between current Hscan features and user requirements and provides a clear plan for development to meet the milestone goals.  The target audience is:  
&nbsp;&nbsp;&nbsp;&nbsp;**Developers**: to assess the workload, define the technolgy stack, and estimate the development costs  
&nbsp;&nbsp;&nbsp;&nbsp;**Tester**: to produce test plan for validating Hscan meets the user requirements  
&nbsp;&nbsp;&nbsp;&nbsp;**Product Manager**: refer to this document for project planning and tracking progress  
### 1.3. Product scope <a class="anchor" id="1.3."></a>
Hscan software implements disease-specific knowledge to the digitization process for mimicking how human experts find atypical cells in current clinical workflow.  The current version of Hscan software can scan entire urine cytology slide fisrt with a lower magnification objective lens to find the suspicious area includeng target cells then scan those suspicious area in detail with a higher maginification objective lens.
According to market expectation and user requirements, this document introduces the software requirements to meet the milestone goals.  The scope of this incremental development of Hscan software is:   
+ improvement plan to enhance scan efficiency
+ UI/UX enhancement 
## 2. General Description <a class="anchor" id="2."></a>
Hscan version 0 provides an easy user interface allow engineers or testers scan whole slide images through auto-mode or manually edit scan mode, ROI and focus dots, available for inhouse AI model inference.
### 2.1. User Requirements <a class="anchor" id="2.1."></a>
Based on the user needs defined in 'Q-POC mk11 User Requirements - AIxMed/Huron' the user requiremetns related to scanner software are as below:  
+ Scan a minimum of 10 cytology slides per hour from common solutions > 97% of the time  
  + Time to First Result -> 10 Minutes  
+ Rapidly image the slide at several "Z" depths  
+ Provides user with digital images that can be analyzed, transported and store electronically  
+ Minimum requirements of software user interface
  + Fully compliant with regulatory requirements
  + Intuitive to use (easy-to-use i.e. unidirectional stepwise workflow, with the exception of user error corrections)
  + A minimal number of keystrokes and/or screens are required in order to run the instrument  
  + A minimal number of keystrokes and/or screens are required in order to perform maintenance of the instrument
+ Data storage (internal)  
  + A minimum of 1,000 scanned slides shall to be stored on the instrument  
+ Slide recognition
  + Specified specimen information will be able to be uploaded to the instrucment via 1 or 2D barcode
    + 2D: Code 128; Codabar
    + 3D: PDF 417; Data Matrix
### 2.2. Gap analysis <a class="anchor" id="2.2."></a>
In order to meet the user requirements, we define the focus area of this milestone of software requirements refer to key attributes in user requirement document, and identify the discrepancies between current statas and desired states, and the actions needed to approach them, as follows.
| Focus Area | Desired Feature | Current State | Action Plan |
|------------|-----------------|---------------|-------------|
| Quality | digital images are available for inhouse AI model inference  | Good/Fair rate (according to cytotech review on UPMC pilot): |- improve bounding-box model |
|  |  |98.63% (Good: 346, Fair: 85, Total: 437)  |  |
|  |  | with manually remove false focus dots   |  |
| Time-to-Result | minimum of 10 cytology slides per hour | refer to [Throughput time](#0.2.) for details | + 40x scan improvement |
|  |  |  | + strip image process |
| Ease-of-Use | recognize specified specimen information | zxing library (Apache License 2.0) supprted Code 128, Codabar, PDF 417, Data Matrix| n.a. |
| Ease-of-use | minumum of 1,000 scanned slides can be stored | more than 3,000 scanned slides (1.2GB per slide image) can be stored |
### Throughput time of Hscan version 0 <a class="anchor" id="0.2."></a>
The scan time 
heuristic batch scan, separate layer images, 02:31:25, average 12:37, 22.5x23.3mm 24 focus dots
heuristic batch scan, stack image, 04:51:13, average 24:16
multiple slices scan. separate layer images, 02:34:08, average 12:50
single layer batch scan, single layer image, 00:45:16, average 03:47

## Revision History  
 Version | Date | Author | Description 
---------|:----:|:------:|----------
 0.01 | 2024-04-17 | Philip Wu | Initial draft 
 0.02 |  |  |  

### Copyright &copy; 2022-2024, AIxMed Inc.

