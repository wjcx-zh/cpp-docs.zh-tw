---
title: "編譯器錯誤 CS1730 | Microsoft Docs"
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
  - "CS1730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1730"
ms.assetid: 20900ca0-702f-4f35-9a60-2dee9cb11902
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1730
組件和模組屬性必須位於檔案中所有定義的其他項目之前 \(using 子句與外部別名宣告除外\)。  
  
 套用在組件層級的屬性不能出現在任何類型宣告之後。  
  
### 更正這個錯誤  
  
1.  將屬性移至檔案頂端，但位於 `using` 指示詞和 `extern` 別名宣告之下。  
  
## 範例  
 下列程式碼會產生 CS1730：  
  
```  
// cs1730.cs class Test { } [assembly: System.Attribute] // CS1730  
```  
  
## 請參閱  
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)