---
title: "因為引數不會轉換成相同類型，所以無法從這些引數推斷定義在 &#39;typename&#39; 中擴充方法 &#39;&lt;方法名稱&gt;&#39; 內類型參數的資料類型 | Microsoft Docs"
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
  - "vbc36658"
  - "bc36661"
  - "vbc36661"
  - "bc36658"
helpviewer_keywords: 
  - "BC36661"
  - "BC36658"
ms.assetid: 0bff97fd-cbe9-4433-8192-6498c6fb5d04
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 因為引數不會轉換成相同類型，所以無法從這些引數推斷定義在 &#39;typename&#39; 中擴充方法 &#39;&lt;方法名稱&gt;&#39; 內類型參數的資料類型
因為引數不會轉換成相同類型，所以無法從這些引數推斷定義在 'typename' 中擴充方法 '\<方法名稱\>' 內類型參數的資料類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 嘗試使用類型推斷，來判斷評估泛型擴充方法呼叫時之類型參數的資料類型。 編譯器找不到符合所有引數之條件約束的資料類型。 因此，它已回報這個錯誤。  
  
> [!NOTE]
>  當無法指定引數時 \(例如，針對查詢運算式中的查詢運算子\)，會顯示不含第二句的錯誤訊息。  
  
 下列程式碼示範這個錯誤。  
  
```vb#  
Option Strict Off Module Module3 Sub Main() Dim c1 As New Class1 '' Not valid. Integer and Date do not convert to the same type. 'c1.targetMethod(19, #3/4/2007#) End Sub <System.Runtime.CompilerServices.Extension()> _ Sub targetMethod(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **錯誤 ID︰**BC36661 和 BC36658  
  
### 更正這個錯誤  
  
-   您可能可以明確地將一個或多個引數轉換成相容的類型 \(如下列程式碼所示\)：  
  
    ```  
    c1.targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   您可能可以指定引數要轉換為之類型參數或參數的資料類型 \(如下列程式碼所示\)：  
  
    ```  
    c1.targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)