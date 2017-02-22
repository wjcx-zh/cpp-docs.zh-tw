---
title: "編譯器錯誤 C3482 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3482"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3482"
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3482
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'this' 在非靜態成員函式內只能做為 Lambda 擷取  
  
 您無法將 `this` 傳遞給靜態方法或全域函式中所宣告之 Lambda 運算式的擷取清單。  
  
### 更正這個錯誤  
  
-   將封入函式轉換成非靜態方法，或  
  
-   從 Lambda 運算式的擷取清單中移除 `this` 指標。  
  
## 範例  
 下列範例會產生 C3482：  
  
```  
// C3482.cpp // compile with: /c class C { public: static void staticMethod() { [this] {}(); // C3482 } };  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)