---
title: "陳述式遞迴呼叫事件 &#39;&lt;事件名稱&gt;&#39; 包含的 &#39;AddHandler&#39; | Microsoft Docs"
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
  - "bc41998"
  - "vbc41998"
helpviewer_keywords: 
  - "BC41998"
ms.assetid: 4375b191-fbd9-4e93-b9bb-9159d533ddf6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陳述式遞迴呼叫事件 &#39;&lt;事件名稱&gt;&#39; 包含的 &#39;AddHandler&#39;
事件定義之 `AddHandler` 存取子中的陳述式不得直接參考事件。  
  
 建議的方法是將事件處理常式清單儲存為已定義事件之類別、結構或模組中的私用欄位。 如需詳細資訊，請參閱[How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)與[How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC41998  
  
### 更正這個錯誤  
  
-   請重寫事件定義，以避免遞迴。  
  
## 請參閱  
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [Event Statement](../Topic/Event%20Statement.md)   
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)