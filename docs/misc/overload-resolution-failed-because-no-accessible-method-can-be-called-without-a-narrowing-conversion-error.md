---
title: "多載解析失敗，因為不需要縮小轉換的多載 &#39;&lt;方法&gt;&#39; 不存在，故無法呼叫: &lt;錯誤&gt; | Microsoft Docs"
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
  - "vbc30519"
  - "bc30519"
helpviewer_keywords: 
  - "BC30519"
ms.assetid: 3b3e724d-6fad-4146-b47d-6525493b2fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 多載解析失敗，因為不需要縮小轉換的多載 &#39;&lt;方法&gt;&#39; 不存在，故無法呼叫: &lt;錯誤&gt;
您已呼叫多載的方法，但編譯器找不到可以呼叫且不用縮小轉換的方法。 縮小轉換會將值變更為資料類型，而可能無法精確保留一些可能的值。  
  
 **錯誤 ID︰**BC30519  
  
### 更正這個錯誤  
  
-   請指定 `Option Strict Off`。  
  
## 請參閱  
 [Overloaded Properties and Methods](../Topic/Overloaded%20Properties%20and%20Methods%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)