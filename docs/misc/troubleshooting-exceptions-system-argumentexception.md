---
title: "疑難排解例外狀況：System.ArgumentException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ArgumentException 例外狀況"
  - "System.ArgumentException 例外狀況"
ms.assetid: d8052e62-bc73-4828-87e9-a84ef2a39a5b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.ArgumentException
提供給方法的引數中，如果至少有一個不符合方法的參數規格，就會擲回 <xref:System.ArgumentException> 例外狀況。  
  
 在下列範例中，當傳送給 `DivideByTwo` 方法的引數不是偶數時，會擲回例外狀況。  
  
```vb#  
Module Module1 Sub Main() ' ArgumentException is not thrown in DivideByTwo because 10 is ' an even number. Console.WriteLine("10 divided by 2 is {0}", DivideByTwo(10)) Try ' ArgumentException is thrown in DivideByTwo because 7 is ' not an even number. Console.WriteLine("7 divided by 2 is {0}", DivideByTwo(7)) Catch argEx As ArgumentException ' Tell the user which problem is encountered. Console.WriteLine("7 cannot be evenly divided by 2.") Console.WriteLine("Exception message: " & argEx.Message) End Try ' Uncomment the next statement to see what happens if you call ' DivideByTwo directly. 'Console.WriteLine(DivideByTwo(7)) End Sub Function DivideByTwo(ByVal num As Integer) As Integer ' If num is an odd number, throw an ArgumentException. The ' ArgumentException class provides a number of constructors ' that you can choose from. If num Mod 2 = 1 Then Throw New ArgumentException("Argument for num must be" & _ " an even number.") End If ' Value of num is even, so return half of its value. Return num / 2 End Function End Module  
```  
  
 `ArgumentException` 類別的所有執行個體都應該包括指定哪個引數無效、可接受值的範圍等相關資訊。 如果有更精確的例外狀況 \(例如 <xref:System.ArgumentNullException> 或 <xref:System.ArgumentOutOfRangeException>\) 能夠更正確地描述狀況，則應改用這種例外狀況，取代 `ArgumentException`。  
  
 如需此例外狀況的詳細資訊，包括其他語言的範例，請參閱 <xref:System.ArgumentException>。 如需其他建構函式 \(Constructor\) 的清單，請參閱 <xref:System.ArgumentException.%23ctor%2A>。  
  
## 請參閱  
 <xref:System.ArgumentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)