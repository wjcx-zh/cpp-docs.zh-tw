---
title: "CDocTemplate Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDocTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocTemplate class"
  - "文件樣板"
  - "範本, 文件"
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDocTemplate Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義資料範本之基本功能的抽象基底類別。  
  
## 語法  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDocTemplate::CDocTemplate](../Topic/CDocTemplate::CDocTemplate.md)|建構 `CDocTemplate` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDocTemplate::AddDocument](../Topic/CDocTemplate::AddDocument.md)|將文件加入至樣板。|  
|[CDocTemplate::CloseAllDocuments](../Topic/CDocTemplate::CloseAllDocuments.md)|關閉所有文件與此範本。|  
|[CDocTemplate::CreateNewDocument](../Topic/CDocTemplate::CreateNewDocument.md)|建立新的文件。|  
|[CDocTemplate::CreateNewFrame](../Topic/CDocTemplate::CreateNewFrame.md)|建立包含文件和檢視的新的框架視窗。|  
|[CDocTemplate::CreateOleFrame](../Topic/CDocTemplate::CreateOleFrame.md)|建立 OLE 啟用框架視窗。|  
|[CDocTemplate::CreatePreviewFrame](../Topic/CDocTemplate::CreatePreviewFrame.md)|建立用來預覽豐富的子框架。|  
|[CDocTemplate::GetDocString](../Topic/CDocTemplate::GetDocString.md)|擷取字串與文件類型。|  
|[CDocTemplate::GetFirstDocPosition](../Topic/CDocTemplate::GetFirstDocPosition.md)|擷取第一個檔案的位置與此範本。|  
|[CDocTemplate::GetNextDoc](../Topic/CDocTemplate::GetNextDoc.md)|擷取文件位置和下一個。|  
|[CDocTemplate::InitialUpdateFrame](../Topic/CDocTemplate::InitialUpdateFrame.md)|初始化框架視窗和選擇性地讓它成為可見。|  
|[CDocTemplate::LoadTemplate](../Topic/CDocTemplate::LoadTemplate.md)|載入指定的 `CDocTemplate` 或衍生類別中的資源。|  
|[CDocTemplate::MatchDocType](../Topic/CDocTemplate::MatchDocType.md)|判斷確定要相符的資料型別與範本之間。|  
|[CDocTemplate::OpenDocumentFile](../Topic/CDocTemplate::OpenDocumentFile.md)|開啟路徑名稱所指定的檔案。|  
|[CDocTemplate::RemoveDocument](../Topic/CDocTemplate::RemoveDocument.md)|從範本移除文件。|  
|[CDocTemplate::SaveAllModified](../Topic/CDocTemplate::SaveAllModified.md)|儲存修改過的所有文件與此範本。|  
|[CDocTemplate::SetContainerInfo](../Topic/CDocTemplate::SetContainerInfo.md)|在就地編輯一個 OLE 項目時，會判斷 OLE 容器的資源。|  
|[CDocTemplate::SetDefaultTitle](../Topic/CDocTemplate::SetDefaultTitle.md)|在文件視窗的標題列中顯示預設標題。|  
|[CDocTemplate::SetPreviewInfo](../Topic/CDocTemplate::SetPreviewInfo.md)|在處理預覽處理常式以外的設定。|  
|[CDocTemplate::SetServerInfo](../Topic/CDocTemplate::SetServerInfo.md)|當嵌入至伺服器資料或就地編輯時，判斷某個資源和類別。|  
  
## 備註  
 您通常會在應用程式的 `InitInstance` 函式的實作的一或多個文件樣板。  文件樣板定義在類別中有三種類型的關聯性:  
  
-   文件類別，您 **CDocument**從衍生。  
  
-   檢視類別，能夠顯示文件類別資料清單頂端。  您可以從 `CView`、 `CScrollView`、 `CFormView`或 `CEditView`衍生自這個類別。  \(您也可以使用 `CEditView` \)。  
  
-   框架視窗類別，其中包含這個檢視。  對於單一文件介面 \(SDI\) \(SDI\) 應用程式，請從 `CFrameWnd`衍生自這個類別。  如果是多重文件介面 \(MDI\) \(MDI\) 應用程式，請從 `CMDIChildWnd`衍生自這個類別。  如果您不需要自訂框架視窗的行為，您可以使用 `CFrameWnd` 或 `CMDIChildWnd` 直接，而不需從衍生的類別。  
  
 您的應用程式有其支援的每種資料型別的資料範本。  例如，在中，如果應用程式支援報表和 Word 文件時，應用程式有兩種文件樣板物件。  每個文件樣板與建立和管理其類型的所有文件管理。  
  
 文件樣板儲存指標至文件、檢視和框架視窗類別的 `CRuntimeClass` 物件。  以建構文件樣板時，這些 `CRuntimeClass` 物件指定。  
  
 文件樣板包含資源的 ID 搭配文件類型 \(例如功能表、圖示或快速鍵 \(Accelerator\) 對應表資源\)。  文件樣板也會包含其資料型別的其他資訊。  這些包括文件類型 \(例如， 「右邊」\) 和副檔名 \(例如， 「.xls」\) 的名稱。  或者，也可以包含應用程式的使用者介面、Windows 文件管理員及物件連結與嵌入 \(OLE\) 支援使用的其他資料。  
  
 如果您的應用程式是一個 OLE 容器和伺服器，文件範本也會定義在就地啟動時使用的功能表的 ID。  如果您的應用程式是一個 OLE 伺服器，文件樣板定義在就地啟動時使用的功能表和工具列的 ID。  您可以呼叫 `SetContainerInfo` 和 `SetServerInfo`指定這些其他 OLE 資源。  
  
 由於 `CDocTemplate` 是抽象類別，所以您無法直接使用類別。  一般的應用程式使用一或兩 `CDocTemplate`\- MFC 程式庫提供的衍生類別: `CSingleDocTemplate`，實作 SDI、MDI `CMultiDocTemplate`，實作。  請參閱這些類別。如需使用資料範本的詳細資訊。  
  
 如果您的應用程式需要的功能是不同的 SDI 或 MDI 中使用者介面範例，您可以從 `CDocTemplate`衍生您的類別。  
  
 如需 `CDocTemplate`的資訊，請參閱 [文件範本和文件\/檢視建立程序](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSingleDocTemplate Class](../../mfc/reference/csingledoctemplate-class.md)   
 [CMultiDocTemplate Class](../../mfc/reference/cmultidoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [CEditView Class](../../mfc/reference/ceditview-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)