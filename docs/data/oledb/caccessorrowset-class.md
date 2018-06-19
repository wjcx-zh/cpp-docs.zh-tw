---
title: CAccessorRowset 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 27d2153c6f600c3a5c75c1218e8751baaabcf030
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090966"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 類別
封裝資料列集，以及其相關聯的存取子中的單一類別。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CNoAccessor, 
          template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 存取子類別。  
  
 `TRowset`  
 資料列集類別。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[繫結](../../data/oledb/caccessorrowset-bind.md)|建立繫結 (使用時**bBind**指定為 false，在[ccommand:: Open](../../data/oledb/ccommand-open.md))。|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|建構函式。|  
|[關閉](../../data/oledb/caccessorrowset-close.md)|關閉資料列集和任何存取子。|  
|[FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)|釋出不再需要將目前記錄中的任何資料行。|  
|[GetColumnInfo](../../data/oledb/caccessorrowset-getcolumninfo.md)|實作[icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。|  
  
## <a name="remarks"></a>備註  
 類別`TAccessor`管理存取子。 類別*TRowset*管理資料列集。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)