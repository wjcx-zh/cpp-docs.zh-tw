---
title: "CDocObjectServer Class | Microsoft Docs"
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
  - "CDocObjectServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "CDocObjectServer class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDocObjectServer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作必要的額外 OLE 介面進行一般 `COleDocument` 伺服器完整 DocObject 伺服器: `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。  
  
## 語法  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDocObjectServer::CDocObjectServer](../Topic/CDocObjectServer::CDocObjectServer.md)|建構 `CDocObjectServer` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDocObjectServer::ActivateDocObject](../Topic/CDocObjectServer::ActivateDocObject.md)|啟動文件伺服器物件，則傳回，而不顯示它。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CDocObjectServer::OnActivateView](../Topic/CDocObjectServer::OnActivateView.md)|顯示 DocObject 檢視。|  
|[CDocObjectServer::OnApplyViewState](../Topic/CDocObjectServer::OnApplyViewState.md)|還原 DocObject 檢視狀態。|  
|[CDocObjectServer::OnSaveViewState](../Topic/CDocObjectServer::OnSaveViewState.md)|儲存 DocObject 檢視狀態。|  
  
## 備註  
 `CDocObjectServer` 從 `CCmdTarget` 和工作嚴格地取得有 `COleServerDoc` 公開介面。  
  
 DocObject 伺服器文件可以包含 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) 物件，表示伺服器介面的 DocObject 項目。  
  
 若要自訂的 DocObject 伺服器，從 `CDocObjectServer` 衍生您的類別並覆寫其檢視設定函式、 [OnActivateView](../Topic/CDocObjectServer::OnActivateView.md)、 [OnApplyViewState](../Topic/CDocObjectServer::OnApplyViewState.md)和 [OnSaveViewState](../Topic/CDocObjectServer::OnSaveViewState.md)。  您必須提供自己的類別的新執行個體以回應架構呼叫。  
  
 如需 DocObjects 的詳細資訊，請參閱 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) 和 [COleCmdUI](../../mfc/reference/colecmdui-class.md) 《 *MFC*參考》中的。  請參閱 [網際網路第一個步驟:主動式文件](../../mfc/active-documents-on-the-internet.md) 和 [主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
 請參閱下列知識庫 \(Knowledge Base\) 文件:  
  
-   Q247382:\<PRB:控制項的工具提示在 ActiveX 文件 \(ActiveX Document Server 容器隱藏  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## 需求  
 **Header:** afxdocob.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem Class](../../mfc/reference/cdocobjectserveritem-class.md)