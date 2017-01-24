---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 必須是實值類型或已限制為 &#39;Structure&#39; 的類型引數，才能與 &#39;Nullable&#39; 或可為 Null 的修飾詞 &#39;?&#39; 搭配使用 | Microsoft Docs"
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
  - "vbc33101"
  - "bc33101"
helpviewer_keywords: 
  - "BC33101"
ms.assetid: b3e0e4e4-87b8-4a38-a450-15233497acaa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 必須是實值類型或已限制為 &#39;Structure&#39; 的類型引數，才能與 &#39;Nullable&#39; 或可為 Null 的修飾詞 &#39;?&#39; 搭配使用
只有實值類型 \(包括結構\) 才能宣告為可為 Null。  
  
```vb#  
' Valid. Dim n? As Integer Dim m As Integer? ' Not valid. ' Dim p? As Object ' Dim q As Nullable(Of Object)  
```  
  
 **錯誤 ID︰**BC33101  
  
### 更正這個錯誤  
  
-   移除 '?' 或 `Nullable`。  
  
-   使用實值資料類型。  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)