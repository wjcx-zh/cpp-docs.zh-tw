---
title: "編譯器錯誤 CS0522 | Microsoft Docs"
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
  - "CS0522"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0522"
ms.assetid: f749f21e-92ee-495c-9b53-179ce9342d05
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0522
'constructor' : 結構無法呼叫基底類別建構函式  
  
 [struct](../Topic/struct%20\(C%23%20Reference\).md) 無法呼叫基底類別建構函式；請移除基底類別建構函式的呼叫。  
  
 下列範例會產生 CS0522：  
  
```  
// CS0522.cs public class clx { public clx(int i) { } public static void Main() { } } public struct cly { public cly(int i):base(0)   // CS0522 // try the following line instead // public cly(int i) { } }  
```