---
title: "無法推斷 &#39;&lt;泛型程序名稱&gt;&#39; 的類型參數 &#39;&lt;類型參數名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法推斷 &#39;&lt;泛型程序名稱&gt;&#39; 的類型參數 &#39;&lt;類型參數名稱&gt;&#39;
泛型程序是在未提供類型引數清單的情況下所呼叫，而且其中一個類型引數的類型推斷失敗。  
  
 當您呼叫泛型程序時，通常會針對該程序所定義的每個類型參數提供類型引數。 不過，您可以選擇完全省略類型引數清單。 如果您這麼做，編譯器會嘗試從呼叫的內容推斷每個類型引數的類型。 如需詳細資訊，請參閱 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)中的＜類型推斷＞。  
  
 類型推斷失敗的其中一個可能原因是類型參數和呼叫的類型之間次序不符。 以下的程式碼可說明這點。  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 在上述程式碼中，兩個 `findLargest` 呼叫都會產生此錯誤，因為類型參數 `t` 呼叫一維陣列，而編譯器從呼叫推斷的類型引數是純量 \(`testValue`\) 和二維陣列 \(`testMatrix`\)。  
  
 **錯誤 ID︰**BC32050  
  
### 更正這個錯誤  
  
-   請確定一般引數類型的類型推斷是與針對泛型程序所宣告的類型參數一致。  
  
     \-或\-  
  
-   呼叫具有完整類型引數清單的泛型程序，因此不需要類型推斷。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)