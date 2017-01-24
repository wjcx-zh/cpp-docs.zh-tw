---
title: "編譯器錯誤 CS1948 | Microsoft Docs"
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
  - "CS1948"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1948"
ms.assetid: 3dac3abe-0edd-4ee1-8fb1-bc597ea63e1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1948
範圍變數 'name' 不可與方法類型參數同名  
  
 相同的宣告空間不能包含兩個識別項相同的宣告。  
  
### 更正這個錯誤  
  
1.  請變更範圍變數或類型參數的名稱。  
  
## 範例  
 下列範例會產生 CS1948，因為識別項 `T` 是用於範圍變數以及方法 `TestMethod` 上的類型參數：  
  
```  
// cs1948.cs using System.Linq; class Test { public void TestMethod<T>(T t) { var x = from T in Enumerable.Range(1, 100) // CS1948 select T; } }  
```