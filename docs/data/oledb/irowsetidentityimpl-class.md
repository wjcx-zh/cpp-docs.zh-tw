---
title: IRowsetIdentityImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 29ec88546a622ee42ce0e81efa9400305e2e14ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 類別
實作 OLE DB [IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx)介面，如此可讓測試的資料列識別。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別衍生自`IRowsetIdentityImpl`。  
  
 `RowClass`  
 儲存體單位**HROW**。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[IsSameRow](../../data/oledb/irowsetidentityimpl-issamerow.md)|比較兩個資料列控點，以查看它們是否參考相同的資料列。|  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)