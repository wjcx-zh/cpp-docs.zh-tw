---
title: "編譯器錯誤 C3491 | Microsoft Docs"
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
  - "C3491"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3491"
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3491
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': 無法在不可變的 Lambda 中修改傳值方式擷取  
  
 不可變的 Lambda 運算式不能修改以傳值方式擷取的變數的值。  
  
### 更正這個錯誤  
  
-   請使用 `mutable` 關鍵字宣告 Lambda 運算式，或  
  
-   以傳址方式將變數傳遞到 Lambda 運算式的擷取清單。  
  
## 範例  
 下列範例會產生 C3491，因為不可變的 Lambda 運算式主體修改了擷取變數 `m`：  
  
```  
// C3491a.cpp int main() { int m = 55; [m](int n) { m = n; }(99); // C3491 }  
```  
  
## 範例  
 下列範例藉由使用 `mutable` 關鍵字宣告 Lambda 運算式，解決了 C3491：  
  
```  
// C3491b.cpp int main() { int m = 55; [m](int n) mutable { m = n; }(99); }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)