---
title: "編譯器錯誤 CS0059 | Microsoft Docs"
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
  - "CS0059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0059"
ms.assetid: 25a8624b-7f7b-4487-ba80-413d57f9132b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0059
不一致的存取範圍：參數類型 'type' 比委派 'delegate' 的存取範圍小  
  
 傳回類型以及方法之型式參數清單中所參考的每個類型都必須至少可以像方法本身一樣地進行存取。 如需詳細資訊，請參閱[存取修飾詞](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0059：  
  
```  
// CS0059.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public delegate void MyClassDel( MyClass myClass);   // CS0059 public class Program { public static void Main() { } }  
```