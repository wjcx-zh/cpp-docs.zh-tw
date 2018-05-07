---
title: CEnumerator 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b7e390212da53f85cb50dd5bb151ea6740784b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cenumerator-class"></a>CEnumerator 類別
使用 OLE DB 列舉值物件，會公開[ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx)介面，以傳回描述所有的資料來源和列舉值的資料列集。  
  
## <a name="syntax"></a>語法

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[尋找](../../data/oledb/cenumerator-find.md)|搜尋可用的提供者 （資料來源） 尋找具有指定名稱的其中一個。|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|擷取`IMoniker`介面目前的記錄。|  
|[開啟](../../data/oledb/cenumerator-open.md)|開啟 列舉值。|  
  
## <a name="remarks"></a>備註  
 您可以擷取**ISourcesRowset**間接從這個類別的資料。  
  
## <a name="requirements"></a>需求  
 **標頭：**atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)