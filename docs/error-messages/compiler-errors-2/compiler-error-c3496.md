---
title: "編譯器錯誤 C3496 | Microsoft Docs"
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
  - "C3496"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3496"
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3496
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'this' 一定以傳值方式擷取: 已忽略 '&'  
  
 您不能以傳址方式來擷取 `this` 指標。  
  
### 更正這個錯誤  
  
-   請以傳值方式來擷取 `this` 指標。  
  
## 範例  
 下列範例會產生 C3496，因為 `this` 指標的參考出現在 Lambda 運算式的擷取清單中：  
  
```  
// C3496.cpp // compile with: /c class C { void f() { [&this] {}(); // C3496 } };  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)