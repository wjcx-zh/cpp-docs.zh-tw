---
title: IRowsetIdentityImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cbafe7f43d8a6c7acfaccb52fd22b595bdd0ec4
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322094"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 類別
實作 OLE DB [IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx)介面，可讓資料列識別測試。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 類別衍生自`IRowsetIdentityImpl`。  
  
 *RowClass*  
 儲存體單位`HROW`。  

## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[IsSameRow](#issamerow)|比較兩個資料列控點，以查看它們是否參考相同的資料列。|  
  
## <a name="issamerow"></a> Irowsetidentityimpl:: Issamerow
比較兩個資料列控點，以查看它們是否參考相同的資料列。  
  
### <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/library/ms719629.aspx)中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 若要比較資料列控制代碼，這個方法會轉換`HROW`控制代碼對應到`RowClass`成員和呼叫`memcmp`指標。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
