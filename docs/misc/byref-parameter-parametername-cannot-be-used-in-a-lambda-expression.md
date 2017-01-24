---
title: "&#39;ByRef&#39; 參數 &#39;&lt;參數名稱&gt;&#39; 不能用在 Lambda 運算式中 | Microsoft Docs"
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
  - "bc36639"
  - "vbc36639"
helpviewer_keywords: 
  - "BC36639"
ms.assetid: 5913f9b6-2929-4c05-8dd1-00b10fcd5a83
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ByRef&#39; 參數 &#39;&lt;參數名稱&gt;&#39; 不能用在 Lambda 運算式中
在 `Sub` 或函式內宣告的 Lambda 運算式不能使用 `Sub` 或函式的任何 `ByRef` 參數。 例如，下列程式碼會導致這個錯誤，因為 Lambda 運算式中使用了 `ByRef` 參數 `n`。  
  
```  
'' Not valid.   
'Sub ExampleSub(ByRef n As Integer)  
  
'    Dim lambda = Function(p As Integer) p + n  
  
'End Sub  
```  
  
 **錯誤識別碼：**BC36639  
  
### 更正這個錯誤  
  
-   將 `ByRef` 參數指派給區域變數，然後在 Lambda 運算式中使用此區域變數，如下列程式碼所示：  
  
    ```  
    Sub ExampleSub(ByRef n As Integer)  
  
        Dim temp = n  
        Dim lambda = Function(p As Integer) p + temp  
  
    End Sub  
    ```  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)