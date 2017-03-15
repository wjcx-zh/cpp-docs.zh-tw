---
title: "Using IDispEventImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventImpl class, 使用"
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Using IDispEventImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用 `IDispEventImpl` 處理事件時，您需要:  
  
-   從 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)衍生您的類別。  
  
-   將 [事件接收對應](../Topic/BEGIN_SINK_MAP.md) 加入至類別。  
  
-   使用 [SINK\_ENTRY](../Topic/SINK_ENTRY.md) 或 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md) 巨集，將項目加入至事件接收對應。  
  
-   實作方法要處理有興趣。  
  
-   建議和 unadvise 事件來源。  
  
## 範例  
 下列範例會顯示如何處理文字的 **應用程式** 物件所引發的事件。 **DocumentChange** 這個事件會定義為 **ApplicationEvents** 分配介面的方法。  
  
 這個範例是 [ATLEventHandling 範例](../top/visual-cpp-samples.md)。  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 這個範例會使用 `#import` 從文字檔中產生的型別程式庫所需的標頭檔。  如果您想要使用文字其他版本的範例，您必須指定正確的 mso dll 檔案。  例如， Office 2000 提供 mso9.dll，並提供 Office XP mso.dll。  這個程式碼會從 stdafx.h 簡化:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/CPP/using-idispeventimpl_1.h)]  
  
 下列程式碼會顯示在 NotSoSimple.h。  相關的程式碼加上註解注意:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/CPP/using-idispeventimpl_2.h)]  
  
## 請參閱  
 [事件處理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling 範例](../top/visual-cpp-samples.md)