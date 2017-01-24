---
title: "執行個體成員和 &#39;Me&#39; 不能用於結構中的 Lambda 運算式。 | Microsoft Docs"
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
  - "vbc36638"
  - "bc36638"
helpviewer_keywords: 
  - "BC36638"
ms.assetid: 5c24a7c7-50f6-4ffb-9ed2-07e2abc4eaf3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 執行個體成員和 &#39;Me&#39; 不能用於結構中的 Lambda 運算式。
從結構內，您已定義 Lambda 運算式指向結構的執行個體成員或使用 `Me`。 下列程式碼會示範這兩個無效的參考。  
  
```vb#  
Structure Structure1 Public InstanceMember As Integer Public Function ExampleFun() As Integer '' The error is caused by use of InstanceMember. 'Dim fun1 = Function() InstanceMember '' The error is caused by use of Me. 'Dim fun2 = Function() Me.InstanceMember 'Return fun1() End Function End Structure  
```  
  
 **錯誤識別碼：**BC36638  
  
### 更正這個錯誤  
  
-   將執行個體成員指派給區域變數，並在您的陳述式中使用區域變數。  
  
    ```vb#  
    Public Function ExampleFunFix() As Integer Dim temp = InstanceMember Dim fun1 = Function() temp Return fun1() End Function  
    ```  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [我](http://msdn.microsoft.com/zh-tw/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Structure Statement](../Topic/Structure%20Statement.md)