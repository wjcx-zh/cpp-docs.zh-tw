---
title: "編譯器錯誤 CS0820 | Microsoft Docs"
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
  - "CS0820"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0820"
ms.assetid: 38c05162-ef20-42a8-9611-02698360dec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0820
無法指派陣列初始設定式給隱含類型區域變數  
  
 隱含類型的陣列就是透過編譯器推斷其項目類型的陣列。 它必須使用 `new`\[\] 修飾詞進行初始化 \(如範例程式碼所示\)。  
  
### 更正這個錯誤  
  
-   請搭配使用 `new`\[\] 修飾詞與陣列初始設定式。  
  
-   請不要使用隱含類型區域變數。  
  
## 範例  
 下列程式碼會產生 CS0820，並示範如何正確地初始化隱含類型陣列：  
  
```  
//cs0820.cs class G { public static int Main() { var a = { 1,2,3}; //CS0820 // Try using one of the following lines instead. // var b = new[] { 1, 2, 3 }; //int[] b = {1, 2, 3}; return -1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)