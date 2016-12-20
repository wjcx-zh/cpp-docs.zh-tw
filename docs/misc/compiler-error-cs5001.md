---
title: "編譯器錯誤 CS5001 | Microsoft Docs"
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
  - "CS5001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS5001"
ms.assetid: e1e26e75-84e0-47c7-be8a-3c4fd0d6f497
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS5001
程式 'program' 未包含適合進入點的靜態 'Main' 方法  
  
 如果在產生可執行檔的程式碼中找不到具有正確簽章的靜態 [Main](../Topic/Main\(\)%20and%20Command-Line%20Arguments%20\(C%23%20Programming%20Guide\).md) 方法，則會發生這個錯誤。 如果所定義進入點函式 `Main` 的大小寫 \(例如小寫 `main`\) 錯誤，也會發生這個錯誤。  
  
-   `Main` 必須宣告為靜態且必須傳回 [void](../Topic/void%20\(C%23%20Reference\).md) 或 [int](../Topic/int%20\(C%23%20Reference\).md)，而且不得有參數，或必須有類型 `string[]` 的一個參數。  
  
## 範例  
 下列範例會產生 CS5001：  
  
```  
// CS5001.cs // CS5001 expected public class a { // Uncomment the following line to resolve. // static void Main() {} }  
```  
  
## 請參閱  
 [Main\(\) 和命令列引數](../Topic/Main\(\)%20and%20Command-Line%20Arguments%20\(C%23%20Programming%20Guide\).md)