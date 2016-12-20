---
title: "編譯器錯誤 CS0177 | Microsoft Docs"
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
  - "CS0177"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0177"
ms.assetid: 852a8c2a-2411-4800-af7c-4c572d9900d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0177
在程式控制權脫離目前的方法之前，必須指派 out 參數 'parameter'  
  
 未在方法主體中指派值給以 [out](../Topic/out%20\(C%23%20Reference\).md) 關鍵字標記的參數。 如需詳細資訊，請參閱[傳遞參數](../Topic/Passing%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0177：  
  
```  
// CS0177.cs public class MyClass { public static void Foo(out int i)   // CS0177 { // uncomment the following line to resolve this error //   i = 0; } public static void Main() { int x = -1; Foo(out x); } }  
```