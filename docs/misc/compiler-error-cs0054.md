---
title: "編譯器錯誤 CS0054 | Microsoft Docs"
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
  - "CS0054"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0054"
ms.assetid: 49346f55-d887-497a-af71-be4cbbf1de24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0054
不一致的存取範圍: 索引子傳回類型 'type' 比索引子 'indexer' 的存取範圍小  
  
 公用建構必須傳回可公開存取的物件。 如需詳細資訊，請參閱[存取修飾詞](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0054：  
  
```  
// CS0054.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass3 { public MyClass this[int i]   // CS0054 { get { return new MyClass(); } } } public class MyClass2 { public static void Main() { } }  
```