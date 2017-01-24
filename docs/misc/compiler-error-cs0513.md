---
title: "編譯器錯誤 CS0513 | Microsoft Docs"
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
  - "CS0513"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0513"
ms.assetid: 6f8569df-713d-4c9c-a675-6576dad139ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0513
'function' 為抽象方法，但包含於非抽象類別 'class' 之中  
  
 方法不能是非抽象類別的[抽象](../Topic/abstract%20\(C%23%20Reference\).md)成員。  
  
 下列範例會產生 CS0513：  
  
```  
// CS0513.cs namespace x { public class clx { abstract public void f();   // CS0513, abstract member of nonabstract class } }  
```