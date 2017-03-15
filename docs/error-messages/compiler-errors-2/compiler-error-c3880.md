---
title: "編譯器錯誤 C3880 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3880"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3880"
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C3880
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : 不可為常值資料成員  
  
 [literal](../../windows/literal-cpp-component-extensions.md) 屬性的型別必須是下列其中一種型別，或是在編譯時期轉換成下列其中一種型別：  
  
-   整數類資料型別  
  
-   string  
  
-   有整數或基礎型別的列舉型別  
  
 下列範例會產生 C3880：  
  
```  
// C3880.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   literal System::Decimal staticConst1 = 10;   // C3880  
   literal int staticConst2 = 10;   // OK  
};  
```