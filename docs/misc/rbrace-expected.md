---
title: "必須是 &#39;}&#39; | Microsoft Docs"
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
  - "vbc30370"
  - "bc30370"
helpviewer_keywords: 
  - "BC30370"
ms.assetid: a4ce9be9-fc5d-46ec-a217-c3428bd0b97e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;}&#39;
陣列初始設定式或條件約束清單未以有效的形式結束。  
  
 用來初始化陣列的項目值必須括在大括弧 \(`{}`\) 內。  
  
```  
Dim demoArray() As Integer = New Integer() {1, 2, 3}   
```  
  
 同樣地，泛型類型參數之條件約束清單中的條件約束必須括在大括弧內。  
  
```  
Public Class dictionaryMaker(Of t As {IComparable, IDisposable, New})   
```  
  
 **錯誤 ID︰**BC30370  
  
### 更正這個錯誤  
  
-   使用 "}" 結束陣列初始設定式或條件約束清單。  
  
## 請參閱  
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)