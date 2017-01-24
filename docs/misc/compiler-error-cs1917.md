---
title: "編譯器錯誤 CS1917 | Microsoft Docs"
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
  - "CS1917"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1917"
ms.assetid: 05688706-e4b4-4273-9244-48cce1f7f9b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1917
類型為 'struct name' 的唯讀欄位 'name' 之成員，無法使用物件初始設定式進行指派，因為它是實值類型。  
  
 為實值類型的唯讀欄位只能指派於建構函式中。  
  
### 更正這個錯誤  
  
-   請將結構變更為類別類型。  
  
-   使用建構函式來初始化結構。  
  
## 範例  
 下列程式碼會產生 CS1917：  
  
```  
// cs1917.cs class CS1917 { public struct TestStruct { public int i; } public class C { public readonly TestStruct str = new TestStruct(); public static int Main() { C c = new C { str = { i = 1 } }; // CS1917 return 0; } } }  
```