---
title: "不再支援 Property Get/Let/Set；請使用新的 Property 宣告語法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30808"
  - "bc30808"
helpviewer_keywords: 
  - "BC30808"
ms.assetid: c8a803eb-316d-4f73-b6ef-27a2914409f3
caps.latest.revision: 10
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不再支援 Property Get/Let/Set；請使用新的 Property 宣告語法
不再支援 `Property Get/Let/Set`；請使用新的 `Property` 宣告語法。  
  
 宣告屬性的語法已變更。 屬性現在定義於區塊內。  
  
 **錯誤 ID︰**BC30808  
  
### 更正這個錯誤  
  
1.  在開頭為 `Property` 關鍵字的程式碼區塊中定義屬性。 使用 `End Property` 建構來結束屬性。  
  
2.  使用 `Get` 關鍵字，在屬性區塊內定義 `Get` 屬性程序。 使用 `End Get` 建構來結束 `Get` 屬性程序。  
  
3.  使用 `Set` 關鍵字，在屬性區塊內定義 `Set` 屬性程序。 使用 `End Set` 建構來結束 `Set` 屬性程序。  
  
4.  使用 `Set` 屬性程序進行所有屬性指派。 不再需要或支援 `Let` 屬性程序。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Language Changes in Visual Basic](http://msdn.microsoft.com/zh-tw/a1be4461-a0e4-4a88-a32c-dcad41ed119a)