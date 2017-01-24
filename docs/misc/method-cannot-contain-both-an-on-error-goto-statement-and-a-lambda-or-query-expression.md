---
title: "方法不能同時包含 &#39; On Error GoTo&#39; 陳述式和 Lambda 或查詢運算式 | Microsoft Docs"
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
  - "bc36595"
  - "vbc36595"
helpviewer_keywords: 
  - "BC36595"
ms.assetid: 4e7cc11e-f53d-4481-afb4-653a81d54483
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法不能同時包含 &#39; On Error GoTo&#39; 陳述式和 Lambda 或查詢運算式
方法同時包含 `On Error Goto` 陳述式和 Lambda 運算式或 LINQ 查詢。 您不能在方法中包含 `On Error Goto` 陳述式以及 Lambda 運算式或 LINQ 查詢。  
  
 **錯誤 ID︰**BC36595  
  
### 更正這個錯誤  
  
1.  請將使用 `On Error Goto` 陳述式的例外狀況處理程式碼取代為 `Try...Catch` 陳述式。  
  
## 請參閱  
 [例外狀況處理簡介 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/9792f16a-0cd2-40bd-ace2-f7a4344c0e52)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [On Error Statement](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)