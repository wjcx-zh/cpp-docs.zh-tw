---
title: "編譯器錯誤 CS0540 | Microsoft Docs"
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
  - "CS0540"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0540"
ms.assetid: 2da2cd4a-0ff1-45ea-bb72-ea078bc95dea
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0540
'介面成員': 包含類型未實作介面 'interface'  
  
 您嘗試在[類別](../Topic/class%20\(C%23%20Reference\).md)中實作非衍生自[介面](../Topic/interface%20\(C%23%20Reference\).md)的介面成員。 您應該刪除介面成員的實作，或將介面加入類別的基底類別清單中。  
  
## 範例  
 下列範例會產生 CS0540。  
  
```  
// CS0540.cs interface I { void m(); } public class Clx { void I.m() {}   // CS0540 } // OK public class Cly : I { void I.m() {} public static void Main() {} }  
```  
  
## 範例  
 下列範例會產生 CS0540。  
  
```  
// CS0540_b.cs using System; class C { void IDisposable.Dispose() {}   // CS0540 } class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```