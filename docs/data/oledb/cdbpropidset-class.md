---
title: CDBPropIDSet 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 67bfd11a46d8e0c852c1881ff8874b7fbd817164
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet 類別
繼承自**DBPROPIDSET**結構，並將建構函式會初始化索引鍵欄位，以及[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)存取方法。  
  
## <a name="syntax"></a>語法

```cpp
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|新增屬性至屬性 ID 集。|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|建構函式。|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|集合的屬性 ID 集的 GUID。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cdbpropidset-operator-equal.md)|指派的一個屬性 ID 集的內容至另一個。|  
  
## <a name="remarks"></a>備註  
 OLE DB 取用者使用**DBPROPIDSET**結構傳遞的取用者想要取得屬性資訊的屬性識別碼的陣列。 在單一識別屬性[DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx)結構屬於一個屬性集。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)