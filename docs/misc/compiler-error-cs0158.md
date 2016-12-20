---
title: "編譯器錯誤 CS0158 | Microsoft Docs"
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
  - "CS0158"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0158"
ms.assetid: 88ac61a9-ce55-4272-9141-0873765a7034
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0158
標籤 'label' 在所包含的範圍內以相同的名稱遮蔽其他標籤  
  
 內部範圍中的標籤會隱藏外部範圍中同名的標籤。 如需詳細資訊，請參閱[goto](../Topic/goto%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0158：  
  
```  
// CS0158.cs namespace MyNamespace { public class MyClass { public static void Main() { goto lab1; lab1: { lab1: goto lab1;   // CS0158 } } } }  
```