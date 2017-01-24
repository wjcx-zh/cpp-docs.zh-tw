---
title: "&lt;類型1&gt; &#39;&lt;類型名稱&gt;&#39; 不可宣告為 &#39;Overrides&#39;，因為其在基底 &lt;類型2&gt; 中不會覆寫 &lt;類型1&gt;。 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30284"
  - "bc30284"
helpviewer_keywords: 
  - "BC30284"
ms.assetid: 8166bd09-dad3-495d-8cf7-66f90824a288
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;類型1&gt; &#39;&lt;類型名稱&gt;&#39; 不可宣告為 &#39;Overrides&#39;，因為其在基底 &lt;類型2&gt; 中不會覆寫 &lt;類型1&gt;。
`Sub`、`Function` 或 `Property` 陳述式指定 `Overrides`，但基底類別中沒有相同名稱的類型存在。  
  
 **錯誤 ID︰**BC30284  
  
### 更正這個錯誤  
  
1.  請檢查類型名稱拼寫正確。  
  
2.  請移除多餘的 `Overrides` 關鍵字。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)