---
title: "IRowsetNotifyImpl::OnRowsetChange | Microsoft Docs"
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
  - "OnRowsetChange"
  - "IRowsetNotifyImpl::OnRowsetChange"
  - "IRowsetNotifyImpl.OnRowsetChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnRowsetChange 方法"
ms.assetid: 5125b0c8-f175-4ee6-befa-8df2c904d5e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetNotifyImpl::OnRowsetChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

告知消費者，影響整個資料列集的任何變更。  
  
## 語法  
  
```  
  
   STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### 參數  
 為參數說明請參閱 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) 。  
  
## 傳回值  
 請參閱 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) 為相對值。  
  
## 備註  
 這個方法會包裝 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) 方法。  請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [IRowsetNotifyImpl 類別](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)