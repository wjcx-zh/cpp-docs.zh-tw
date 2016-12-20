---
title: "編譯器錯誤 CS0132 | Microsoft Docs"
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
  - "CS0132"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0132"
ms.assetid: e8ad1281-2912-4b6a-b2af-a319a23ddd16
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0132
'constructor' : 靜態的建構函式不能使用參數  
  
 不能以一個或多個參數宣告[靜態](../Topic/static%20\(C%23%20Reference\).md)建構函式。 如需詳細資訊，請參閱[建構函式](../Topic/Constructors%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0132：  
  
```  
// CS0132.cs namespace MyNamespace { public class MyClass { public MyClass(int i) { } } public class MyClass2 : MyClass { static MyClass2(int i)   // CS0132 { } } }  
```