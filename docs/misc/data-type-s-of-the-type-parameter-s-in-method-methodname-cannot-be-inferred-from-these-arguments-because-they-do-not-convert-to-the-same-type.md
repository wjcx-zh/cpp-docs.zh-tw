---
title: "無法從這些引數推斷方法 &#39;&lt;方法名稱&gt;&#39; 中類型參數的資料類型，因為它們無法轉換成相同的類型 | Microsoft Docs"
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
  - "vbc36660"
  - "bc36660"
  - "vbc36657"
  - "bc36657"
helpviewer_keywords: 
  - "BC36660"
  - "BC36657"
ms.assetid: e80c5afd-e16d-4f03-bdf1-c79c4286114b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從這些引數推斷方法 &#39;&lt;方法名稱&gt;&#39; 中類型參數的資料類型，因為它們無法轉換成相同的類型
無法從這些引數推斷方法 '\<方法名稱\>' 中類型參數的資料類型，因為它們無法轉換成相同的類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 嘗試使用類型推斷，來判斷評估泛型程序呼叫時之類型參數的資料類型。 編譯器找不到符合所有引數之條件約束的資料類型。 因此，它已回報這個錯誤。  
  
> [!NOTE]
>  當無法指定引數時 \(例如，針對查詢運算式中的查詢運算子\)，會顯示不含第二句的錯誤訊息。  
  
 下列程式碼示範這個錯誤。  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. Integer and Date do not convert to the same type. 'targetMethod(19, #3/4/2007#) End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **錯誤 ID︰**BC36660 和 BC36657  
  
### 更正這個錯誤  
  
-   您可能可以明確地將一個或多個引數轉換成相容的類型 \(如下列程式碼所示\)：  
  
    ```  
    targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   您可能可以指定引數要轉換成的類型參數或參數的資料類型 \(如下列程式碼所示\)：  
  
    ```  
    targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## 請參閱  
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)