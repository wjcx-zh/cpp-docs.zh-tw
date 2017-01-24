---
title: "疑難排解例外狀況：System.Data.ConstraintException | Microsoft Docs"
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
  - "ConstraintException 類別"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.ConstraintException
嘗試進行違反條件約束的動作時，就會擲回 <xref:System.Data.ConstraintException> 例外狀況。  
  
## 相關秘訣  
 **請放寬或關閉資料集中的條件約束**。  
 填入 <xref:System.Data.DataSet.EnforceConstraints%2A> 物件中的資料表時，您可以使用 <xref:System.Data.DataSet> 屬性暫時關閉條件約束。  
  
 **確定您未嘗試將值指定至主索引鍵欄位，而此欄位中的主索引鍵已存在於資料表中。**  
 如果該主索引鍵已存在，就會擲回這個例外狀況。  
  
 **請先清除資料集，然後再從檢視狀態載入它們。**  
 如果載入資料集之前，資料集中已有資料，可能會擲回這個例外狀況。  
  
## 請參閱  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)