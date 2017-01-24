---
title: "應用程式控制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式控制"
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式控制
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 要求對應用程式及其物件的基本控制項。  這個 OLE 系統 DLL 必須能夠啟動，並自動發行應用程式，請調整其物件的產生和修改，依此類推。  本主題中的函式符合這些需求。  除了由這個 OLE 系統 DLL 之外，必須由應用程式有時會呼叫這些函式。  
  
### 應用程式控制  
  
|||  
|-|-|  
|[AfxOleCanExitApp](../Topic/AfxOleCanExitApp.md)|指示應用程式是否可以結束。|  
|[AfxOleGetMessageFilter](../Topic/AfxOleGetMessageFilter.md)|擷取應用程式的目前訊息篩選條件。|  
|[AfxOleGetUserCtrl](../Topic/AfxOleGetUserCtrl.md)|擷取目前使用者控制旗標。|  
|[AfxOleSetUserCtrl](../Topic/AfxOleSetUserCtrl.md)|設定或清除使用者控制旗標。|  
|[AfxOleLockApp](../Topic/AfxOleLockApp.md)|將作用中物件的數目的框架的全域物件中應用程式的。|  
|[必須](../Topic/AfxOleUnlockApp.md)|會使用中物件的數目的框架的計數在應用程式的。|  
|[AfxOleRegisterServerClass](../Topic/AfxOleRegisterServerClass.md)|註冊在 OLE 系統註冊的伺服器。|  
|[AfxOleSetEditMenu](../Topic/AfxOleSetEditMenu.md)|實作 *typename* 物件命令的使用者介面。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)