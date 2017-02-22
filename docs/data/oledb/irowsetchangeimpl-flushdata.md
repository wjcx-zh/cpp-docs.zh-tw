---
title: "IRowsetChangeImpl::FlushData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetChangeImpl::FlushData"
  - "IRowsetChangeImpl.FlushData"
  - "FlushData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FlushData 方法"
ms.assetid: fd4bc73b-bc25-4aab-90d5-0bed92670c88
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetChangeImpl::FlushData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由做資料提供者的 Overidden 對它的存放區。  
  
## 語法  
  
```  
  
      HRESULT FlushData(  
   HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush   
);  
```  
  
#### 參數  
 *hRowToFlush*  
 \[對資料列的控制代碼資料的。  這個資料行的型別從 `IRowsetImpl` 類別 \(`CSimpleRow` 的 *RowClass* 樣板引數來決定的預設\)。  
  
 *hAccessorToFlush*  
 \[out 存取子的控制代碼，在其 **PROVIDER\_MAP** 的包含繫結資訊和型別資訊 \(請參閱 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)\)。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetChangeImpl 類別](../../data/oledb/irowsetchangeimpl-class.md)