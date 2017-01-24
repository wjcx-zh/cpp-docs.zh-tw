---
title: "疑難排解例外狀況：System.Data.SqlServerCe.SqlCeException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Data.SqlServerCe.SqlCeException 例外狀況"
  - "SqlCeException 例外狀況"
  - "SqlServerCe.SqlCeException 例外狀況"
ms.assetid: b0414ab9-94f1-48cc-a2ee-763c005150d5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.SqlServerCe.SqlCeException
當基礎提供者從 SQL Server Compact 資料來源傳回警告或錯誤時，就會擲回 `System.Data.SqlServerCe.SqlCeException` 例外狀況。 如需這個錯誤之原因的詳細資訊，請參閱 MSDN 網站上的 [SQL Server Compact Edition 錯誤](http://msdn2.microsoft.com/library/ms171849.aspx)。  
  
## 備註  
 `System.Data.SqlServerCe.SqlCeException` 永遠都包含至少一個 `System.Data.SqlServerCe.SqlCeError` 的執行個體。 這個類別無法被繼承。  
  
 如需詳細資訊，請參閱 [SQL Server Compact 3.5 類別庫](http://go.microsoft.com/fwlink/?LinkID=102595)。  
  
## 請參閱  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)