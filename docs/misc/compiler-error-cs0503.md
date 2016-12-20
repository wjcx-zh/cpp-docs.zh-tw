---
title: "編譯器錯誤 CS0503 | Microsoft Docs"
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
  - "CS0503"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0503"
ms.assetid: 12a337c9-8c5d-473d-8ce6-057b2c7e7935
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0503
無法將 abstract 方法 'method' 標記成 virtual  
  
 不需要將成員方法標記為 [abstract](../Topic/abstract%20\(C%23%20Reference\).md) 和 [virtual](../Topic/virtual%20\(C%23%20Reference\).md)，因為 **abstract** 即表示 **virtual**。  
  
 下列範例會產生 CS0503：  
  
```  
// CS0503.cs namespace x { abstract public class clx { abstract virtual public void f();   // CS0503 } }  
```