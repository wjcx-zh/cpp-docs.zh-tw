---
title: "編譯器錯誤 CS0828 | Microsoft Docs"
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
  - "CS0828"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0828"
ms.assetid: e18ffe72-2fcc-436d-be7f-8c8365b86129
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0828
無法將 'expression' 指派給匿名類型屬性。  
  
 無法使用 Null 值或不安全的類型或是方法群組或匿名函式來初始化匿名類型。  
  
### 更正這個錯誤  
  
1.  在指派左邊加入類型宣告，或變更右邊的運算式，使其具有可接受的類型。  
  
## 範例  
 下列程式碼會產生 CS0828，因為無法使用 Null 值初始化匿名類型的成員。  
  
```  
// cs0828.cs using System; public class C { public static int Main() { var a = 1; var c = new { p1 = null }; // CS0828 return 1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)