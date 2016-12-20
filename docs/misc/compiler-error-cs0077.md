---
title: "編譯器錯誤 CS0077 | Microsoft Docs"
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
  - "CS0077"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0077"
ms.assetid: 55d3d290-d172-41a3-b326-ebf5a0a7e81f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0077
as 運算子必須和參考類型或可為 Null 的類型一起使用 \('int' 是不可為 Null 的實值類型\)。  
  
 傳遞了[實值類型](../Topic/Value%20Types%20\(C%23%20Reference\).md)給 [as](../Topic/as%20\(C%23%20Reference\).md) 運算子。 因為 `as` 可以傳回 [null](../Topic/null%20\(C%23%20Reference\).md)，所以只能傳遞[參考類型](../Topic/Reference%20Types%20\(C%23%20Reference\).md)或可為 Null 的類型給它。 如需可為 Null 類型的詳細資訊，請參閱[可為 Null 的類型](../Topic/Nullable%20Types%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0077：  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```