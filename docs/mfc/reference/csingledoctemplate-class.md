---
title: "CSingleDocTemplate Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSingleDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSingleDocTemplate class"
  - "文件樣板, single"
  - "單一文件介面 (SDI), 應用程式"
  - "範本, SDI"
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSingleDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義實作單一文件介面 \(SDI\) \(SDI\) 的資料範本。  
  
## 語法  
  
```  
class CSingleDocTemplate : public CDocTemplate  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSingleDocTemplate::CSingleDocTemplate](../Topic/CSingleDocTemplate::CSingleDocTemplate.md)|建構 `CSingleDocTemplate` 物件。|  
  
## 備註  
 SDI 應用程式使用主框架視窗中顯示文件，只有一個檔案上次開啟。  
  
 文件樣板定義類別之間有三種類型的關聯性:  
  
-   文件類別，您 **CDocument**從衍生。  
  
-   檢視類別，能夠顯示文件類別資料清單頂端。  您可以從 `CView`、 `CScrollView`、 `CFormView`或 `CEditView`衍生自這個類別。  \(您也可以使用 `CEditView` \)。  
  
-   框架視窗類別，其中包含這個檢視。  對於 SDI 文件範本，您可以從 `CFrameWnd`衍生自這個類別，如果您不需要自訂主框架視窗的行為，您可以使用，而不用 `CFrameWnd` 直接衍生自類別。  
  
 SDI 應用程式通常支援一種類型的文件，因此，只會有一個 `CSingleDocTemplate` 物件。  只有一個檔案上次開啟。  
  
 您不需要呼叫 `CSingleDocTemplate` 的任何成員函式除了建構函式 \(Constructor\)  架構會在內部處理 `CSingleDocTemplate` 物件。  
  
 如需使用 `CSingleDocTemplate`的資訊，請參閱 [文件範本和文件\/檢視建立程序](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC DOCKTOOL 範例](../../top/visual-cpp-samples.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CMultiDocTemplate Class](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)