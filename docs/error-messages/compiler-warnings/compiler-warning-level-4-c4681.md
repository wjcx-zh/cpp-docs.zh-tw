---
title: "編譯器警告 (層級 4) C4681 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4681"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4681"
ms.assetid: a4e6d85f-3e21-4b45-a551-c23d3c554d3f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 4) C4681
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': coclass 不指定為事件來源的預設介面  
  
 未指定類別的 [source](../../windows/source-cpp.md) 介面。  
  
 下列範例會產生 C4681：  
  
```  
// C4681.cpp // compile with: /W4 /c #define _ATL_ATTRIBUTES 1 #include <atlbase.h> #include <atlcom.h> [module(name="test")]; [dual, uuid("00000000-0000-0000-0000-000000000000")] __interface IEvent { [id(3)] HRESULT myEvent(); }; [object, uuid("00000000-0000-0000-0000-000000000001")] __interface ISource { HRESULT Fire(); }; [ coclass, source(IEvent), default(ISource), // Uncomment the following line to resolve. // default(IEvent), uuid("00000000-0000-0000-0000-000000000002") ] struct CSource : ISource {   // C4681 HRESULT Fire() { return 0; } };  
```