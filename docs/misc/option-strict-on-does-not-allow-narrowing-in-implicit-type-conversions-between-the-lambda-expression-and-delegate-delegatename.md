---
title: "Option Strict On 不允許在 Lambda 運算式和委派 &#39;&lt;委派名稱&gt;&#39; 之間縮小隱含類型轉換。 | Microsoft Docs"
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
  - "bc36662"
  - "vbc36662"
helpviewer_keywords: 
  - "BC36662"
ms.assetid: 4504497b-56ba-4631-ad7b-59975f7fee04
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 不允許在 Lambda 運算式和委派 &#39;&lt;委派名稱&gt;&#39; 之間縮小隱含類型轉換。
當 `Option Strict` 為 On 時，您不能在委派中的參數與指派給該委派類型之變數的 Lambda 運算式的對應參數之間，進行資料類型的縮小轉換。 例如，在下列程式碼中，委派 `Del` 具有一個類型為 `Integer` 的參數。  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String  
```  
  
 因此，指派給類型 `Del` 之變數的任何 Lambda 運算式的對應參數可以是 `Integer` 或可從 `Integer` 擴展轉換的任何資料類型。  
  
```vb#  
' Valid. Dim example1 As Del = Function(n As Integer) "Valid" Dim example2 As Del = Function(n As Long) "Valid" ' Not valid. Dim example3 As Del = Function(n As Short) "Not Valid"  
```  
  
 **錯誤 ID︰**BC36662  
  
### 更正這個錯誤  
  
-   變更委派或 Lambda 運算式中之參數的資料類型，以確保存在擴展關聯性。  
  
-   不要指定 Lambda 運算式中的參數資料類型。 類型將從委派中的對應參數進行推斷。  
  
    ```vb#  
    Dim example4 As Del = Function(n) "Valid"  
    ```  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [Delegates](../Topic/Delegates%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)