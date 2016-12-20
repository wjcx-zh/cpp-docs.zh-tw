---
title: "&#39;Throw&#39; 陳述式不可以在 &#39;Catch&#39; 陳述式外或 &#39;Finally&#39; 陳述式內省略運算元 | Microsoft Docs"
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
  - "vbc30666"
  - "bc30666"
helpviewer_keywords: 
  - "BC30666"
ms.assetid: a208a6ea-0e36-4bf1-8984-4de1a0e38a2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Throw&#39; 陳述式不可以在 &#39;Catch&#39; 陳述式外或 &#39;Finally&#39; 陳述式內省略運算元
`Catch` 陳述式外的 `Throw` 陳述式必須提供例外狀況物件的名稱。  
  
 **錯誤 ID：**BC30666  
  
### 更正這個錯誤  
  
1.  指定衍生自 `System.Exception` 之例外狀況物件的名稱。  
  
2.  重建您的程式碼，讓 `Throw` 陳述式位於 `Catch` 區塊內。  
  
## 請參閱  
 [Throw Statement](../Topic/Throw%20Statement%20\(Visual%20Basic\).md)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 中的例外狀況類別](http://msdn.microsoft.com/zh-tw/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)