---
title: "COleCmdUI Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "COleCmdUI class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# COleCmdUI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 MFC 的方法可以更新使用者介面物件狀態與應用程式相關 `IOleCommandTarget`前置的功能。  
  
## 語法  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleCmdUI::COleCmdUI](../Topic/COleCmdUI::COleCmdUI.md)|建構 `COleCmdUI` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleCmdUI::Enable](../Topic/COleCmdUI::Enable.md)|設定或明確啟用命令旗標。|  
|[COleCmdUI::SetCheck](../Topic/COleCmdUI::SetCheck.md)|設定已開啟或關閉切換命令的狀態。|  
|[COleCmdUI::SetText](../Topic/COleCmdUI::SetText.md)|傳回命令的文字名稱或狀態字串。|  
  
## 備註  
 在沒有啟用 DocObjects 的應用程式，在中，當使用者檢視在應用程式中， MFC 的功能表處理 **UPDATE\_COMMAND\_UI** notifcations。  提供可以操作反映特定命令的狀態告知的每一 [CCmdUI](../../mfc/reference/ccmdui-class.md) 物件。  不過，在中，當您的應用程式可以存取 DocObjects 時， MFC 會處理序 **UPDATE\_OLE\_COMMAND\_UI** 告知和指派 `COleCmdUI` 物件。  
  
 `COleCmdUI` 允許 DocObject 接收來自其容器的使用者介面 \(UI\) 的命令 \(例如， FileNew 開啟，列印，等\)，並允許容器接收來自 DocObject 之使用者介面的命令。  雖然 `IDispatch` 可以用來將相同的命令， `IOleCommandTarget` 提供簡單的方式來進行查詢，並執行，因為它依賴標準命令集，通常不搭配任何引數，而且沒有型別資訊是包含的。  `COleCmdUI` 可用來啟用更新，並將 DocObject 使用者介面命令的其他屬性。  當您想要叫用命令時，請呼叫 [COleServerDoc::OnExecOleCmd](../Topic/COleServerDoc::OnExecOleCmd.md)。  
  
 如需 DocObjects 的詳細資訊，請參閱 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) 和 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。  請參閱 [網際網路第一個步驟:主動式文件](../../mfc/active-documents-on-the-internet.md) 和 [主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
## 繼承階層架構  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## 需求  
 **Header:** afxdocobj.h  
  
## 請參閱  
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)