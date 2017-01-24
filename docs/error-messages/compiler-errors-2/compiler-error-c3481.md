---
title: "編譯器錯誤 C3481 | Microsoft Docs"
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
  - "C3481"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3481"
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3481
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': 找不到 Lambda 擷取變數  
  
 編譯器找不到傳遞至 Lambda 運算式擷取清單的變數定義。  
  
### 更正這個錯誤  
  
-   請從 Lambda 運算式的擷取清單移除變數。  
  
## 範例  
 下例會產生 C3481，因為未定義變數 `n`：  
  
```  
// C3481.cpp int main() { [n] {}(); // C3481 }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)