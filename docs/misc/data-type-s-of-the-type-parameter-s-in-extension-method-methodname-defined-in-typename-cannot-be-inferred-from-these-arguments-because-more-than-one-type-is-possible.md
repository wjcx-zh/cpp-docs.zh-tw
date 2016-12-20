---
title: "因為可能的類型不只一種，所以無法從這些引數推斷定義在 &#39;&lt;類型名稱&gt;&#39; 中擴充方法 &#39;&lt;方法名稱&gt;&#39; 內類型參數的資料類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36655"
  - "vbc36652"
  - "vbc36655"
  - "bc36652"
helpviewer_keywords: 
  - "BC36655"
  - "BC36652"
ms.assetid: 49836f20-c877-4267-8bdc-6f6d108fb8c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 因為可能的類型不只一種，所以無法從這些引數推斷定義在 &#39;&lt;類型名稱&gt;&#39; 中擴充方法 &#39;&lt;方法名稱&gt;&#39; 內類型參數的資料類型
因為可能的類型不只一種，所以無法從這些引數推斷定義在 '\<類型名稱\>' 中擴充方法 '\<方法名稱\>' 內類型參數的資料類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 嘗試使用類型推斷來判斷泛型擴充方法呼叫中之類型參數的類型。 編譯器發現一或多個類型參數的多個可能資料類型，並報告這個錯誤。  
  
> [!NOTE]
>  當無法指定引數時 \(例如，針對查詢運算式中的查詢運算子\)，會顯示不含第二句的錯誤訊息。  
  
 下列程式碼示範這個錯誤。  
  
```vb#  
Option Strict Off Imports System.Runtime.CompilerServices Module Module1 Sub Main() Dim caller As New Class1 '' Not valid. 'caller.targetExtension(1, "2") End Sub <Extension()> _ Sub targetExtension(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **錯誤 ID：**BC36655 \(在 [!INCLUDE[vbteclinq](../Token/vbteclinq_md.md)] 查詢內\) 和 BC36652 \(在查詢外\)  
  
### 更正這個錯誤  
  
-   如果錯誤出現在查詢外，請嘗試明確指定類型參數的資料類型：  
  
    ```  
    caller.targetExtension(Of Integer)(1, "2") caller.targetExtension(Of String)(1, "2")  
    ```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)