---
title: "編譯器錯誤 C3483 | Microsoft Docs"
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
  - "C3483"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3483"
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3483
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' 已是 Lambda 擷取清單的一部分  
  
 您已多次傳遞相同的變數給 Lambda 運算式的擷取清單。  
  
### 更正這個錯誤  
  
-   請從擷取清單移除變數的所有其他執行個體。  
  
## 範例  
 下列範例會產生 C3483，因為 `n` 變數多次出現在 Lambda 運算式的擷取清單中：  
  
```  
// C3483.cpp int main() { int m = 6, n = 5; [m,n,n] { return n + m; }(); // C3483 }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)