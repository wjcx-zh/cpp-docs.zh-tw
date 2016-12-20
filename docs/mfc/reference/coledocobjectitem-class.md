---
title: "COleDocObjectItem Class | Microsoft Docs"
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
  - "COleDocObjectItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDocObjectItem class"
  - "containment"
  - "containment, doc object"
  - "doc object containment"
  - "document object containment"
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDocObjectItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作主動式文件內含項目。  
  
## 語法  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDocObjectItem::COleDocObjectItem](../Topic/COleDocObjectItem::COleDocObjectItem.md)|建構 `COleDocObject` 項目。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDocObjectItem::DoDefaultPrinting](../Topic/COleDocObjectItem::DoDefaultPrinting.md)|使用預設的印表機設定，會列印容器應用程式的文件。|  
|[COleDocObjectItem::ExecCommand](../Topic/COleDocObjectItem::ExecCommand.md)|執行使用者指定的命令。|  
|[COleDocObjectItem::GetActiveView](../Topic/COleDocObjectItem::GetActiveView.md)|擷取文件的現用檢視表。|  
|[COleDocObjectItem::GetPageCount](../Topic/COleDocObjectItem::GetPageCount.md)|擷取頁面數目容器應用程式的文件。|  
|[COleDocObjectItem::OnPreparePrinting](../Topic/COleDocObjectItem::OnPreparePrinting.md)|容器應用程式的文件列印的準備工作。|  
|[COleDocObjectItem::OnPrint](../Topic/COleDocObjectItem::OnPrint.md)|列印容器應用程式的文件。|  
|[COleDocObjectItem::QueryCommand](../Topic/COleDocObjectItem::QueryCommand.md)|使用者介面事件產生的一或多個命令狀況的查詢。|  
|[COleDocObjectItem::Release](../Topic/COleDocObjectItem::Release.md)|若已開啟，釋放與 OLE 連結項目的連接並關閉。  不會終結用戶端項目。|  
  
## 備註  
 在 MFC 中，主動式文件都需處理規則，就地編輯內嵌，但具有下列差異:  
  
-   `COleDocument`衍生的類別仍然會維護目前內嵌項目的清單，不過，這些項目可能是 `COleDocObjectItem`衍生項目。  
  
-   當主動式文件為作用中時，它會佔用整個檢視的工作區，以便就地啟動時。  
  
-   主動式文件容器有 **說明** 功能表的完全控制。  
  
-   **說明** 功能表包含主動式文件容器和伺服器的功能表項目。  
  
 由於主動式文件容器擁有 **說明** 功能表容器，可以將 \[伺服器 **說明** 功能表訊息負責伺服器。  這項整合可由 `COleDocObjectItem`處理。  
  
 如需功能表合併及主動式文件啟動的詳細資訊，請參閱 [現用文件內含項目](../../mfc/active-document-containment.md)概觀。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC MFCBIND 範例](../../top/visual-cpp-samples.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem Class](../../mfc/reference/cdocobjectserveritem-class.md)