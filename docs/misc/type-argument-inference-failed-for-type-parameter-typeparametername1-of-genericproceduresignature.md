---
title: "&#39;&lt;泛型程序簽章&gt;&#39; 之類型參數 &#39;&lt;類型參數名稱1&gt;&#39; 的類型引數推斷失敗 | Microsoft Docs"
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
  - "vbc32116"
  - "bc32116"
helpviewer_keywords: 
  - "BC32116"
ms.assetid: 6bfb02ec-814a-4b1f-a585-6d902a861d00
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;泛型程序簽章&gt;&#39; 之類型參數 &#39;&lt;類型參數名稱1&gt;&#39; 的類型引數推斷失敗
'\<泛型程序簽章\>' 之類型參數 '\<類型參數名稱1\>' 的類型引數推斷失敗。 從傳遞給參數 '\<類型參數名稱1\>' 的引數所推斷的類型引數，與從傳遞給參數 '\<類型參數名稱2\>' 的引數所推斷的類型引數衝突。  
  
 呼叫沒有任何類型引數的泛型程序，而且嘗試的類型推斷已產生類型參數的資料類型衝突。  
  
 通常，當您呼叫泛型程序時，會針對泛型程序所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，則編譯器會嘗試推斷要傳遞給類型參數的類型。 如果呼叫的內容提供類型參數的衝突資料類型資訊，則類型推斷會失敗。  
  
 下列程式碼可能會產生此錯誤。  
  
```  
Public Sub takeTwoValues(Of t)(ByVal x As t, ByVal y As t) End Sub Call takeTwoValues(4, 2.5)  
```  
  
 因為第一個引數可讓編譯器推斷類型參數 `t` 的 `Integer`，而第二個引數可讓它推斷相同類型參數的 `Double`，所以傳遞給 `t` 的資料類型發生衝突。  
  
 **錯誤 ID︰**BC32116  
  
### 更正這個錯誤  
  
-   請將類型引數提供給泛型類型，這樣編譯器就不需要推斷它們。  
  
    ```  
    Call takeTwoValues(Of Double)(4, 2.5)  
    ```  
  
     請注意，在兩個一般引數的資料類型不同的情況下，呼叫端程式碼必須傳遞可容納這兩種資料類型的類型引數。 在此情況下，`Integer` 會擴展至 `Double`。  
  
     \-或\-  
  
-   重新定義泛型程序，以指定一般參數的不同類型參數，讓推斷類型不發生衝突。  
  
    ```  
    Public Sub takeTwoValues(Of t1, t2)(ByVal x As t1, ByVal y As t2)  
    ```  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)