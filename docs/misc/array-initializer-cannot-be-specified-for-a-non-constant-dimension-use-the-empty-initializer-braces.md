---
title: "無法指定非常數維度的陣列初始設定式; 請使用空的初始設定式 &#39;{}&#39; | Microsoft Docs"
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
  - "vbc30949"
  - "bc30949"
helpviewer_keywords: 
  - "BC30949"
ms.assetid: b3d27d9c-7a1f-4bac-ad71-388b24b807b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法指定非常數維度的陣列初始設定式; 請使用空的初始設定式 &#39;{}&#39;
陣列初始化編譯時期未知的維度。  
  
 下列程式碼會產生這個錯誤。  
  
```  
Dim j As Integer Dim intArray As Integer = New Integer(1, j) {{0, 100}, {1,101}}  
```  
  
 下列程式碼可避免這個錯誤。  
  
```  
Dim intArray As Integer = New Integer(1, j) {} For i As Integer = 0 To j intArray(0, i) = i intArray(1, i) = 100 + i Next i  
```  
  
 **錯誤 ID︰**BC30949  
  
### 更正這個錯誤  
  
-   如果可能的話，請指定陣列宣告中的常數維度。  
  
-   如果您無法指定常數維度，則必須在非常數維度變成未知時，使用迴圈初始化陣列。  
  
## 請參閱  
 [For Each...Next 陳述式](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)   
 [NOTINBUILD Visual Basic 中的陣列概觀](http://msdn.microsoft.com/zh-tw/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [NOTINBUILD 如何：初始化多維陣列](http://msdn.microsoft.com/zh-tw/502dcf8b-d86c-46f1-ad7d-3ce809645774)