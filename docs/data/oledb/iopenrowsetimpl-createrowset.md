---
title: IOpenRowsetImpl::CreateRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7aa478d86ba21dd482c3507352fb7f321df2ee0e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
建立資料列集物件。 並非由使用者直接呼叫。 請參閱[iopenrowset:: Openrowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中*OLE DB 程式設計人員參考。*  
  
## <a name="syntax"></a>語法  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>參數  
 `RowsetClass`  
 代表使用者的資料列集類別的樣板類別成員。 通常是由精靈產生。  
  
 `pRowsetObj`  
 [out]資料列集物件的指標。 通常不使用此參數，但如果您必須從資料列集執行更多工作，才能將它傳遞給 COM 物件才能使用。 存留期`pRowsetObj`受限於`ppRowset`。  
  
 其他參數，請參閱[iopenrowset:: Openrowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中*OLE DB 程式設計人員參考。*  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IOpenRowsetImpl 類別](../../data/oledb/iopenrowsetimpl-class.md)