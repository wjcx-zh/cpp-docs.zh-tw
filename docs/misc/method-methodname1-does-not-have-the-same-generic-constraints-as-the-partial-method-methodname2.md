---
title: "方法 &#39;&lt;方法名稱1&gt;&#39; 沒有和部分方法 &#39;&lt;方法名稱2&gt;&#39; 相同的泛型條件約束 | Microsoft Docs"
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
  - "bc31438"
  - "vbc31438"
helpviewer_keywords: 
  - "BC31438"
ms.assetid: ea092f0c-661b-49db-80c1-76401fc8bc0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 &#39;&lt;方法名稱1&gt;&#39; 沒有和部分方法 &#39;&lt;方法名稱2&gt;&#39; 相同的泛型條件約束
您已定義部分方法實作，其泛型條件約束與部分方法宣告中的條件約束不同。 下列程式碼說明這個錯誤。  
  
```vb#  
Partial Class Class1 Partial Private Sub Test(Of T As Class)(ByVal arg As T) End Sub End Class Partial Class Class1 '' The error occurs here, for Test. 'Private Sub Test(Of T As Structure)(ByVal arg As T) 'End Sub End Class  
```  
  
 **錯誤 ID︰**BC31438  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)   
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)