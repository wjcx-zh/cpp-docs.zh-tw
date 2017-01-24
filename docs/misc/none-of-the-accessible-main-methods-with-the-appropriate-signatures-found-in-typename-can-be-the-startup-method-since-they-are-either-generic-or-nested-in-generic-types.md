---
title: "在 &#39;&lt;類型名稱&gt;&#39; 中所找到具有適當簽章之可存取的 &#39;Main&#39; 方法，沒有任何一個可作為啟動方法，因為這些方法可能是泛型類型或是泛型類型中的巢狀類型 | Microsoft Docs"
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
  - "vbc30796"
  - "BC30796"
helpviewer_keywords: 
  - "BC30796"
ms.assetid: 606b3629-5a92-4c79-ace2-a530cab8c978
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;&lt;類型名稱&gt;&#39; 中所找到具有適當簽章之可存取的 &#39;Main&#39; 方法，沒有任何一個可作為啟動方法，因為這些方法可能是泛型類型或是泛型類型中的巢狀類型
類別、模組或結構沒有可作為專案啟動程序的任何 `Main` 程序。  
  
 Visual Basic 要求專案的啟動程序不得相依於類型引數。 因此，它必須能夠存取至少一個非泛型且未包含在任何泛型類型中的 `Main` 程序。  
  
 **錯誤 ID︰**BC30796  
  
### 更正這個錯誤  
  
-   定義 `Main` 程序的其中至少一個，使其非泛型且未包含在泛型類型中。  
  
     \-或\-  
  
-   在專案的 \[屬性\] 頁上，為 \[啟動表單\] 或 \[啟始物件\] 指定不同的表單或模組。  
  
## 請參閱  
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [NIB：Visual Basic 版的 Hello, World](http://msdn.microsoft.com/zh-tw/9d030b60-e148-4366-a462-69532f02294c)