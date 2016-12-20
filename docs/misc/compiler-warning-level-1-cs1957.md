---
title: "編譯器警告 (層級 1) CS1957 | Microsoft Docs"
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
  - "CS1957"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1957"
ms.assetid: a4823211-52ce-4ffa-b19b-ee874069409f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1957
成員 'name' 覆寫 'method'。 在執行階段，有多個覆寫候選項。 取決於所呼叫方法的實作。  
  
 方法參數的差異僅在於它們是否為 `ref`或者在執行階段無法區別 `out`。  
  
### 避免這個警告  
  
1.  將不同的名稱或不同數目的參數提供給其中一種方法。  
  
## 範例  
 下列程式碼會產生 CS1957：  
  
```  
// cs1957.cs class Base<T, S> { public virtual string Test(out T x) // CS1957 { x = default(T); return "Base.Test"; } public virtual void Test(ref S x) { } } class Derived : Base<int, int> { public override string Test(out int x) { x = 0; return "Derived.Test"; } static int Main() { int x; if (new Derived().Test(out x) == "Derived.Test") return 0; return 1; } }  
```