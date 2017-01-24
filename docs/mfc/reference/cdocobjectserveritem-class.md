---
title: "CDocObjectServerItem Class | Microsoft Docs"
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
  - "CDocObjectServerItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "CDocObjectServerItem class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocObjectServerItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

特定實作 OLE 伺服器 DocObject 動詞命令的伺服器。  
  
## 語法  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDocObjectServerItem::CDocObjectServerItem](../Topic/CDocObjectServerItem::CDocObjectServerItem.md)|建構 `CDocObjectServerItem` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDocObjectServerItem::GetDocument](../Topic/CDocObjectServerItem::GetDocument.md)|擷取指標包含項目的文件。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CDocObjectServerItem::OnHide](../Topic/CDocObjectServerItem::OnHide.md)|如果此框架嘗試隱藏 DocObject 項目，則會擲回例外狀況。|  
|[CDocObjectServerItem::OnShow](../Topic/CDocObjectServerItem::OnShow.md)|呼叫由架構進行 DocObject 項目就地啟動。  如果項目不是 DocObject，呼叫 [COleServerItem::OnShow](../Topic/COleServerItem::OnShow.md)。|  
  
## 備註  
 `CDocObjectServerItem` 定義可覆寫成員函式: [OnHide](../Topic/CDocObjectServerItem::OnHide.md)、 [OnOpen](http://msdn.microsoft.com/zh-tw/7a9b1363-6ad8-4732-9959-4e35c07644fd)和 [OnShow](../Topic/CDocObjectServerItem::OnShow.md)。  
  
 若要使用 `CDocObjectServerItem`，請確定您的 `COleServerDoc`的 [OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) 覆寫衍生類別 `CDocObjectServerItem` 傳回新的物件。  如果您需要變更項目的任何功能，您可以建立自己的 `CDocObjectServerItem`新執行個體的衍生類別。  
  
 如需 DocObjects 的詳細資訊，請參閱 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) 和 [COleCmdUI](../../mfc/reference/colecmdui-class.md) 《 *MFC*參考》中的。  請參閱 [網際網路第一個步驟:主動式文件](../../mfc/active-documents-on-the-internet.md) 和 [主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## 需求  
 **Header:** afxdocob.h  
  
## 請參閱  
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer Class](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem Class](../../mfc/reference/coledocobjectitem-class.md)