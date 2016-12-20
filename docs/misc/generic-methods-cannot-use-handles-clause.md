---
title: "泛型方法不可以使用 &#39;Handles&#39; 子句 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32080"
  - "BC32080"
helpviewer_keywords: 
  - "BC32080"
ms.assetid: 88c62a1c-aee3-46b2-ad78-76790022c04c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型方法不可以使用 &#39;Handles&#39; 子句
泛型 `Sub` 程序在其宣告中包含 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md) 子句。  
  
 `Handles` 子句指定 `Sub` 程序所處理的事件清單。 若要成為事件處理常式，`Sub` 程序所擁有的簽章必須與其處理的每個事件相同。 使用 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 在編譯時期無法預測的簽章，可以多次建立泛型程序。 因此，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法保證與 `Handles` 子句中事件之簽章相符的簽章。  
  
 **錯誤 ID︰**BC32080  
  
### 更正這個錯誤  
  
-   如果 `Sub` 程序必須為泛型，請從其宣告中移除 `Handles` 子句。 使用 [AddHandler Statement](../Topic/AddHandler%20Statement.md) 建立這個事件處理常式與某個事件的關聯。  
  
-   如果 `Sub` 程序必須使用 `Handles` 子句來關聯事件，請從其宣告中移除 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md) 子句。 您必須搭配使用非泛型程序與 `Handles`。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [不在組建中：事件和事件處理常式](http://msdn.microsoft.com/zh-tw/95074a0d-1cbc-4221-a95a-964185c7f962)