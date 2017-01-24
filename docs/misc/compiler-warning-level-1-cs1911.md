---
title: "編譯器警告 (層級 1) CS1911 | Microsoft Docs"
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
  - "CS1911"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1911"
ms.assetid: 95e8a7a0-1c19-4930-a7e9-3ae4060e97d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1911
透過匿名方法、Lambda 運算式、查詢運算式或迭代器的 'base' 關鍵字存取成員 'name'，會導致無法驗證的程式碼。 考慮將存取移入所包含類型的 Helper 方法。  
  
 以迭代器或匿名方法之方法主體內的 `base` 關鍵字呼叫虛擬函式，會導致無法驗證的程式碼。 無法驗證的程式碼無法在部分信任的環境中執行。  
  
 CS1911 的解決方法之一，是將虛擬函式呼叫移至 Helper 函式。  
  
## 範例  
 下列範例會產生 CS1911。  
  
```  
// CS1911.cs // compile with: /W:1 using System; delegate void D(); delegate D RetD(); class B { protected virtual void M() { Console.WriteLine("B.M"); } } class Der : B { protected override void M() { Console.WriteLine("D.M"); } void Test() { base.M(); } D Test2() { return new D(base.M); } public D CallBaseM() { return delegate () { base.M(); };   // CS1911 // try the following line instead // return delegate () { Test(); }; } public RetD DelToBaseM() { return delegate () { return new D(base.M); };   // CS1911 // try the following line instead // return delegate () { return Test2(); }; } } class Program { public static void Main() { Der der = new Der(); D d = der.CallBaseM(); d(); RetD rd = der.DelToBaseM(); rd()(); } }  
```