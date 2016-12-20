---
title: "編譯器錯誤 CS1113 | Microsoft Docs"
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
  - "CS1113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1113"
ms.assetid: ef2d828f-b5ee-4be9-ba2e-36df5502cc5a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1113
在實值類型 'type' 中定義的擴充方法 'name' 無法用來建立委派。  
  
 針對類別類型定義的擴充方法可以用來建立委派。 針對實值類型定義的擴充方法則否。  
  
### 更正這個錯誤  
  
1.  請讓擴充方法與類別類型產生關聯。  
  
2.  使方法成為結構上的一般方法。  
  
## 範例  
 下列範例會產生 CS1113：  
  
```  
// cs1113.cs using System; public static class Extensions { public static S ExtMethod(this S s) { return s; } } public struct S { } public class Test { static int Main() { Func<S> f = new S().ExtMethod; // CS1113 return 1; } }  
  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)