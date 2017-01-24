---
title: "編譯器錯誤 CS0037 | Microsoft Docs"
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
  - "CS0037"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0037"
ms.assetid: 1d34a71e-10a0-4fa8-9b94-343e69428c61
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0037
無法將 null 轉換成 'type'，因為它是不可為 Null 的實值類型  
  
 編譯器無法將 null 指派給實值類型；您只能將 null 指派給[參考類型](../Topic/Reference%20Types%20\(C%23%20Reference\).md)或可為 Null 的類型。[結構](../Topic/struct%20\(C%23%20Reference\).md)類型是實值類型。 如需詳細資訊，請參閱[可為 Null 的類型](../Topic/Nullable%20Types%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0037：  
  
```  
// CS0037.cs public struct s { } class a { public static void Main() { int i = null;   // CS0037 s ss = null;    // CS0037 } }  
```