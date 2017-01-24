---
title: "屬性成員 &#39;&lt;成員名稱&gt;&#39; 不可以是指派的目標，因為它未宣告為 &#39;Public&#39; | Microsoft Docs"
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
  - "vbc31511"
  - "bc31511"
helpviewer_keywords: 
  - "BC31511"
ms.assetid: f8c958f6-58a4-4aff-b8c3-f2e9481e8132
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性成員 &#39;&lt;成員名稱&gt;&#39; 不可以是指派的目標，因為它未宣告為 &#39;Public&#39;
已嘗試指派值給屬性的私用成員。  
  
 **錯誤 ID︰**BC31511  
  
### 更正這個錯誤  
  
1.  移除指派。  
  
2.  如果使用您所開發的自訂屬性，請將屬性成員的存取修飾詞變更為 `Public`。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)