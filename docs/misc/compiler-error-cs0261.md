---
title: "編譯器錯誤 CS0261 | Microsoft Docs"
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
  - "CS0261"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0261"
ms.assetid: c2af7b31-4a48-457a-8d9b-0956dd0d46f9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0261
'type' 的部分宣告必須全部為類別、全部為結構，或全部為介面  
  
 如果部分類型在不同位置宣告為不同類型的建構，就會發生這個錯誤。 如需詳細資訊，請參閱[部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0261：  
  
```  
// CS0261.cs partial class A  // CS0261 – A declared as a class here, but as a struct below { } partial struct A { }  
```