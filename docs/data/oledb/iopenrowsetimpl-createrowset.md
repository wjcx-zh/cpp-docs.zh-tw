---
title: "IOpenRowsetImpl::CreateRowset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOpenRowsetImpl.CreateRowset"
  - "IOpenRowsetImpl::CreateRowset"
  - "CreateRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateRowset 方法"
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IOpenRowsetImpl::CreateRowset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立一個 rowset 物件。  不會直接由使用者呼叫。  如需詳細資訊，請參閱  *OLE DB 程式設計人員參考* 中的 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)。  
  
## 語法  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### 參數  
 `RowsetClass`  
 表示使用者的資料列集類別的樣板類別 \(Template\-Class\) 成員。  通常由精靈產生。  
  
 `pRowsetObj`  
 \[資料列集物件的指標。  一般而言不會使用這個參數，不過，當您必須在傳遞至 COM 物件之前對結構描述資料列集進行更多工作時可以使用它。  `pRowsetObj` 的存留期由 `ppRowset` 約束。  
  
 如需其他參數，請參閱《*OLE DB 程式設計人員參考*》的[IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IOpenRowsetImpl 類別](../../data/oledb/iopenrowsetimpl-class.md)