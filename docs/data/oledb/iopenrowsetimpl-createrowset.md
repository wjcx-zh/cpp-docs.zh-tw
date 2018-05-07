---
title: 'Iopenrowsetimpl:: Createrowset |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d4554a2aeee3218ce505dc2c135167a3e38d55c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
 [IOpenRowsetImpl 類別](../../data/oledb/iopenrowsetimpl-class.md)