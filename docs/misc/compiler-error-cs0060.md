---
title: "編譯器錯誤 CS0060 | Microsoft Docs"
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
  - "CS0060"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0060"
ms.assetid: ae6d4fb7-5ff9-4883-82c3-f55b190f439a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0060
存取範圍不一致：基底類別 'class1' 的存取範圍小於類別 'class2'  
  
 基底類別和繼承類別之間的類別存取範圍應該一致。  
  
 下列範例會產生 CS0060：  
  
```  
// CS0060.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass2 : MyClass   // CS0060 { public static void Main() { } }  
```  
  
## 請參閱  
 [存取修飾詞](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)