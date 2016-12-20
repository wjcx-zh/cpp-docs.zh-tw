---
title: "無法推斷二元 &#39;If&#39; 運算子的第一個和第二個運算元之一般類型 | Microsoft Docs"
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
  - "vbc33110"
  - "bc33110"
helpviewer_keywords: 
  - "BC33110"
ms.assetid: f46873aa-f6cd-4cc9-9e8e-e668bddf0980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法推斷二元 &#39;If&#39; 運算子的第一個和第二個運算元之一般類型
無法推斷二元 'If' 運算子的第一個和第二個運算元之一般類型。 一個運算元必須要能夠擴展轉換成另一個運算元。  
  
 二元 `If` 運算子要求其中一個引數與另一個引數之間必須進行擴展轉換。 例如，由於 `Integer` 與 `String` 之間沒有任一方向的擴展轉換，因此下列程式碼會造成這個錯誤。  
  
```vb#  
Dim first? As Integer  
Dim second As String = "First is Nothing"  
'' Not valid.  
' Console.WriteLine(If(first, second))  
```  
  
 **錯誤 ID︰**BC33110  
  
### 更正這個錯誤  
  
-   如果可能的話，請在您的程式碼中提供其中一個運算元的明確轉換：  
  
    ```  
    Console.WriteLine(If(first, CInt(second)))   
    ```  
  
-   使用不同的條件式建構重寫程式碼。  
  
    ```  
    If first IsNot Nothing Then  
        Console.WriteLine(first)  
    Else  
        Console.WriteLine(second)  
    End If  
    ```  
  
## 請參閱  
 [If Operator](../Topic/If%20Operator%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [If...Then...Else Statement](../Topic/If...Then...Else%20Statement%20\(Visual%20Basic\).md)