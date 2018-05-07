---
title: 'Cbulkrowset:: Releaserows |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ReleaseRows
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
dev_langs:
- C++
helpviewer_keywords:
- ReleaseRows method
ms.assetid: ba48aff3-0887-47ba-aed7-7ff28fa1c4a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a00de4950445a0d16c43d46a486390c152029de6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cbulkrowsetreleaserows"></a>CBulkRowset::ReleaseRows
呼叫[irowset:: Releaserows](https://msdn.microsoft.com/en-us/library/ms719771.aspx)目前從大量資料列集擷取的所有資料列的參考計數遞減。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ReleaseRows() throw();  
  
```  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CBulkRowset 類別](../../data/oledb/cbulkrowset-class.md)   
 [CBulkRowset::AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)