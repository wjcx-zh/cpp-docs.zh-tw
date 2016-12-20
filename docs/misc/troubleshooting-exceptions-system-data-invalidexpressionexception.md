---
title: "疑難排解例外狀況：System.Data.InvalidExpressionException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidExpressionException 類別"
ms.assetid: 2de49b17-4b3f-46e0-bf5c-01b075ddbd5c
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.InvalidExpressionException
嘗試將包含無效 <xref:System.Data.InvalidExpressionException> 的 <xref:System.Data.DataColumn> 加入至 <xref:System.Data.DataColumn.Expression%2A> 時，就會擲回 <xref:System.Data.DataColumnCollection> 例外狀況。  
  
## 相關秘訣  
 **請檢查運算式的語法。**  
 <xref:System.Data.DataColumn.Expression%2A> 屬性是用以計算資料行的值，或用於建立彙總資料行。  
  
## 請參閱  
 <xref:System.Data.InvalidExpressionException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)