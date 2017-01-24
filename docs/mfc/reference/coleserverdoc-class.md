---
title: "COleServerDoc Class | Microsoft Docs"
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
  - "COleServerDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleServerDoc class"
  - "container/server applications"
  - "OLE containers, server documents"
  - "OLE 伺服器應用程式, managing server documents"
  - "OLE server documents"
  - "server documents, OLE"
  - "伺服器, OLE"
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleServerDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 伺服器資料的基底類別。  
  
## 語法  
  
```  
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleServerDoc::COleServerDoc](../Topic/COleServerDoc::COleServerDoc.md)|建構 `COleServerDoc` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleServerDoc::ActivateDocObject](../Topic/COleServerDoc::ActivateDocObject.md)|啟動相關的 DocObject 文件。|  
|[COleServerDoc::ActivateInPlace](../Topic/COleServerDoc::ActivateInPlace.md)|啟動就地編輯的文件。|  
|[COleServerDoc::DeactivateAndUndo](../Topic/COleServerDoc::DeactivateAndUndo.md)|停用伺服器的使用者介面。|  
|[COleServerDoc::DiscardUndoState](../Topic/COleServerDoc::DiscardUndoState.md)|中止復原狀態資訊。|  
|[COleServerDoc::GetClientSite](../Topic/COleServerDoc::GetClientSite.md)|擷取指標到基礎 `IOleClientSite` 介面。|  
|[COleServerDoc::GetEmbeddedItem](../Topic/COleServerDoc::GetEmbeddedItem.md)|傳回指向代表整份文件的項目。|  
|[COleServerDoc::GetItemClipRect](../Topic/COleServerDoc::GetItemClipRect.md)|傳回就地編輯目前的裁剪方框。|  
|[COleServerDoc::GetItemPosition](../Topic/COleServerDoc::GetItemPosition.md)|傳回目前位置矩形，相對於容器應用程式的工作區，就地編輯。|  
|[COleServerDoc::GetZoomFactor](../Topic/COleServerDoc::GetZoomFactor.md)|傳回以像素為單位的縮放因數。|  
|[COleServerDoc::IsDocObject](../Topic/COleServerDoc::IsDocObject.md)|判斷文件是否屬於 DocObject。|  
|[COleServerDoc::IsEmbedded](../Topic/COleServerDoc::IsEmbedded.md)|指出文件是在個別的檔案或容器執行內嵌。|  
|[COleServerDoc::IsInPlaceActive](../Topic/COleServerDoc::IsInPlaceActive.md)|不過，如果項目之後，目前已啟動 `TRUE` 傳回。|  
|[COleServerDoc::NotifyChanged](../Topic/COleServerDoc::NotifyChanged.md)|容器告知使用者變更了文件。|  
|[COleServerDoc::NotifyClosed](../Topic/COleServerDoc::NotifyClosed.md)|容器告知使用者關閉文件。|  
|[COleServerDoc::NotifyRename](../Topic/COleServerDoc::NotifyRename.md)|容器告知使用者重新命名此文件。|  
|[COleServerDoc::NotifySaved](../Topic/COleServerDoc::NotifySaved.md)|容器通知使用者已儲存文件。|  
|[COleServerDoc::OnDeactivate](../Topic/COleServerDoc::OnDeactivate.md)|呼叫框架，當使用者停用就地啟動的項目。|  
|[COleServerDoc::OnDeactivateUI](../Topic/COleServerDoc::OnDeactivateUI.md)|呼叫這個框架終結控制項和其他使用者介面項目就地啟動時建立。|  
|[COleServerDoc::OnDocWindowActivate](../Topic/COleServerDoc::OnDocWindowActivate.md)|呼叫框架，該容器的文件框架視窗中啟用或停用。|  
|[COleServerDoc::OnResizeBorder](../Topic/COleServerDoc::OnResizeBorder.md)|呼叫框架，該容器應用程式的框架視窗或文件視窗調整大小。|  
|[COleServerDoc::OnShowControlBars](../Topic/COleServerDoc::OnShowControlBars.md)|呼叫由架構來顯示或隱藏就地編輯的控制列。|  
|[COleServerDoc::OnUpdateDocument](../Topic/COleServerDoc::OnUpdateDocument.md)|呼叫框架，當為內嵌項目的伺服器資料儲存，更新項目的容器的複本。|  
|[COleServerDoc::RequestPositionChange](../Topic/COleServerDoc::RequestPositionChange.md)|變更就地編輯框架的位置。|  
|[COleServerDoc::SaveEmbedding](../Topic/COleServerDoc::SaveEmbedding.md)|呼叫容器應用程式儲存文件。|  
|[COleServerDoc::ScrollContainerBy](../Topic/COleServerDoc::ScrollContainerBy.md)|移至 Bin 資料。|  
|[COleServerDoc::UpdateAllItems](../Topic/COleServerDoc::UpdateAllItems.md)|容器告知使用者變更了文件。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleServerDoc::CreateInPlaceFrame](../Topic/COleServerDoc::CreateInPlaceFrame.md)|呼叫以建立畫面格就地編輯的框架視窗。|  
|[COleServerDoc::DestroyInPlaceFrame](../Topic/COleServerDoc::DestroyInPlaceFrame.md)|呼叫框架終結就地編輯的框架視窗。|  
|[COleServerDoc::GetDocObjectServer](../Topic/COleServerDoc::GetDocObjectServer.md)|覆寫這個函式會建立新的物件 `CDocObjectServer` 並指出文件是 DocObject\) 容器。|  
|[COleServerDoc::OnClose](../Topic/COleServerDoc::OnClose.md)|呼叫由架構，在容器需要關閉文件。|  
|[COleServerDoc::OnExecOleCmd](../Topic/COleServerDoc::OnExecOleCmd.md)|執行指定的命令或顯示此命令的說明。|  
|[COleServerDoc::OnFrameWindowActivate](../Topic/COleServerDoc::OnFrameWindowActivate.md)|呼叫框架，該容器的框架視窗中啟用或停用。|  
|[COleServerDoc::OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md)|呼叫以取得代表整份文件的 `COleServerItem` ;用來取得內嵌項目。  需要的實作。|  
|[COleServerDoc::OnReactivateAndUndo](../Topic/COleServerDoc::OnReactivateAndUndo.md)|呼叫框架繼續在就地編譯期間所做的變更。|  
|[COleServerDoc::OnSetHostNames](../Topic/COleServerDoc::OnSetHostNames.md)|呼叫由架構，在容器設定內嵌物件的視窗標題。|  
|[COleServerDoc::OnSetItemRects](../Topic/COleServerDoc::OnSetItemRects.md)|呼叫框架放置在容器應用程式視窗內的就地編輯框架視窗。|  
|[COleServerDoc::OnShowDocument](../Topic/COleServerDoc::OnShowDocument.md)|呼叫由架構來顯示或隱藏文件。|  
  
## 備註  
 伺服器文件可以包含 [COleServerItem](../../mfc/reference/coleserveritem-class.md) 物件，表示伺服器介面內嵌或連結的項目。  當伺服器應用程式是由容器啟動編輯內嵌項目時，項目的形式載入其伺服器資料; `COleServerDoc` 物件包含 `COleServerItem` 物件，包含整個文件。  當伺服器應用程式是由容器啟動編輯連結的項目時，現有的資料從磁碟載入，文件內容的部分反白顯示表示連結的項目。  
  
 `COleServerDoc` 物件也可以包含 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 類別中的項目。  這可讓您建立容器伺服器應用程式。  會 `COleServerItem` 服務物件時，這個架構提供了函式適當地儲存 `COleClientItem` 項目。  
  
 如果您的伺服器應用程式不支援連結，伺服器資料只一定會包含伺服器項目，表示整個內嵌物件做為文件。  如果您的伺服器應用程式來支援介面，它必須建立伺服器項目，每次選取範圍複製到剪貼簿。  
  
 若要使用 `COleServerDoc`，請從衍生類別並實作 [OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) 成員函式，可讓您的伺服器支援內嵌項目。  從 `COleServerItem` 衍生類別實作在文件中的項目，並傳回該類別物件從 `OnGetEmbeddedItem`的。  
  
 若要支援連結的項目， `COleServerDoc` 提供 [OnGetLinkedItem](../Topic/COleLinkingDoc::OnGetLinkedItem.md) 成員函式。  如果您有處理文件項目的方式，您可以使用預設實作或覆寫它。  
  
 您需要 `COleServerDoc`\-伺服器資料的每個型別的衍生類別讓應用程式支援。  例如，在中，如果您的伺服器應用程式支援工作表和圖表，您需要兩 `COleServerDoc`衍生類別。  
  
 如需伺服器的詳細資訊，請參閱本文 [伺服器:實作伺服器](../../mfc/servers-implementing-a-server.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [COleLinkingDoc Class](../../mfc/reference/colelinkingdoc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [COleLinkingDoc Class](../../mfc/reference/colelinkingdoc-class.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)