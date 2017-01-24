---
title: "編譯器錯誤 CS0623 | Microsoft Docs"
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
  - "CS0623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0623"
ms.assetid: c9fd6888-b9c5-48bf-b25b-2fae1446ad24
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0623
陣列初始設定式只可用於變數或欄位初始設定式中。 請嘗試改用新的運算式。  
  
 嘗試在內容中使用陣列初始設定式來初始化陣列，這是不允許的作業。  
  
## 範例  
 下列範例會產生 CS0623，因為編譯器會將 \\{4\\} 解譯為外部陣列初始設定式內的內嵌陣列初始設定式：  
  
```  
//cs0632.cs using System; class X { public int[] x = { 2, 3, {4}}; //CS0623 }  
```  
  
## 請參閱  
 [陣列](../Topic/Arrays%20\(C%23%20Programming%20Guide\).md)