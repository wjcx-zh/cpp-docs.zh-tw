---
title: "編譯器警告 (層級 2) CS0114 | Microsoft Docs"
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
  - "CS0114"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0114"
ms.assetid: 9647772b-d581-4620-981e-f9c607d4a1af
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0114
'function1' 會隱藏繼承的成員 'function2'。 若要讓目前的方法覆寫該實作，請加入 override 關鍵字。 否則，請加入 new 關鍵字。  
  
 類別中的宣告與基底類別中的宣告衝突，因此，將會隱藏基底類別成員。  
  
 如需詳細資訊，請參閱 [base](../Topic/base%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0114：  
  
```  
// CS0114.cs // compile with: /W:2 /warnaserror abstract public class clx { public abstract void f(); } public class cly : clx { public void f() // CS0114, hides base class member // try the following line instead // override public void f() { } public static void Main() { } }  
```