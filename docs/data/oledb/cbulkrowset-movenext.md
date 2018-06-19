---
title: 'Cbulkrowset:: Movenext |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
dev_langs:
- C++
helpviewer_keywords:
- MoveNext method
ms.assetid: 788f3344-cf60-4af1-8f5f-0098c8d1a3f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 68ec7e4a583039a0087654dadde36598a3ced629
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094452"
---
# <a name="cbulkrowsetmovenext"></a>CBulkRowset::MoveNext
擷取下的一個資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveNext() throw();  
  
```  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。 當已到達資料列集結尾時，傳回**DB_S_ENDOFROWSET**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CBulkRowset 類別](../../data/oledb/cbulkrowset-class.md)