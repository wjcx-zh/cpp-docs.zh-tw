---
title: 'Iopenrowsetimpl:: Openrowset |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs:
- C++
helpviewer_keywords:
- OpenRowset method
ms.assetid: 2ece8d6c-d165-4f1d-b155-8609bbb60eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84bd34786dd87e92d70ad28d0f0a961cb01c1e48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iopenrowsetimplopenrowset"></a>IOpenRowsetImpl::OpenRowset
開啟並傳回包含單一基底資料表或索引的所有資料列的資料列集。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[iopenrowset:: Openrowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 ATLDB 中找不到這個方法。H. 當您建立的提供者會建立 ATL 物件精靈。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IOpenRowsetImpl 類別](../../data/oledb/iopenrowsetimpl-class.md)