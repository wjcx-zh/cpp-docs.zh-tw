---
title: "事件接收對應 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件接收對應"
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 事件接收對應
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當內嵌 OLE automation 控制項引發事件時，控制項的容器使用由 MFC 提供的稱為事件接收對應的機制接收事件。  這個事件接收對應指定每個特定事件的處理常式以及那些事件函式的參數。  如需事件接收對應的詳細資訊，請參閱本文件的 [ActiveX 控制項容器](../../mfc/activex-control-containers.md)。  
  
### 事件接收對應  
  
|||  
|-|-|  
|[BEGIN\_EVENTSINK\_MAP](../Topic/BEGIN_EVENTSINK_MAP.md)|開始接收對應的定義。|  
|[DECLARE\_EVENTSINK\_MAP](../Topic/DECLARE_EVENTSINK_MAP.md)|宣告事件接收對應。|  
|[END\_EVENTSINK\_MAP](../Topic/END_EVENTSINK_MAP.md)|關閉事件接收對應的定義。|  
|[ON\_EVENT](../Topic/ON_EVENT.md)|定義特定事件的事件處理常式。|  
|[ON\_EVENT\_RANGE](../Topic/ON_EVENT_RANGE.md)|定義一組 OLE automation 控制項引發的特定事件的事件處理常式。|  
|[ON\_EVENT\_REFLECT](../Topic/ON_EVENT_REFLECT.md)|在由控制項的容器處理之前，接收控制項引發的事件。|  
|[ON\_PROPNOTIFY](../Topic/ON_PROPNOTIFY.md)|為處理 OLE automation 控制項的屬性通知定義處理常式。|  
|[ON\_PROPNOTIFY\_RANGE](../Topic/ON_PROPNOTIFY_RANGE.md)|定義處理來自一組 OLE automation 控制項的屬性通知處理常式。|  
|[ON\_PROPNOTIFY\_REFLECT](../Topic/ON_PROPNOTIFY_REFLECT.md)|在由控制項的容器處理前，接收控制項傳送的屬性通知。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)