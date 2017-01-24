---
title: "無法從這些引數推斷定義在 &#39;&lt;類型名稱&gt;&#39; 中擴充方法 &#39;&lt;方式名稱&gt;&#39; 內類型參數的資料類型 | Microsoft Docs"
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
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36646"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從這些引數推斷定義在 &#39;&lt;類型名稱&gt;&#39; 中擴充方法 &#39;&lt;方式名稱&gt;&#39; 內類型參數的資料類型
無法從這些引數推斷定義在 '\<類型名稱\>' 中擴充方法 '\<方式名稱\>' 內類型參數的資料類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 嘗試使用類型推斷，來判斷評估泛型擴充方法呼叫時之類型參數的資料類型。 不過，編譯器在這個方法中找不到類型參數的資料類型，並會報告錯誤。  
  
> [!NOTE]
>  當無法指定引數時 \(例如，針對查詢運算式中的查詢運算子\)，會顯示不含第二句的錯誤訊息。  
  
 下列程式碼示範這個錯誤。  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **錯誤 ID︰**BC36649 和 BC36646  
  
### 更正這個錯誤  
  
-   您可以指定一個或多個類型參數的資料類型，而不是依賴類型推斷。  
  
## 請參閱  
 [Relaxed Delegate Conversion](../Topic/Relaxed%20Delegate%20Conversion%20\(Visual%20Basic\).md)   
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)