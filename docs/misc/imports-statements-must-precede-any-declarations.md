---
title: "&#39;Imports&#39; 陳述式必須位在任何宣告之前。 | Microsoft Docs"
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
  - "vbc30465"
  - "bc30465"
helpviewer_keywords: 
  - "BC30465"
ms.assetid: 726365f6-d6fc-454a-a43b-afa41bfea82a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Imports&#39; 陳述式必須位在任何宣告之前。
`Imports` 陳述式接在原始程式檔內的宣告陳述式後面。  
  
 `Imports` 陳述式從參考的專案和組件中匯入命名空間名稱，以及在它出現的專案內定義的命名空間名稱。`Imports` 陳述式必須放在原始程式檔中，在任何識別項參考之前。  
  
 **錯誤識別碼︰**BC30465  
  
### 更正這個錯誤  
  
-   將 `Imports` 陳述式移至原始程式檔的上方，在任何宣告陳述式之前。  
  
## 請參閱  
 [Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)