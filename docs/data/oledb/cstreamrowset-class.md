---
title: "CStreamRowset 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e499d732beb2d73dbb6ec0bbe0b360eeb394b9d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cstreamrowset-class"></a>CStreamRowset 類別
用於`CCommand`或`CTable`宣告。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 存取子類別。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|建構函式。 執行個體化並初始化`CStreamRowset`物件。|  
|[關閉](../../data/oledb/cstreamrowset-close.md)|版本[ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx)類別中的介面指標。|  
  
## <a name="remarks"></a>備註  
 使用`CStreamRowset`中您`CCommand`或`CTable`宣告，例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]  
  
 或  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` 傳回`ISequentialStream`指標，它會儲存在`m_spStream`。 然後使用**讀取**方法來擷取 XML 格式 （Unicode 字串） 資料。 例如:   
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 執行 XML 格式化中，並會傳回所有資料行和資料列集，以 XML 字串的所有資料列。  
  
> [!NOTE]
>  這項功能只能搭配 SQL Server 2000。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)