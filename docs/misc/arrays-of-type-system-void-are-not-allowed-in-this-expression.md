---
title: "此運算式中不允許類型 &#39;System.Void&#39; 的陣列 | Microsoft Docs"
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
  - "vbc31428"
  - "bc31428"
helpviewer_keywords: 
  - "BC31428"
ms.assetid: 21d77b56-585f-4107-b7ec-21933ba58017
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此運算式中不允許類型 &#39;System.Void&#39; 的陣列
指派陳述式或宣告中的運算式指定了 <xref:System.Void> 類型的陣列。  
  
 <xref:System.Void> 結構是 .NET Framework、Visual C\# 和 Visual C\+\+ \(特別是後兩項\) 在內部使用的特殊類型。 它代表不傳回值之方法的傳回值類型。 Visual Basic 會在未傳回值時使用 `Sub` 程序，並在傳回值時使用 `Function` 程序。  
  
 <xref:System.Void> 類型的陣列不具任何意義，而且不可在任何內容中使用。  
  
 **錯誤 ID︰**BC31428  
  
### 更正這個錯誤  
  
1.  移除指定陣列的括弧。  
  
2.  除非您有特別的理由，需要比較執行階段類型與 <xref:System.Void>，否則請移除所有參考。  
  
## 請參閱  
 <xref:System.Void>