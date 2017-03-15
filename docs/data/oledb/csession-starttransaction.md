---
title: "CSession::StartTransaction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSession::StartTransaction"
  - "StartTransaction"
  - "ATL.CSession.StartTransaction"
  - "CSession.StartTransaction"
  - "ATL::CSession::StartTransaction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "StartTransaction 方法"
ms.assetid: cd7bd2be-fad1-4e2b-932b-79d308efb8fb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CSession::StartTransaction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟動工作階段的一種新的交易。  
  
## 語法  
  
```  
  
      HRESULT StartTransaction(  
   ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL   
) const throw( );  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx) 。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 《 *OLE DB 程式設計人員參考》 \(*如需詳細資訊，請參閱 [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)