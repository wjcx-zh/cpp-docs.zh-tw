---
title: "編譯器錯誤 CS0241 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0241"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "預設方法參數值"
  - "預設值, 參數值"
  - "預設值, 方法參數值"
  - "預設參數值"
  - "CS0241"
ms.assetid: be31b194-3de5-4aab-b23a-6cf790f940ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0241
不允許預設參數規範  
  
 [方法參數](../Topic/Method%20Parameters%20\(C%23%20Reference\).md)不可以有預設值。 如果您想要達到相同的效果，請使用方法多載。 如需詳細資訊，請參閱[傳遞參數](../Topic/Passing%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0241。 此外，這個範例還會示範如何使用多載來模擬具有預設引數的方法。  
  
```  
// CS0241.cs public class A { public void Test(int i = 9) {}   // CS0241 } public class B { public void Test() { Test(9); } public void Test(int i)  {} } public class C { public static void Main() { B x = new B(); x.Test(); } }  
```