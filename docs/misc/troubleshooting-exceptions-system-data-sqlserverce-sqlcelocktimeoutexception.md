---
title: "疑難排解例外狀況：System.Data.SqlServerCe.SqlCeLockTimeoutException | Microsoft Docs"
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
  - "SqlCeLockTimeoutException 例外狀況"
  - "System.Data.SqlServerCe.SqlCeLockTimeoutException 例外狀況"
ms.assetid: 81be7a69-f343-48f0-b94b-c6018df833cf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.SqlServerCe.SqlCeLockTimeoutException
如果達到鎖定逾時，並且 SQL Server Compact 在等待鎖定時發生逾時的情況，就會擲回 `System.Data.SqlServerCe.SqlCeLockTimeoutException` 例外狀況。 預設鎖定逾時為 2000 毫秒。 如需詳細資訊，請參閱 [SQL Server Compact 3.5 類別庫](http://go.microsoft.com/fwlink/?LinkID=102595)。  
  
## 請參閱  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)