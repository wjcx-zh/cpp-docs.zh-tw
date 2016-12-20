---
title: "編譯器錯誤 CS0822 | Microsoft Docs"
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
  - "CS0822"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0822"
ms.assetid: 519091be-2332-4df4-acd9-e3b633966b3d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0822
隱含類型區域變數不可以是常數  
  
 隱含類型區域變數只有在儲存匿名類型時才需要。 在所有其他情況下，都只是為了方便起見。 如果變數的值永遠不會變更，只需要提供它明確的類型。 嘗試對隱含類型區域變數使用 `readonly` 修飾詞會產生 CS0106。  
  
### 更正這個錯誤  
  
1.  如果您需要變數是常數或 `readonly`，請提供它明確的類型。  
  
## 範例  
 下列程式碼會產生 CS0822：  
  
```  
// cs0822.cs class A { public static int Main() { const var x = 0; // CS0822.cs return -1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)