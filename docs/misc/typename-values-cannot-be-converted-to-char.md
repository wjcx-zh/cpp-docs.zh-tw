---
title: "&#39;&lt;類型名稱&gt;&#39; 值無法轉換為 &#39;Char&#39; | Microsoft Docs"
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
  - "bc32007"
  - "vbc32007"
helpviewer_keywords: 
  - "BC32007"
ms.assetid: b04212da-57ac-4493-9480-04c12b50f875
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型名稱&gt;&#39; 值無法轉換為 &#39;Char&#39;
'\<類型名稱\>' 值無法轉換為 Char。 使用 'Microsoft.VisualBasic.ChrW' 將數字值解譯為 Unicode 字元，或先將它轉換為 'String' 以產生數字。  
  
 運算式嘗試將資料類型轉換成 `String` 或 `Object` 以外的 `Char`。  
  
 **錯誤識別碼：**BC32007  
  
### 更正這個錯誤  
  
-   使用 `ChrW` 函式將數值轉換成 Unicode 字元，或先將值轉換成 `String` 再轉換成 `Char`。  
  
## 請參閱  
 [不在組建中：Chr、ChrW 函式](http://msdn.microsoft.com/zh-tw/37f3c707-8a6f-4c51-9b02-9e634c4299ab)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Char Data Type](../Topic/Char%20Data%20Type%20\(Visual%20Basic\).md)