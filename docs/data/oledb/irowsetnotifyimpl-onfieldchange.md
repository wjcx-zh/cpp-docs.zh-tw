---
title: "IRowsetNotifyImpl::OnFieldChange | Microsoft Docs"
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
  - "IRowsetNotifyImpl.OnFieldChange"
  - "IRowsetNotifyImpl::OnFieldChange"
  - "OnFieldChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnFieldChange 方法"
ms.assetid: f26b492c-c86e-423b-9374-175e510a2860
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetNotifyImpl::OnFieldChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

告知消費者，資料行值的任何變更。  
  
## 語法  
  
```  
  
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### 參數  
 為參數說明請參閱 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) 。  
  
## 傳回值  
 為相對值。請參閱 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) 。  
  
## 備註  
 這個方法會包裝 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) 方法。  請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [IRowsetNotifyImpl 類別](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)