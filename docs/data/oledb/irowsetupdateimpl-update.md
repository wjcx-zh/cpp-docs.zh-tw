---
title: "IRowsetUpdateImpl::Update | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetUpdateImpl::Update"
  - "IRowsetUpdateImpl::Update"
  - "IRowsetUpdateImpl.Update"
  - "ATL.IRowsetUpdateImpl.Update"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Update 方法"
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetUpdateImpl::Update
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

自上次擷取傳送所做的任何變更。  
  
## 語法  
  
```  
  
      STDMETHOD ( Update )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus   
);  
```  
  
#### 參數  
 `hReserved`  
 \[in\] 對應至 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)的 `hChapter` 參數。  
  
 如需其他參數，請參閱 *OLE DB 程式設計人員參考*的 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx) 。  
  
## 備註  
 變更會藉由呼叫 [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)傳輸。  消費者需要為了讓變更生效。呼叫 [CRowset::Update](../../data/oledb/crowset-update.md) 。  設定 *prgRowstatus* 為適當的值如 *OLE DB 程式設計人員參考*的 [資料列狀態](https://msdn.microsoft.com/en-us/library/ms722752.aspx) 所述。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)