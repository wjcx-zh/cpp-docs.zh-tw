---
title: "擴充方法 &#39;&lt;方法方稱&gt;&#39; (定義於 &#39;&lt;類型名稱&gt;&#39; 中) 的參數 &#39;&lt;參數名稱&gt;&#39; 已經有符合的省略引數 | Microsoft Docs"
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
  - "bc36583"
  - "vbc36583"
helpviewer_keywords: 
  - "BC36583"
ms.assetid: 662072fa-abb8-43c3-8ca2-aefb20f2e902
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 擴充方法 &#39;&lt;方法方稱&gt;&#39; (定義於 &#39;&lt;類型名稱&gt;&#39; 中) 的參數 &#39;&lt;參數名稱&gt;&#39; 已經有符合的省略引數
擴充方法的程序呼叫依位置省略一個引數，然後依名稱提供引數。 例如，擴充方法 `ABC` 的下列呼叫會先忽略參數 `Y` 的引數，然後再依名稱提供。  
  
```  
<Extension()> _ Public Sub ABC(ByVal X As Integer, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) End Sub ' . . . ' Calling extension method ABC. Dim number As Integer ' Not valid. ' number.ABC(, 4, Y:=5)  
```  
  
 **錯誤 ID：**BC36583  
  
### 更正這個錯誤  
  
-   依位置提供引數，或移除省略引數的逗號。  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Passing Arguments by Position and by Name](../Topic/Passing%20Arguments%20by%20Position%20and%20by%20Name%20\(Visual%20Basic\).md)