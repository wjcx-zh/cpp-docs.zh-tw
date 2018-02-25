---
title: "IDBPropertiesImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e1b1486d5eff73b4f868f5990ceb628cfb7dd20a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl 類別
提供的實作`IDBProperties`介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IDBPropertiesImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)|傳回目前所設定的資料來源物件或目前設於初始化屬性群組中的屬性值的資料來源、 資料來源資訊，以及初始化屬性群組中的屬性值列舉值。|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|傳回提供者所支援的所有屬性的相關資訊。|  
|[SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)|列舉值的資料來源和初始化屬性群組，資料來源物件或初始化屬性群組中，設定屬性。|  
  
## <a name="remarks"></a>備註  
 [IDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx)是資料來源物件的強制介面和列舉值的選用介面。 不過，如果列舉值公開[IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx)，它必須公開`IDBProperties`。 `IDBPropertiesImpl` 實作`IDBProperties`利用靜態函式所定義[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)