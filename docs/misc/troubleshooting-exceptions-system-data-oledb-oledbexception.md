---
title: "疑難排解例外狀況：System.Data.OleDb.OleDbException | Microsoft Docs"
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
  - "OLEDB"
  - "OleDbException 類別"
  - "例外狀況, OLEDB"
ms.assetid: f50077cf-e411-41f0-b73e-19eef83036c1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.OleDb.OleDbException
當 OLE DB 資料來源傳回警告或錯誤時，就會產生 <xref:System.Data.OleDb.OleDbException> 例外狀況。  
  
## 相關秘訣  
 **請確認您是用有效認證連接。**  
 確定所提供的認證都是有效的。 如需詳細資訊，請參閱<xref:System.Data.OleDb.OleDbErrorCollection>。  
  
 **請確定伺服器名稱是正確的，而且該伺服器正在執行。**  
 確定您使用正確的伺服器名稱，而且確實可以到達伺服器。 如需詳細資訊，請參閱<xref:System.Data.OleDb.OleDbErrorCollection>。  
  
### 備註  
 當 .NET Framework Data Provider for OLE DB 遇到伺服器所產生的錯誤時，就會擲回這個例外狀況。  
  
 如果發生嚴重錯誤，伺服器可能會關閉 <xref:System.Data.OleDb.OleDbConnection>。 但是，使用者可以再次開啟連線，然後繼續進行。  
  
## 請參閱  
 <xref:System.Data.OleDb.OleDbException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)