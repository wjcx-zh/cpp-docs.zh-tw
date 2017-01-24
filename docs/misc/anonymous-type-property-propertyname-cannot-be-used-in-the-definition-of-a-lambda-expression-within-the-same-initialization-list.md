---
title: "匿名類型屬性 &#39;&lt;屬性名稱&gt;&#39; 不可以使用在相同初始設定清單內的 Lambda 運算式的定義中 | Microsoft Docs"
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
  - "vbc36549"
  - "bc36549"
helpviewer_keywords: 
  - "BC36549"
ms.assetid: 6d04692a-957a-41ce-a19c-fcb06a186d1a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 匿名類型屬性 &#39;&lt;屬性名稱&gt;&#39; 不可以使用在相同初始設定清單內的 Lambda 運算式的定義中
匿名類型之初始設定清單中所定義的屬性不能是相同清單中 Lambda 運算式定義的一部分。 例如，在下列程式碼中，屬性 `Num` 不能包括在 `LambdaFun` 的定義中。  
  
```vb#  
' Not valid.  
'Dim anon = New With {.Num = 4, .LambdaFun = Function() .Num > 0}  
```  
  
 **錯誤 ID︰**BC36549  
  
### 更正這個錯誤  
  
1.  請考慮將匿名類型分割成兩個部分：  
  
    ```vb#  
    Dim anon1 = New With {.Num = 4}  
    Dim anon2 = New With {.LambdaFun = Function() anon1.Num > 0}  
    ' - or -  
    Dim anon3 = New With {.lambdaFun = Function(n As Integer) n > 0}  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    anon1.Num = -5  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    ```  
  
     請注意，如果您將 `anon1.Num` 宣告為 `Key` 屬性，就無法變更其值。  
  
2.  替代方法是使用一般函式陳述式來存取匿名類型屬性：  
  
    ```vb#  
    Function testNum(ByVal n As Integer) As Boolean  
        Return n > 0  
    End Function  
    Console.WriteLine(testNum(anon1.Num))  
    ```  
  
3.  同樣地，您可以使用在匿名類型外部定義的 Lambda 函式：  
  
    ```vb#  
    Dim lambdaFun1 = Function() anon1.Num > 0  
    Dim lambdaFun2 = Function(n As Integer) n > 0  
    ```  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [Anonymous Types](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)