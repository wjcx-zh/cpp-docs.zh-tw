---
title: "IRowsetUpdateImpl::SetData | Microsoft Docs"
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
  - "SetData"
  - "IRowsetUpdateImpl::SetData"
  - "IRowsetUpdateImpl.SetData"
  - "ATL::IRowsetUpdateImpl::SetData"
  - "ATL.IRowsetUpdateImpl.SetData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetData 方法"
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::SetData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一個或多個資料行中設定資料值。  
  
## 語法  
  
```  
  
      STDMETHOD ( SetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData   
);  
```  
  
#### 參數  
 如需詳細資訊，請參閱  *OLE DB 程式設計人員參考*  中的 [IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx)。  
  
## 備註  
 這個方法會覆寫 [IRowsetChangeImpl::SetData](../../data/oledb/irowsetchangeimpl-setdata.md) 方法，但包含原始資料快取可讓作業的直接或延後處理。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)