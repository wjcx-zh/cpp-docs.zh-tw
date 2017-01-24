---
title: "無法從這些引數推斷方法 &#39;&lt;方法名稱&gt;&#39; 中類型參數的資料類型，因為可能會有一個以上的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36651"
  - "bc36654"
  - "vbc36651"
  - "vbc36654"
helpviewer_keywords: 
  - "BC36651"
  - "BC36654"
ms.assetid: d4bf408c-ca1f-44ad-855a-3df898de60c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從這些引數推斷方法 &#39;&lt;方法名稱&gt;&#39; 中類型參數的資料類型，因為可能會有一個以上的類型
無法從這些引數推斷方法 '\<方法名稱\>' 中類型參數的資料類型，因為可能會有一個以上的類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 您嘗試使用類型推斷來判斷泛型程序呼叫中的類型參數的類型。 編譯器發現一或多個類型參數的多個可能資料類型，並報告這個錯誤。  
  
> [!NOTE]
>  當無法指定引數時 \(例如，針對查詢運算式中的查詢運算子\)，會顯示不含第二句的錯誤訊息。  
  
 下列程式碼示範這個錯誤。  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. 'targetMethod(1, "2") End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **錯誤 ID：**BC36654 \(在 [!INCLUDE[vbteclinq](../Token/vbteclinq_md.md)] 查詢內\) 和 BC36651 \(在查詢外\)。  
  
### 更正這個錯誤  
  
-   如果錯誤出現在查詢外，請嘗試明確指定類型參數的資料類型：  
  
    ```  
    targetMethod(Of Integer)(1, "2")  
    ```  
  
## 請參閱  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)