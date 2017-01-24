---
title: "CSession::Commit | Microsoft Docs"
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
  - "CSession.Commit"
  - "ATL.CSession.Commit"
  - "ATL::CSession::Commit"
  - "CSession::Commit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Commit 方法"
ms.assetid: 1d5f56b9-000c-4bae-a975-89d3452f499f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession::Commit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

認可交易。  
  
## 語法  
  
```  
  
      HRESULT Commit(   
   BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0    
) const throw( );  
```  
  
#### 參數  
 請參閱*《 OLE DB 程式設計人員參考》*的[ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx) 。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 如需詳細資訊，請參閱 [ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)