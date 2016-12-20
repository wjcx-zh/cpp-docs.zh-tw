---
title: "編譯器警告 (層級 4) CS0028 | Microsoft Docs"
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
  - "CS0028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0028"
ms.assetid: 47df919f-01fa-45ae-a4b7-912445e679e2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 4) CS0028
'function declaration' 的進入點簽章錯誤  
  
 `Main` 的方法宣告無效：它是使用無效的簽章進行宣告。`Main` 必須宣告為靜態，而且必須傳回 [int](../Topic/int%20\(C%23%20Reference\).md) 或 [void](../Topic/void%20\(C%23%20Reference\).md)。 如需詳細資訊，請參閱[Main\(\) 和命令列引數](../Topic/Main\(\)%20and%20Command-Line%20Arguments%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0028：  
  
```  
// CS0028.cs // compile with: /W:4 /warnaserror public class a { public static double Main(int i)   // CS0028 // Try the following line instead: // public static void Main() { } }  
```