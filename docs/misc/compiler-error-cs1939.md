---
title: "編譯器錯誤 CS1939 | Microsoft Docs"
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
  - "CS1939"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1939"
ms.assetid: 9a7cdd48-3d45-473a-a799-c7771ef8158d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1939
無法將範圍變數 'name' 當做 out 或 ref 參數傳遞。  
  
 範圍變數是一種唯讀的變數，其會在查詢運算式中引入，並作為來源序列中每個後續項目的識別項。 因為它無法以任何方式修改，因此不需要以 `ref` 或 `out` 傳遞。 因此，這兩項作業無效。  
  
### 更正這個錯誤  
  
1.  以傳值方式傳遞範圍變數。  
  
## 範例  
 下列範例會產生 CS1939：  
  
```  
// cs1939.cs using System.Linq; class Test { public static void F(ref int i) { } public static void Main() { var list = new int[] { 0, 1, 2, 3, 4, 5 }; var q = from x in list let k = x select Test.F(ref x); // CS1939 } }  
```