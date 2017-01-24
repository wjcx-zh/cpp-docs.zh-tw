---
title: "編譯器錯誤 CS0267 | Microsoft Docs"
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
  - "CS0267"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0267"
ms.assetid: 11aaab96-5838-4e36-9551-5b032a1089e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0267
partial 修飾詞只可緊接在 'class'、'struct' 或 'interface' 之前  
  
 在類別、結構或介面的宣告中，**partial** 修飾詞的位置不正確。 若要修正錯誤，請重新排序修飾詞。 如需詳細資訊，請參閱[部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0267：  
  
```  
// CS0267.cs public partial class MyClass { public MyClass() { } } partial public class MyClass  // CS0267 // Try this line instead: // public partial class MyClass { public void Foo() { } public static void Main() { } }  
```