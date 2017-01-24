---
title: "編譯器錯誤 CS0811 | Microsoft Docs"
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
  - "CS0811"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0811"
ms.assetid: 99f81ad3-684f-47aa-adb8-360e24901454
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0811
偵錯資訊的 'name' 完整名稱太長。 不使用 '\/debug' 選項進行編譯。  
  
 偵錯資訊中的變數和類型名稱有大小限制。  
  
### 更正這個錯誤  
  
1.  如果無法修改名稱，則唯一的替代方法是不使用 [\/debug](../Topic/-debug%20\(C%23%20Compiler%20Options\).md) 選項進行編譯。  
  
## 範例  
 下列程式碼會產生 CS0811：  
  
```  
// cs0811.cs //Compile with: /debug using System; using System.Collections.Generic; namespace TestNamespace { using Long = List<List<List<List<List<List<List<List<List<List<List<List<List <List<List<List<List<List<List<List<List<List<List<List<List<List<List<List<int>>>>>>>>>>>>>>>>>>>>>>>>>>>>; // CS0811 class Test { static int Main() { return 1; } } }  
```