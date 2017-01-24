---
title: "編譯器錯誤 CS0017 | Microsoft Docs"
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
  - "CS0017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0017"
ms.assetid: 5e2a3eb3-6f6e-485d-8293-ceabea4d6905
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0017
程式 'output file name' 有一個以上的已定義進入點。 請以 \/main 編譯以指定包含進入點的類型。  
  
 程式只能有一個 [Main](../Topic/Main\(\)%20and%20Command-Line%20Arguments%20\(C%23%20Programming%20Guide\).md) 方法。  
  
 若要解決這個錯誤，您可以刪除程式碼中的所有 Main 方法，只保留一個，或使用 [\/main](../Topic/-main%20\(C%23%20Compiler%20Options\).md) 編譯器選項，指定要使用的 Main 方法。  
  
 下列範例會產生 CS0017：  
  
```  
// CS0017.cs // compile with: /target:exe public class clx { static public void Main() { } } public class cly { public static void Main()   // CS0017, delete one Main or use /main { } }  
```