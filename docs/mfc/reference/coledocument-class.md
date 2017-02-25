---
title: "COleDocument Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDocument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDocument class"
  - "文件, OLE"
  - "OLE containers, client items"
  - "OLE 文件"
  - "OLE 文件, 基底類別"
  - "visual editing, OLE document base class"
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleDocument Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援視覺化編輯 OLE 文件的基底類別。  
  
## 語法  
  
```  
class COleDocument : public CDocument  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDocument::COleDocument](../Topic/COleDocument::COleDocument.md)|建構 `COleDocument` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDocument::AddItem](../Topic/COleDocument::AddItem.md)|將項目加入至文件中維護項目的清單。|  
|[COleDocument::ApplyPrintDevice](../Topic/COleDocument::ApplyPrintDevice.md)|將所有用戶端項目的目標裝置列印文件。|  
|[COleDocument::EnableCompoundFile](../Topic/COleDocument::EnableCompoundFile.md)|使用 OLE 要存放的理由文件結構化儲存體檔案格式。|  
|[COleDocument::GetInPlaceActiveItem](../Topic/COleDocument::GetInPlaceActiveItem.md)|傳回目前是就地啟動的 OLE 項目。|  
|[COleDocument::GetNextClientItem](../Topic/COleDocument::GetNextClientItem.md)|取得可逐一查看的下一個用戶端項目。|  
|[COleDocument::GetNextItem](../Topic/COleDocument::GetNextItem.md)|取得可逐一查看的前一個項目。|  
|[COleDocument::GetNextServerItem](../Topic/COleDocument::GetNextServerItem.md)|取得可逐一查看中的伺服器項目。|  
|[COleDocument::GetPrimarySelectedItem](../Topic/COleDocument::GetPrimarySelectedItem.md)|傳回文件中的主要選取的 OLE 項目。|  
|[COleDocument::GetStartPosition](../Topic/COleDocument::GetStartPosition.md)|取得初始位置開始反覆項目。|  
|[COleDocument::HasBlankItems](../Topic/COleDocument::HasBlankItems.md)|空白項目的檢查文件中。|  
|[COleDocument::OnShowViews](../Topic/COleDocument::OnShowViews.md)|呼叫，當文件變成可見或不可見的。|  
|[COleDocument::RemoveItem](../Topic/COleDocument::RemoveItem.md)|從文件中維護的項目清單中移除項目。|  
|[COleDocument::UpdateModifiedFlag](../Topic/COleDocument::UpdateModifiedFlag.md)|如果修改文件，標記為已修改任何包含的 OLE 項目。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDocument::OnEditChangeIcon](../Topic/COleDocument::OnEditChangeIcon.md)|處理變更圖表顯示功能表命令的事件。|  
|[COleDocument::OnEditConvert](../Topic/COleDocument::OnEditConvert.md)|處理內嵌或連結物件的轉換從某種型別到另一個。|  
|[COleDocument::OnEditLinks](../Topic/COleDocument::OnEditLinks.md)|在編輯功能表處理連結的事件順序。|  
|[COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)|傳送附加了文件的郵件訊息。|  
|[COleDocument::OnUpdateEditChangeIcon](../Topic/COleDocument::OnUpdateEditChangeIcon.md)|呼叫框架更新編輯\/變更圖示功能表選項的命令 UI。|  
|[COleDocument::OnUpdateEditLinksMenu](../Topic/COleDocument::OnUpdateEditLinksMenu.md)|呼叫框架更新編輯\/連結功能表的命令 UI 選項。|  
|[COleDocument::OnUpdateObjectVerbMenu](../Topic/COleDocument::OnUpdateObjectVerbMenu.md)|呼叫由架構來更新編輯\/*ObjectName* 功能表的命令 UI 選項和動詞命令功能表的子功能表從編輯\/*ObjectName*存取的。|  
|[COleDocument::OnUpdatePasteLinkMenu](../Topic/COleDocument::OnUpdatePasteLinkMenu.md)|呼叫框架更新貼上特殊功能表選取命令的 UI。|  
|[COleDocument::OnUpdatePasteMenu](../Topic/COleDocument::OnUpdatePasteMenu.md)|呼叫框架更新貼上功能表選取命令的 UI。|  
  
## 備註  
 `COleDocument` **CDocument**從衍生，可以讓您的 OLE 應用程式使用 MFC 程式庫提供的文件\/檢視架構。  
  
 `COleDocument` 視為檔案做為 [CDocItem](../../mfc/reference/cdocitem-class.md) 物件集合至控制代碼 OLE 項目。  因為它們的文件必須可以包含 OLE 項目，容器和伺服器應用程式要求這種結構。  [COleServerItem](../../mfc/reference/coleserveritem-class.md) 和 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 類別，從 `CDocItem`衍生的同時，管理應用程式和 OLE 項目之間的互動。  
  
 如果您正在撰寫簡單的容器應用程式，從 `COleDocument`衍生您的類別檔案。  如果您撰寫支援連結到該檔案中的內嵌項目的一個容器應用程式，從 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)衍生您的類別檔案。  如果您正在撰寫伺服器應用程式或組合容器\/伺服器，從 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)衍生您的類別檔案。  `COleLinkingDoc` 和 `COleServerDoc` 從 `COleDocument`衍生自，因此，這些類別繼承所有服務可在 `COleDocument` 和 **CDocument**。  
  
 若要使用 `COleDocument`，請從衍生類別並加入功能來管理應用程式的非 OLE 資料和內嵌或連結的項目。  如果您定義 `CDocItem`\-儲存應用程式的原生資料的衍生類別，您可以使用 `COleDocument` 定義的預設實作會儲存您的 OLE 和非 OLE 資料。  您也可以設計自己單獨儲存對非 OLE 資料本身的資料結構與 OLE 項目。  如需詳細資訊，請參閱本文。 [容器:複合檔案](../../mfc/containers-compound-files.md)。  
  
 **CDocument** 透過電子郵件傳送支援您的文件中，如果郵件支援 \(MAPI 存在\)。  `COleDocument` 更新 [OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md) 正確處理複合文件。  如需詳細資訊，請參閱 Microsoft 知識庫文件 [MAPI](../../mfc/mapi.md) 和 [在 MFC 的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 砂的寬線](../../top/visual-cpp-samples.md)   
 [MFC MFCBIND 範例](../../top/visual-cpp-samples.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)