---
title: "無法在具有 &#39;As New&#39; 的變數宣告中指定可為 Null 的修飾詞 | Microsoft Docs"
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
  - "bc33109"
  - "vbc33109"
helpviewer_keywords: 
  - "BC33109"
ms.assetid: 135def20-3535-4239-bffb-43208d1b3f63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法在具有 &#39;As New&#39; 的變數宣告中指定可為 Null 的修飾詞
在指定 `As New` 的變數宣告中已包括可為 Null 的類型修飾詞 \(?\)。 下列範例會產生這個錯誤：  
  
```vb#  
Dim num? As New ExampleStructure  
```  
  
 **錯誤 ID︰**BC33109  
  
### 更正這個錯誤  
  
1.  請從可為 Null 的變數宣告中移除 `New` 關鍵字 \(如下列範例所示\)：  
  
    ```vb#  
    Dim num? As ExampleStructure  
    ```  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)