---
title: "編譯器錯誤 CS0144 | Microsoft Docs"
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
  - "CS0144"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0144"
ms.assetid: 3904cab1-05bd-44ec-81d0-e36c5656f742
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0144
無法建立抽象類別或介面 'interface' 的執行個體  
  
 您無法建立[抽象](../Topic/abstract%20\(C%23%20Reference\).md)類別或[介面](../Topic/interface%20\(C%23%20Reference\).md)的執行個體。 如需詳細資訊，請參閱[介面](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0144：  
  
```  
// CS0144.cs interface MyInterface { } public class MyClass { public static void Main() { MyInterface myInterface = new MyInterface ();   // CS0144 } }  
```