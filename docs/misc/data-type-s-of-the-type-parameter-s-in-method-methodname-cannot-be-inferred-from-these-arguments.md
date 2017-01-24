---
title: "無法從這些引數推斷方法 &#39;&lt;方法名稱&gt;&#39; 中類型參數的資料類型 | Microsoft Docs"
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
  - "vbc36648"
  - "bc36645"
  - "bc36648"
  - "vbc36645"
helpviewer_keywords: 
  - "BC36648"
  - "BC36645"
ms.assetid: cc8c67bb-6cbb-4d7c-ba26-fe1d38908434
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從這些引數推斷方法 &#39;&lt;方法名稱&gt;&#39; 中類型參數的資料類型
無法從這些引數推斷方法 '\<方法名稱\>' 中類型參數的資料類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 嘗試使用類型推斷，來判斷評估泛型程序呼叫時之類型參數 \(參數\) 的資料類型 \(類型\)。 不過，編譯器在這個方法中找不到類型參數的資料類型，並會報告錯誤。  
  
> [!NOTE]
>  當無法指定引數時 \(例如，針對查詢運算式中的查詢運算子\)，會顯示不含第二句的錯誤訊息。  
  
 例如，下列程式碼示範這個錯誤。  
  
```vb#  
Module Module1 Sub Main() '' Not valid. 'GenericMethod("Hello", "World") End Sub Sub GenericMethod(Of T)(ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface  
```  
  
 **錯誤 ID︰**BC36648 和 BC36645  
  
### 更正這個錯誤  
  
-   您可以指定一個或多個類型參數的資料類型，而不是依賴類型推斷。  
  
## 請參閱  
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)