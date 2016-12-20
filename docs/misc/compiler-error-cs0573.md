---
title: "編譯器錯誤 CS0573 | Microsoft Docs"
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
  - "CS0573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0573"
ms.assetid: 10ef9625-44f1-4936-ada3-56938357aa01
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0573
'field declaration': 在結構中不能有執行個體欄位初始設定式  
  
 您無法初始化[結構](../Topic/struct%20\(C%23%20Reference\).md)的執行個體欄位。 實值類型的欄位將初始化為其預設值，而參考類型欄位將初始化為 `null`。  
  
## 範例  
 下列範例會產生 CS0573：  
  
```  
// CS0573.cs namespace x { public class clx { public static void Main() { } } public struct cly { clx a = new clx();   // CS0573 // clx a;            // OK int i = 7;           // CS0573 // int i;            // OK } }  
```