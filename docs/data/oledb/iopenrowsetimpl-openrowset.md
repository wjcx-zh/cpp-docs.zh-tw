---
title: "IOpenRowsetImpl::OpenRowset | Microsoft Docs"
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
  - "OpenRowset"
  - "IOpenRowsetImpl::OpenRowset"
  - "IOpenRowsetImpl.OpenRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenRowset 方法"
ms.assetid: 2ece8d6c-d165-4f1d-b155-8609bbb60eb6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOpenRowsetImpl::OpenRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開啟並傳回含有來自單一基底資料表或索引的所有資料行的資料列集。  
  
## 語法  
  
```  
  
      HRESULT OpenRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset   
);  
```  
  
#### 參數  
 如需詳細資訊，請參閱  *OLE DB 程式設計人員參考* 中的 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)。  
  
## 備註  
 這個方法是在 ATLDB.H. 中找不到。  當您建立提供者時，它會由 ATL 物件精靈所建立。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IOpenRowsetImpl 類別](../../data/oledb/iopenrowsetimpl-class.md)