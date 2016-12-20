---
title: "&#39;Catch&#39; 無法攔截類型 &#39;&lt;類型名稱&gt;&#39;，因為它不是 &#39;System.Exception&#39; 或繼承自 &#39;System.Exception&#39; 的類別 | Microsoft Docs"
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
  - "vbc30392"
  - "bc30392"
helpviewer_keywords: 
  - "BC30392"
ms.assetid: 1d513d1d-38f5-4b4e-95bb-9f1209553803
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; 無法攔截類型 &#39;&lt;類型名稱&gt;&#39;，因為它不是 &#39;System.Exception&#39; 或繼承自 &#39;System.Exception&#39; 的類別
`Catch` 只能攔截例外狀況，而您已嘗試攔截非衍生自例外狀況的項目。  
  
 **錯誤 ID︰**BC30392  
  
### 更正這個錯誤  
  
1.  移除 `Catch` 陳述式，或將 `Catch` 的目標變更為實際例外狀況。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)