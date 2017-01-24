---
title: "不可以使用 &#39;New&#39; 宣告陣列 | Microsoft Docs"
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
  - "vbc30053"
  - "bc30053"
helpviewer_keywords: 
  - "BC30053"
ms.assetid: aa55f3b7-2045-497b-9543-5ec6e2b74fe2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不可以使用 &#39;New&#39; 宣告陣列
`New` 關鍵字只能出現在陣列宣告的初始設定部分。 這表示 `New` 必須在等號 \(`=`\) 右邊，以便建立要指派給陣列變數的新陣列類型。  
  
 類別初始設定的捷徑不能用於陣列。 下列兩行程式碼都有效且對等，因為它們會從類別初始化物件。  
  
```  
Dim formA as Form = New Form Dim formA as New Form  
```  
  
 不過，陣列初始設定無法使用與類別初始設定相同的捷徑。  
  
 請注意，陣列的 `New` 子句必須同時包含括弧 `()` 和大括弧 `{}`。 括弧指定新的類型是一個陣列，而大括弧則提供初始設定值。 編譯器需要大括弧，即使它們是空的，也就是說，即使您未初始化任何陣列值。  
  
 **錯誤 ID︰**BC30053  
  
### 更正這個錯誤  
  
-   請將陳述式，例如 `Dim myDates() As New Date` 取代為例如 `Dim myDates() As Date = New Date() {}` 的陳述式。  
  
## 請參閱  
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)