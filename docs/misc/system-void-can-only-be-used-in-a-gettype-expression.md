---
title: "&#39;System.Void&#39; 只能使用於 GetType 運算式 | Microsoft Docs"
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
  - "bc31422"
  - "vbc31422"
helpviewer_keywords: 
  - "BC31422"
ms.assetid: 84e45194-cb46-41f6-8420-a1498baeaaba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Void&#39; 只能使用於 GetType 運算式
指派陳述式或宣告中的運算式使用 <xref:System.Void> 作為變數、程序參數、函式傳回或類型引數的類型。  
  
 <xref:System.Void> 結構是 .NET Framework、Visual C\# 和 Visual C\+\+ \(特別是後兩項\) 在內部使用的特殊類型。 它代表不傳回值之方法的傳回值類型。 Visual Basic 會在未傳回值時使用 `Sub` 程序，並在傳回值時使用 `Function` 程序。  
  
 您可以使用 [GetType Operator](../Topic/GetType%20Operator%20\(Visual%20Basic\).md) 運算子測試參考變數，以查看其執行階段類型是否為 <xref:System.Void>，但無法在任何其他內容中使用 <xref:System.Void>。  
  
 **錯誤 ID︰**BC31422  
  
### 更正這個錯誤  
  
1.  如果您想要比較變數的執行階段類型與 <xref:System.Void>，請使用 `GetType` 運算子。  
  
2.  除非您有特別的理由，需要比較執行階段類型與 <xref:System.Void>，否則請移除所有參考。  
  
## 請參閱  
 <xref:System.Void>   
 [GetType Operator](../Topic/GetType%20Operator%20\(Visual%20Basic\).md)