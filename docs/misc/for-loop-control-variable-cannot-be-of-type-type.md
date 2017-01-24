---
title: "&#39;For&#39; 迴圈控制變數不能為類型 &#39;&lt;類型&gt;&#39; | Microsoft Docs"
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
  - "vbc30337"
  - "bc30337"
helpviewer_keywords: 
  - "BC30337"
ms.assetid: 988bba15-e9a2-4045-98a0-7f53c8b2c3e3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;For&#39; 迴圈控制變數不能為類型 &#39;&lt;類型&gt;&#39;
您嘗試使用的迴圈控制變數不是有效的類型。 在 `For` 迴圈開始時，會以文字順序評估起點、結束點和間距值。 這三個運算式必須隱含可以轉換成變數類型的能力。 如果 `For` 迴圈變數屬於類型 `Object`，則執行階段中至少一個運算式必須為數字類型，且所有三個運算式對於三者間最廣泛的數字類型必須是可強迫的。  
  
 **錯誤 ID：**BC30337  
  
### 更正這個錯誤  
  
-   請檢查迴圈控制變數的類型，並將它變更為有效類型。  
  
## 請參閱  
 [For \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/c470a263-9b49-4308-8fd6-8592b84a7980)   
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)   
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)