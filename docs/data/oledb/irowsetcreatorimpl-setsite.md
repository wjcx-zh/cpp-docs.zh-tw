---
title: 'Irowsetcreatorimpl:: Setsite |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs:
- C++
helpviewer_keywords:
- SetSite method
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: af2883b261b754cee04e2c5090d1ef9b9887c04f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetcreatorimplsetsite"></a>IRowsetCreatorImpl::SetSite
設定站台，其中包含資料列集物件。 如需詳細資訊，請參閱[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>參數  
 `pCreator`  
 [in]指標**IUnknown**管理資料列集物件的站台的介面指標。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此外，`IRowsetCreatorImpl::SetSite`可讓 OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**屬性。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetCreatorImpl 類別](../../data/oledb/irowsetcreatorimpl-class.md)