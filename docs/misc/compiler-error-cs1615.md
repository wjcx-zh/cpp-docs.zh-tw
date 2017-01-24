---
title: "編譯器錯誤 CS1615 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1615"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1615"
ms.assetid: 518bb07f-0e3a-4761-9931-66845eb5df1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1615
傳遞引數 'number' 時不應該包含 'keyword' 關鍵字  
  
 使用了 `ref` 或 **out** 的其中一個關鍵字，但函式未接受該引數的 `ref` 或 **out** 參數。 若要解決此錯誤，請移除不正確的關鍵字，並使用符合函式宣告的適當關鍵字，如果有的話。  
  
 下列範例會產生 C1615：  
  
```  
// CS1615.cs class C { public void f(int i) {} public static void Main() { int i = 1; f(ref i);  // CS1615 } }  
```