---
title: "編譯器警告 C4693 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4693"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4693"
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 C4693
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': 密封的抽象類別不能有任何執行個體成員 'Test'  
  
 如果類型標記為 [sealed](../../windows/sealed-cpp-component-extensions.md) 和 [abstract](../../windows/abstract-cpp-component-extensions.md)，就只能有靜態成員。  
  
## 範例  
 下例會產生 C4693。  
  
```  
// C4693.cpp // compile with: /clr /c public ref class Public_Ref_Class sealed abstract { public: void Test() {}   // C4693 static void Test2() {}   // OK };  
```