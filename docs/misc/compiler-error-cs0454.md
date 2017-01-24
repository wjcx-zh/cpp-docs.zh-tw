---
title: "編譯器錯誤 CS0454 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0454"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0454"
ms.assetid: 2c83bc5e-53bb-473e-92aa-5122dadd79d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0454
循環條件約束相依性，涉及 '類型參數1' 和 '類型參數2'  
  
 這個錯誤是由於在某個時間點，一個類型參數參考到另一個類型參數，而第二個類型參數又參考回第一個類型參數所引起。 若要修正這個錯誤，請移除其中一個條件約束來中斷循環相依性。 請注意，循環條件約束相依性可能是間接的。  
  
## 範例  
 下列程式碼會產生錯誤 CS0454。  
  
```  
// CS0554 using System; public class GenericsErrors { public class G4<T> where T : T { } // CS0454 }  
```  
  
## 範例  
 下列範例會示範兩個類型條件約束之間的循環相依性。  
  
```  
public class Gen<T,U> where T : U where U : T  // CS0454 { }  
```