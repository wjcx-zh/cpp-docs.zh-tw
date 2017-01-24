---
title: "Lambda 運算式不可以轉換成 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;&lt;類型名稱&gt;&#39; 不是委派類型 | Microsoft Docs"
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
  - "bc36625"
  - "vbc36625"
helpviewer_keywords: 
  - "BC36625"
ms.assetid: c03634d4-d831-4f8c-b6ab-566465968e4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lambda 運算式不可以轉換成 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;&lt;類型名稱&gt;&#39; 不是委派類型
可以使用委派有效的 Lambda 運算式。 它們可以轉換成相容的委派類型，但無法轉換成任何其他類型。 例如，您可以定義委派類型，並指派其 Lambda 運算式，或傳送 Lambda 運算式作為 <xref:System.Func%601> 參數的引數。 下列程式碼顯示這些範例。  
  
```vb#  
Module Module1 Delegate Function FunDel(ByVal m As Integer) As Boolean Sub Main() ' Assign a lambda expression to a function delegate. Dim negative As FunDel = Function(n As Integer) n < 0 Console.WriteLine(negative(-3)) ' Send a lambda as the argument to a delegate parameter. Dim numbers() As Integer = {3, 4, 2, 8, 1, 0, 9, 13, 42} Dim evens = numbers.Where(Function(n) n Mod 2 = 0) For Each even In evens Console.WriteLine(even) Next End Sub End Module  
```  
  
 **錯誤 ID︰**BC36625  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)