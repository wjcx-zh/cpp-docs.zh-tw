---
title: "編譯器錯誤 C3490 | Microsoft Docs"
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
  - "C3490"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3490"
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3490
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法修改 'var'，因為正由常數物件存取中  
  
 在 `const` 方法中宣告的 Lambda 運算式不能修改不可變動的成員資料。  
  
### 更正這個錯誤  
  
-   移除方法宣告的 `const` 修飾詞。  
  
## 範例  
 下列範例會產生 C3490，因為它修改了 `const` 方法中的成員變數 `_i`：  
  
```  
// C3490a.cpp // compile with: /c class C { void f() const  { auto x = [=]() { _i = 20; }; // C3490 } int _i; };  
```  
  
## 範例  
 下例會藉由移除方法宣告的 `const` 修飾詞來解析 C3490：  
  
```  
// C3490b.cpp // compile with: /c class C { void f() { auto x = [=]() { _i = 20; }; } int _i; };  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)