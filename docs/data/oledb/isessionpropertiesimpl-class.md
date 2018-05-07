---
title: ISessionPropertiesImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 62b1321c9d7d50ff2cd459b395efa1e8147a06ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 類別
提供的實作[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`ISessionPropertiesImpl`。  
  
 `PropClass`  
 預設為使用者定義的屬性類別`T`。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|傳回屬性的清單中目前所設定的工作階段的工作階段屬性群組。|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|在工作階段屬性群組中設定屬性。|  
  
## <a name="remarks"></a>備註  
 工作階段的強制介面。 這個類別會實作工作階段屬性，藉由呼叫靜態函式所定義[屬性集對應](../../data/oledb/begin-propset-map.md)。 屬性集對應應該指定在您的工作階段類別。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)