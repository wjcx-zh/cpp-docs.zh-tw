---
title: "編譯器錯誤 CS1928 | Microsoft Docs"
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
  - "CS1928"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1928"
ms.assetid: bcc9dbef-ded5-4ddd-8c03-a9837cb6d165
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1928
'Type' 不包含 'method' 的定義，而且最佳的擴充方法多載 'method' 有一些無效的引數。  
  
 編譯器找不到具有所呼叫之方法名稱的類別成員時，會產生這個錯誤。 它可以找到具有該名稱的擴充方法，但未包含符合透過方法呼叫傳入之類型的簽章。  
  
### 更正這個錯誤  
  
1.  傳入符合現有擴充方法或類別方法的類型。  
  
## 範例  
 下列程式碼會產生 CS1928：  
  
```  
// cs1928.cs class Test { static void Main() { Test t = new Test(); t.M("hi"); // CS1928 } } static class Ext { public static void M(this Test t, int i) { } }  
```  
  
 這個錯誤通常會伴隨 CS1503：引數 'n'：無法從 'typeA' 轉換為 'typeB'。  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)