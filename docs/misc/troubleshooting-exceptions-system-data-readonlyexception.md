---
title: "疑難排解例外狀況：System.Data.ReadOnlyException | Microsoft Docs"
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
  - "ReadOnlyException 類別"
ms.assetid: 1ac5da38-c5af-4fec-8fe1-1b9dd5069e59
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.ReadOnlyException
嘗試變更唯讀資料行的值時，就會擲回 <xref:System.Data.ReadOnlyException> 例外狀況。  
  
## 相關秘訣  
 **將資料行變更為讀取\/寫入。**  
 如果您嘗試變更唯讀資料行的值，就會擲回這個例外狀況。 如需詳細資訊，請參閱<xref:System.Data.DataColumn>。  
  
 **請確認您在正確的資料行中修改資料。**  
 如果您嘗試變更唯讀資料行的值，就會擲回這個例外狀況。 如需詳細資訊，請參閱<xref:System.Data.DataColumn>。  
  
## 請參閱  
 <xref:System.Data.ReadOnlyException>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)