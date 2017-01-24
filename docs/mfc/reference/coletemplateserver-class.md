---
title: "COleTemplateServer Class | Microsoft Docs"
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
  - "COleTemplateServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation servers [C++], 實作"
  - "COleTemplateServer class"
  - "link containers [C++]"
  - "OLE link containers"
  - "OLE 伺服器應用程式, COleTemplateServer class"
  - "OLE 伺服器應用程式, managing server documents"
  - "伺服器, OLE"
  - "visual editing, 伺服器"
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleTemplateServer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用來編輯伺服器、Automation 伺服程式和連結容器 \(應用程式的 OLE 視覺化 embeddings 支援的連結\)。  
  
## 語法  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleTemplateServer::COleTemplateServer](../Topic/COleTemplateServer::COleTemplateServer.md)|建構 `COleTemplateServer` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleTemplateServer::ConnectTemplate](../Topic/COleTemplateServer::ConnectTemplate.md)|線上文件範本為基礎 `COleObjectFactory` 物件。|  
|[COleTemplateServer::Unregister](../Topic/COleTemplateServer::Unregister.md)|將關聯的資料樣板。|  
|[COleTemplateServer::UpdateRegistry](../Topic/COleTemplateServer::UpdateRegistry.md)|註冊與 OLE 系統登錄資料型別。|  
  
## 備註  
 這個類別是從類別衍生， [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)一般而言，您可以直接使用 `COleTemplateServer` 而不是衍生自類別。  `COleTemplateServer` 使用 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) 物件處理伺服器文件。  請使用 `COleTemplateServer` 實作時，完整的伺服器，也就是說，可以當做獨立應用程式的伺服器上。  完整的伺服器通常是多重文件介面 \(MDI\) \(MDI\) 應用程式，不過，單一文件介面 \(SDI\) \(SDI\) 應用程式支援。  一 `COleTemplateServer` 物件為伺服器資料的每個型別需要應用程式支援，也就是說，如果您的伺服器應用程式支援工作表和圖表，您必須有兩個 `COleTemplateServer` 物件。  
  
 `COleTemplateServer` 覆寫 `COleObjectFactory`定義的 `OnCreateInstance` 成員函式。  此成員函式由架構呼叫建立適當類型的 C\+\+. C\+\+ 物件。  
  
 如需伺服器的詳細資訊，請參閱本文 [伺服器:實作伺服器](../../mfc/servers-implementing-a-server.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [COleObjectFactory Class](../../mfc/reference/coleobjectfactory-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)