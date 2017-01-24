---
title: "編譯器錯誤 CS0127 | Microsoft Docs"
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
  - "CS0127"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0127"
ms.assetid: b20333bf-badf-4f96-a3ee-bd35f4f7e807
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0127
因為 'function' 傳回 void，return 關鍵字後面不可接物件運算式  
  
 傳回類型為 [void](../Topic/void%20\(C%23%20Reference\).md) 的方法無法傳回值。 如需詳細資訊，請參閱[方法](../Topic/Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0127：  
  
```  
// CS0127.cs namespace MyNamespace { public class MyClass { public int hiddenMember2 { get { return 0; } set   // CS0127, set has an implicit void return type { return 0;   // remove return statement to resolve this CS0127 } } public static void Main() { } } }  
```