---
title: "編譯器錯誤 CS1688 | Microsoft Docs"
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
  - "CS1688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1688"
ms.assetid: e15672a1-2570-4e65-99fc-7acc190ae643
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1688
無法將沒有參數清單的匿名方法區塊轉換為委派類型 'delegate'，因為它有一或多個 out 參數  
  
 在大部分情況下，編譯器允許匿名方法區塊省略參數。 如果匿名方法區塊沒有參數清單，但委派具有 `out` 參數，則會引發這個錯誤。 編譯器不允許這種情況，因為它需要忽略 `out` 參數的存在，但這不可能是正確的行為。  
  
## 範例  
 下列程式碼會產生錯誤 CS1688。  
  
```  
// CS1688.cs using System; delegate void OutParam(out int i); class ErrorCS1676 { static void Main() { OutParam o; o = delegate  // CS1688 // Try this instead: // o = delegate(out int i) { Console.WriteLine(""); }; } }  
```