---
title: "編譯器錯誤 CS0058 | Microsoft Docs"
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
  - "CS0058"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0058"
ms.assetid: 9535da60-03b9-41ab-93e1-e57b6440fca9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0058
不一致的存取範圍：傳回類型 'type' 比委派 'delegate' 的存取範圍小  
  
 公用建構必須傳回可公開存取的物件。 如需詳細資訊，請參閱[存取修飾詞](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0058，因為未將任何存取修飾詞套用至 MyClass，因此預設具有私用存取範圍：  
  
```  
// CS0058.cs class MyClass // try the following line instead // public class MyClass { } public delegate MyClass MyClassDel();   // CS0058 public class A { public static void Main() { } }  
```  
  
## 請參閱  
 [private](../Topic/private%20\(C%23%20Reference\).md)