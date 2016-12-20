---
title: "Option Strict On 要求，如果無法推斷每個 Lambda 運算式參數的類型，就必須使用 &#39;As&#39; 子句來宣告這些參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36642"
  - "vbc36642"
helpviewer_keywords: 
  - "BC36642"
ms.assetid: 2aaa62b8-49c9-4ae8-b0f5-08e3f0b5ad10
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 要求，如果無法推斷每個 Lambda 運算式參數的類型，就必須使用 &#39;As&#39; 子句來宣告這些參數
您已經在 Lambda 運算式中宣告參數，未使用 `As` 子句，`Option Strict` 為 On。  
  
```  
' Not valid when Option Strict is on. ' Dim increment1 = Function (n) n + 1  
```  
  
 如果可以推斷 `n` 的類型，上一個宣告即有效。 例如，如果您將前一個 Lambda 運算式指派給函式委派 `Del`：  
  
```  
Delegate Function Del(ByVal p As Integer) As Integer  
```  
  
 現在就可以從參數 `p` 推斷 `n` 的類型：  
  
```  
Dim increment2 as Del = Function(n) n + 1  
```  
  
 **錯誤 ID：**BC36642  
  
### 更正這個錯誤  
  
-   將 `As` 子句加入參數宣告中：  
  
    ```  
    Dim increment3 = Function (n As Integer) n + 1  
    ```  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)