---
title: "Using IDispEventSimpleImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDispEventSimpleImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventSimpleImpl class, 使用"
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Using IDispEventSimpleImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用 `IDispEventSimpleImpl` 處理事件時，您需要:  
  
-   從 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)衍生您的類別。  
  
-   將 [事件接收對應](../Topic/BEGIN_SINK_MAP.md) 加入至類別。  
  
-   定義描述事件的 [\_ATL\_FUNC\_INFO](../atl/reference/atl-func-info-structure.md) 結構。  
  
-   使用 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md) 巨集，將項目加入至事件接收對應。  
  
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
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/CPP/using-idispeventsimpleimpl_1.h)]  
  
 從這個型別是在這個範例中實際的程式庫的唯一資訊是文字 **應用程式** 物件和 **ApplicationEvents** 介面的 IID 的 CLSID。  這項資訊只能在編譯時期。  
  
 下列程式碼會顯示在 Simple.h。  相關的程式碼加上註解注意:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/CPP/using-idispeventsimpleimpl_2.h)]  
  
 下列程式碼是從 Simple.cpp:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/CPP/using-idispeventsimpleimpl_3.cpp)]  
  
## 請參閱  
 [事件處理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling 範例](../top/visual-cpp-samples.md)