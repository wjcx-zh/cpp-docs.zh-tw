---
title: "&#39;&lt;變數名稱&gt;&#39; 的類型模稜兩可，因為迴圈繫結和 step 變數不會擴展為相同類型 | Microsoft Docs"
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
  - "vbc30983"
  - "bc30983"
helpviewer_keywords: 
  - "BC30983"
ms.assetid: 6b97153c-dee3-4429-b92a-2e5a212c864b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;變數名稱&gt;&#39; 的類型模稜兩可，因為迴圈繫結和 step 變數不會擴展為相同類型
您的程式碼包含 `For...Next` 迴圈，其中，編譯器無法推斷迴圈控制變數的資料類型，因為下列條件為 true：  
  
-   未使用 `As` 子句指定迴圈控制變數的資料類型。  
  
-   迴圈繫結和 step 變數包含至少兩種資料類型。  
  
-   資料類型之間可能存在多種可能轉換。  
  
-   候選項目之間沒有最佳類型，如此，迴圈控制變數的類型選擇模稜兩可。  
  
 例如，下列迴圈具有一個類型為 `Integer` 的迴圈繫結以及一個類型為 `UInteger` 的迴圈繫結：  
  
```vb#  
Dim m As Integer = 1 Dim n As UInteger = 10 ' Not valid. ' For i = m To n ' Loop processing. ' Next  
```  
  
 `Integer` 與 `UInteger` 之間存在可能轉換，而 `UInteger` 與 `Integer` 之間存在可能轉換，但兩者都是縮小轉換，因此都不是最佳選擇。  
  
 在下一個範例中，加入類型為 `Double` 的第三個變數。`Integer` 和 `UInteger` 都具有 `Double` 的標準擴展轉換，這會將 `Double` 的轉換設為最佳選擇。 類型推斷會將資料類型 `Double` 指派給迴圈控制變數 `i`。  
  
```vb#  
Dim stepVar As Double = 1 ' Valid. For i = m To n Step stepVar ' Loop processing. Next  
```  
  
 **錯誤 ID︰**BC30983  
  
### 更正這個錯誤  
  
-   將其中一個變數明確地轉換成其他變數具有擴展轉換的類型，例如：  
  
    ```  
    For i = m To CLng(n)  
    ```  
  
-   使用 `As` 子句來指定控制變數的類型：  
  
    ```  
    For i As Double = m To n   
    ```  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Local Type Inference](../Topic/Local%20Type%20Inference%20\(Visual%20Basic\).md)   
 [Option Infer Statement](../Topic/Option%20Infer%20Statement.md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)