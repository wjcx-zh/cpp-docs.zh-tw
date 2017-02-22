---
title: "CMultiDocTemplate Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMultiDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiDocTemplate class"
  - "MDI, 範本"
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CMultiDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義實作多重文件介面 \(MDI\) \(MDI\) 的資料範本。  
  
## 語法  
  
```  
  
class CMultiDocTemplate : public CDocTemplate  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMultiDocTemplate::CMultiDocTemplate](../Topic/CMultiDocTemplate::CMultiDocTemplate.md)|建構 `CMultiDocTemplate` 物件。|  
  
## 備註  
 使用 MDI 應用程式的主框架視窗，因為使用者可以開啟零或多個文件框架視窗，每一個會顯示文件的工作區。  如需 MDI 的詳細描述，請參閱 *Windows 軟體介面設計方針*。  
  
 文件樣板定義在類別中有三種類型的關聯性:  
  
-   文件類別，您 [CDocument](../../mfc/reference/cdocument-class.md)從衍生。  
  
-   檢視類別，能夠顯示文件類別資料清單頂端。  您可以從 [CView](../../mfc/reference/cview-class.md)、 `CScrollView`、 `CFormView`或 `CEditView`衍生自這個類別。  \(您也可以使用 `CEditView` \)。  
  
-   框架視窗類別，其中包含這個檢視。  對於 MDI 文件範本，您可以從 `CMDIChildWnd`衍生自這個類別，或者，如果您不需要，自訂文件框架視窗的行為，您可以使用，而不用 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 直接衍生自類別。  
  
 MDI 應用程式可支援超過一種類型的文件，然後，不同類型的檔案可以同時開啟。  您的應用程式有其支援的每個資料型別的資料範本。  例如，在中，如果您的 MDI 應用程式支援報表和 Word 文件時，應用程式有兩個 `CMultiDocTemplate` 物件。  
  
 當使用者建立新文件時，應用程式會使用文件樣板。  如果應用程式支援超過一種類型的文件，則架構會從文件範本取得支援的文件類型的名稱並將其顯示在新的檔案對話方塊的清單中。  當使用者選取某個資料型別，應用程式會建立資料類別物件、框架視窗物件和檢視物件並互相附加它們。  
  
 您不需要呼叫 `CMultiDocTemplate` 的任何成員函式除了建構函式 \(Constructor\)  架構會在內部處理 `CMultiDocTemplate` 物件。  
  
 如需 `CMultiDocTemplate`的資訊，請參閱 [文件範本和文件\/檢視建立程序](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate Class](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)