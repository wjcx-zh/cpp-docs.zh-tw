---
title: "ICommandPropertiesImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 36c524d8aae9223e47b39bfe6cbfdfafdaa006f6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 類別
提供的實作[ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自  
  
 `PropClass`  
 您屬性的類別。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|傳回在目前要求的資料列集的資料列集屬性群組中的屬性清單。|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|在資料列集屬性群組中設定屬性。|  
  
## <a name="remarks"></a>備註  
 這是必要的命令。 所定義的靜態函式所提供的實作[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)巨集。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)