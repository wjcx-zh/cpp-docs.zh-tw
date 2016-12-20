---
title: "編譯器錯誤 C2695 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2695"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2695"
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2695
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function1': 覆寫虛擬函式和 'function2' 的不同只在呼叫慣例  
  
 衍生類別內的函式簽章，不能覆寫基底類別內的函式和變更呼叫慣例 \(Calling Convention\)。  
  
 下列範例會產生 C2695：  
  
```  
// C2695.cpp  
class C {  
   virtual void __fastcall func();  
};  
  
class D : public C {  
   virtual void __clrcall func();   // C2695  
};  
```