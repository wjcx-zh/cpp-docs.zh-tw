---
title: "疑難排解例外狀況：System.Data.Odbc.OdbcException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHOdbc"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "例外狀況, ODBC"
  - "ODBC, 例外狀況"
  - "OdbcException 類別"
ms.assetid: 5f2c2167-cf7b-4634-af86-44dc71eff02d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Data.Odbc.OdbcException
當 ODBC 資料來源傳回警告或錯誤時，就會產生 <xref:System.Data.Odbc.OdbcException> 例外狀況。  
  
## 相關秘訣  
 **請確認您是用有效認證連接。**  
 檢查您的認證，確定認證是有效的。  
  
 **請確定伺服器名稱是正確的，而且該伺服器正在執行。**  
 請確定您使用的是正確的伺服器名稱，而且此伺服器是可連線的。  
  
## 備註  
 每當 <xref:System.Data.Odbc.OdbcDataAdapter> 發生伺服器產生的錯誤時，就會擲回這個例外狀況。  
  
 如果發生嚴重錯誤，伺服器可能會關閉 <xref:System.Data.Odbc.OdbcConnection>。 但是，使用者可以再次開啟連線，然後繼續進行。  
  
## 請參閱  
 <xref:System.Data.Odbc.OdbcException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)