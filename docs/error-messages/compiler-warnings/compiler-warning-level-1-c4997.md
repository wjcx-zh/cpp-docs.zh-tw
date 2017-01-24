---
title: "編譯器警告 (層級 1) C4997 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4997"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4997"
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4997
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': coclass 未實作 COM 介面或虛擬介面  
  
 使用 [coclass](../../windows/coclass.md) 屬性所標示的類別未實作介面。  
  
 下列範例會產生 C4997：  
  
```  
// C4997.cpp // compile with: /WX // to resolve this C4997, uncomment all code #include <objbase.h> [ object ] __interface I { HRESULT func(); }; [ coclass ] struct C /*: I*/ { /* HRESULT func() { return S_OK; } */ };   // C4997  
```