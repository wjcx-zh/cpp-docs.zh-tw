---
title: "IRowsetCreatorImpl::SetSite | Microsoft Docs"
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
  - "IRowsetCreatorImpl.SetSite"
  - "IRowsetCreatorImpl<T>::SetSite"
  - "IRowsetCreatorImpl::SetSite"
  - "SetSite"
  - "ATL.IRowsetCreatorImpl.SetSite"
  - "ATL::IRowsetCreatorImpl<T>::SetSite"
  - "ATL::IRowsetCreatorImpl::SetSite"
  - "ATL.IRowsetCreatorImpl<T>.SetSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetSite 方法"
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetCreatorImpl::SetSite
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定包含資料列集物件的網站。  如需詳細資訊，請參閱 [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。  
  
## 語法  
  
```  
  
      STDMETHOD( SetSite )(  
   IUnknown* pCreator   
);  
```  
  
#### 參數  
 `pCreator`  
 \[out 處理資料列集物件的站台的 **IUnknown** 介面指標的指標。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 此外， `IRowsetCreatorImpl::SetSite` 啟用 OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS** 屬性。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetCreatorImpl 類別](../../data/oledb/irowsetcreatorimpl-class.md)