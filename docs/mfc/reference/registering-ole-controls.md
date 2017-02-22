---
title: "註冊 OLE 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE 控制項, 註冊"
  - "註冊 OLE 控制項"
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# 註冊 OLE 控制項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE automation 控制項，就像其他 OLE 伺服器物件，可以由其他 OLE 感知應用程式存取。  只要將控制項註冊的型別達成程式庫和類別。  
  
 下列函式可讓您加入和移除控制項的類別、屬性頁和型別程式庫在 Windows 系統註冊資料庫:  
  
### 註冊 OLE 控制項  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](../Topic/AfxOleRegisterControlClass.md)|將控制項的類別加入至登入資料庫。|  
|[AfxOleRegisterPropertyPageClass](../Topic/AfxOleRegisterPropertyPageClass.md)|將控制項屬性頁加入至登入資料庫。|  
|[AfxOleRegisterTypeLib](../Topic/AfxOleRegisterTypeLib.md)|將控制項的型別程式庫到登入資料庫。|  
|[AfxOleUnregisterClass](../Topic/AfxOleUnregisterClass.md)|從系統註冊資料庫移除控制項類別和屬性頁類別。|  
|[AfxOleUnregisterTypeLib](../Topic/AfxOleUnregisterTypeLib.md)|從系統註冊資料庫移除控制項的型別程式庫。|  
  
 `AfxOleRegisterTypeLib` 在 `DllRegisterServer`的控制項 DLL 的實作通常會呼叫。  同樣地， `AfxOleUnregisterTypeLib` 是由 `DllUnregisterServer`呼叫。  `AfxOleRegisterControlClass`、 `AfxOleRegisterPropertyPageClass`和 `AfxOleUnregisterClass` 所控制的 Class Factory 或屬性頁的 `UpdateRegistry` 成員函式通常會呼叫。  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)