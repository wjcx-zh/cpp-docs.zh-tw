---
title: "Irowsetcreatorimpl:: Setsite |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec7621972020d15068d53ccb3351983bc2b1b825
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [IRowsetCreatorImpl 類別](../../data/oledb/irowsetcreatorimpl-class.md)