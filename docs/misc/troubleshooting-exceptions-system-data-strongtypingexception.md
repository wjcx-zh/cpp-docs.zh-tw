---
title: "疑難排解例外狀況：System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StrongTypingException 類別"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.StrongTypingException
當使用者存取強型別 <xref:System.Data.StrongTypingException> 中的 <xref:System.DBNull> 值時發生 <xref:System.Data.DataTable.DataSet%2A>。  
  
## 相關秘訣  
 **請加入 StrongTypingException 的錯誤處理。**  
 將存取 <xref:System.Data.DataTable.DataSet%2A> 的程式碼放置在 `Try…Catch` 區塊中，並攔截 <xref:System.Data.StrongTypingException>。  
  
## 請參閱  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [使用 Visual Studio 中的資料集](../Topic/Dataset%20tools%20in%20Visual%20Studio.md)