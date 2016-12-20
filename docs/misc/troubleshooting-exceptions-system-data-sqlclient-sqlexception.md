---
title: "疑難排解例外狀況：System.Data.SqlClient.SqlException | Microsoft Docs"
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
  - "SqlException 類別"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.SqlClient.SqlException
當 SQL Server 傳回警告或錯誤時，就會產生 <xref:System.Data.SqlClient.SqlException> 例外狀況。  
  
## 相關秘訣  
 **請確認您是用有效認證連接。**  
 確定所提供的認證都是有效的。 如需詳細資訊，請參閱[How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)。  
  
 **請確定伺服器名稱是正確的，而且該伺服器正在執行。**  
 確定您使用正確的伺服器名稱，而且確實可以到達伺服器。  
  
### 備註  
 每當 .NET Framework Data Provider for SQL Server 發生伺服器產生的錯誤時，便會擲回這個例外狀況。  
  
 安全性層級 10 或以下的訊息是告知性的訊息，用以指出問題產生的原因是使用者輸入了錯誤的資訊。 安全性層級 11 至 16 是由使用者所產生，可以由使用者進行更正。 17 到 25 的嚴重性層級表示軟體或硬體錯誤。 發生層級 17、18，或 19 的錯誤時，您可以繼續工作，但可能無法執行特定的陳述式。  
  
 當嚴重性層級為 19 或低於 19 時，<xref:System.Data.SqlClient.SqlConnection> 仍保持開啟。 發生 20 或以上的安全性層級時，伺服器通常會關閉 <xref:System.Data.SqlClient.SqlConnection>。 但是，使用者可以再次開啟連線，然後繼續進行。 在這兩個情況中，<xref:System.Data.SqlClient.SqlException> 皆由執行該命令的方法所產生。  
  
 如需 SQL Server 所傳送的警告和告知性訊息，請參閱《SQL Server 線上書籍》的＜疑難排解＞一節。  
  
## 請參閱  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)