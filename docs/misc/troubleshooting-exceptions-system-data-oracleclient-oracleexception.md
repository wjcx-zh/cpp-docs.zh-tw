---
title: "疑難排解例外狀況：System.Data.OracleClient.OracleException | Microsoft Docs"
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
  - "OracleException 類別"
  - "Oracle"
  - "例外狀況, Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.OracleClient.OracleException
當 Oracle 資料庫或 .NET Framework Data Provider for Oracle 傳回警告或錯誤時，就會產生 <xref:System.Data.OracleClient.OracleException> 例外狀況。  
  
## 相關秘訣  
 **請確認您是用有效認證連接。**  
 確定所提供的認證都是有效的。  
  
 **請確定伺服器名稱是正確的，而且該伺服器正在執行。**  
 確定您使用正確的伺服器名稱，而且確實可以到達伺服器。  
  
## 備註  
 每當 <xref:System.Data.OracleClient.OracleDataAdapter> 發生伺服器產生的錯誤時，就會擲回這個例外狀況。  
  
 如果發生嚴重錯誤，伺服器可能會關閉 <xref:System.Data.OracleClient.OracleConnection>。 但是，使用者可以再次開啟連線，然後繼續進行。  
  
## 請參閱  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)