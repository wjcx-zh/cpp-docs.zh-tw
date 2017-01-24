---
title: "CSession::GetTransactionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetTransactionInfo"
  - "CSession.GetTransactionInfo"
  - "ATL.CSession.GetTransactionInfo"
  - "CSession::GetTransactionInfo"
  - "ATL::CSession::GetTransactionInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetTransactionInfo 方法"
ms.assetid: 9fa62808-3162-4b5a-8610-e1abb8cf9a71
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession::GetTransactionInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回有關交易的資訊。  
  
## 語法  
  
```  
  
      HRESULT GetTransactionInfo(   
   XACTTRANSINFO* pInfo    
) const throw( );  
```  
  
#### 參數  
 如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* 中的[ITransaction::GetTransactionInfo](https://msdn.microsoft.com/en-us/library/ms714975.aspx)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 如需詳細資訊，請參閱*OLE DB 程式設計人員參考*  [ITransaction::GetTransactionInfo](https://msdn.microsoft.com/en-us/library/ms714975.aspx) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)