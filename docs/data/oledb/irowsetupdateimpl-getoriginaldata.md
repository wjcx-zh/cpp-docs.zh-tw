---
title: "IRowsetUpdateImpl::GetOriginalData | Microsoft Docs"
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
  - "ATL.IRowsetUpdateImpl.GetOriginalData"
  - "IRowsetUpdateImpl.GetOriginalData"
  - "GetOriginalData"
  - "ATL::IRowsetUpdateImpl::GetOriginalData"
  - "IRowsetUpdateImpl::GetOriginalData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOriginalData 方法"
ms.assetid: 7477b3b7-6b1b-49a7-8167-b34323f0fdcc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::GetOriginalData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

得到最近傳送至或從資料來源獲得的資料，忽略暫止的變更。  
  
## 語法  
  
```  
  
      STDMETHOD ( GetOriginalData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData   
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 中的 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)