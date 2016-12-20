---
title: "&#39;Char&#39; 的值無法轉換成 &#39;&lt;類型名稱&gt;&#39; | Microsoft Docs"
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
  - "bc32006"
  - "vbc32006"
helpviewer_keywords: 
  - "BC32006"
ms.assetid: c033f65e-a315-47fc-be2e-ed371847a221
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Char&#39; 的值無法轉換成 &#39;&lt;類型名稱&gt;&#39;
'Char' 的值無法轉換成 '\<類型名稱\>'。 使用 Microsoft.VisualBasic.AscW 將字元解譯為 Unicode 值，或使用 Microsoft.VisualBasic.Val 將它解譯為數字。  
  
 運算式嘗試將 `Char` 值轉換成 `String` 或 `Object` 以外的資料類型。  
  
 **錯誤 ID︰**BC32006  
  
### 更正這個錯誤  
  
-   使用 `AscW` 函式將 `Char` 值解譯為 Unicode 字元碼，或使用 `Val` 函式將它解譯為數字。  
  
## 請參閱  
 [不在組建中：Asc、AscW 函式](http://msdn.microsoft.com/zh-tw/6814bfec-12ba-41fb-b10e-bec99750d5e1)   
 [不在組建中：Val 函式](http://msdn.microsoft.com/zh-tw/81650f77-9242-4ec1-8e04-e93b5daa451d)   
 [Char Data Type](../Topic/Char%20Data%20Type%20\(Visual%20Basic\).md)