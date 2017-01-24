---
title: "&#39;ParamArray&#39; 不能套用至擴充方法的第一個參數 | Microsoft Docs"
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
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ParamArray&#39; 不能套用至擴充方法的第一個參數
'ParamArray' 不能套用至擴充方法的第一個參數。 第一個參數會指定要擴充的類型。  
  
 擴充方法的第一個參數會指定方法可擴充的資料類型。 因此，第一個參數是必要項目，不得為選用項目。 因為參數陣列會自動為選用項目，所以它不能作為擴充方法的第一個引數。  
  
> [!NOTE]
>  執行方法時，叫用方法的擴充資料類型執行個體會變成方法之第一個參數的引數。 例如，`greeting.Print()` 中的執行個體 `greeting` 是擴充方法 `Public Sub Print (ByVal str As String)` 中第一個參數的引數 \(`str`\)。  
  
 **錯誤 ID︰**BC36554  
  
### 更正這個錯誤  
  
-   如果參數陣列未指定您想要擴充的資料類型，請加入新的第一個參數來指定這個類型。  
  
    ```  
    <Extension()> Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String) ' Concatenate the strings in addOns to str. End Sub  
    ```  
  
-   如果參數陣列指定您想要擴充的資料類型，請考慮將它變更為需要引數的一般陣列，而非參數陣列。 一般陣列可以進行擴充。  
  
    ```  
    <Extension()> Public Function Sum(ByVal ints() As Integer) As Integer Dim total As Integer = 0 For Each i As Integer In ints total = total + i Next i Return total End Function  
    ```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Parameter Arrays](../Topic/Parameter%20Arrays%20\(Visual%20Basic\).md)   
 [Optional Parameters](../Topic/Optional%20Parameters%20\(Visual%20Basic\).md)