---
title: "編譯器錯誤 CS1955 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1955"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1955"
ms.assetid: 38a8542d-da53-4739-b807-46c8c077363c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1955
非可叫用 \(Non\-invocable\) 成員 'name' 不能作為方法使用。  
  
 只能叫用方法和委派。 當您嘗試使用空括弧來呼叫方法或委派以外的項目時，會產生這個錯誤。  
  
### 更正這個錯誤  
  
1.  請從運算式中移除括弧。  
  
## 範例  
 下列程式碼會產生 CS1955，因為程式碼嘗試使用方法呼叫運算子 [\(\)](../Topic/\(\)%20Operator%20\(C%23%20Reference\).md) 來叫用欄位和屬性。 您不能呼叫欄位或屬性，但可以使用成員存取運算子 \([.](../Topic/.%20Operator%20\(C%23%20Reference\).md)\) 來存取它所儲存的值。  
  
```  
// cs1955.cs class A { public int x = 0; public int X { get { return x; } set { x = value; } } } class Test { static int Main() { A a = new A(); a.x(); // CS1955 a.X(); // CS1955 // Try this line instead: // int num = a.x; } }  
```