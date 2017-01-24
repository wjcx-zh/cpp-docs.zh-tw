---
title: "編譯器警告 (層級 2) CS0279 | Microsoft Docs"
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
  - "CS0279"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0279"
ms.assetid: 5e5faa8f-3d5b-4999-aa62-ff7f131a3e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0279
'類型名稱' 未實作 '模式名稱' 模式， 因為 '方法名稱' 為靜態或並非公用。  
  
 C\# 中有幾個依賴已定義模式的陳述式，例如 `foreach` 和 `using`。 例如，`foreach` 依賴實作可列舉模式的集合類別。 當編譯器由於方法已宣告為 `static` 或不是 `public` 而無法進行比對時，就會發生這個錯誤 模式中的方法必須是類別的執行個體，而且必須是公用。  
  
## 範例  
 下列範例會產生 CS0279：  
  
```  
// CS0279.cs using System; using System.Collections; public class myTest : IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } public static void Main() { foreach (int i in new myTest()) {}  // CS0279 } }  
```