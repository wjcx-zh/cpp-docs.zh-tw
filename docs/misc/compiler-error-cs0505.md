---
title: "編譯器錯誤 CS0505 | Microsoft Docs"
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
  - "CS0505"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0505"
ms.assetid: e3cb9e33-7338-4869-859b-81d7439f0d23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0505
'member1': 因為 'member2' 不是函式，所以無法覆寫  
  
 類別宣告嘗試在基底類別中覆寫非方法。 覆寫必須符合成員類型。 如果想要與基底類別中的方法同名的方法，請在基底類別的方法宣告使用 [new](../Topic/new%20\(C%23%20Reference\).md) \(而非 [override](../Topic/override%20\(C%23%20Reference\).md)\)。  
  
 下列範例會產生 CS0505：  
  
```  
// CS0505.cs // compile with: /target:library public class clx { public int i; } public class cly : clx { public override int i() { return 0; }   // CS0505 }  
```