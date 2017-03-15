---
title: "編譯器錯誤 C3291 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3291"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3291"
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 編譯器錯誤 C3291
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'default' : trivial 屬性不能使用這個名稱  
  
 trivial 屬性不可命名為 `default`。 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3291：  
  
```  
// C3291.cpp // compile with: /clr /c ref struct C { property System::String ^ default;   // C3291 property System::String ^ Default;   // OK };  
```