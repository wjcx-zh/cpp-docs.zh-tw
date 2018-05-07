---
title: 'Crowset:: Crowset |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>::CRowset
- CRowset.CRowset
- ATL::CRowset::CRowset
- ATL::CRowset<TAccessor>::CRowset
- ATL.CRowset.CRowset
- CRowset
- CRowset<TAccessor>.CRowset
- CRowset::CRowset
- ATL.CRowset<TAccessor>.CRowset
dev_langs:
- C++
helpviewer_keywords:
- CRowset class, constructor
ms.assetid: 1c6f72e2-f4f4-48dc-957e-038ae8914ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c1ac78caaf82dc42a5e4d4afdab7e03bad53c5f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetcrowset"></a>CRowset::CRowset
建立新`CRowset`物件，並將它與 （選擇性） 關聯[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)當做參數提供的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
      CRowset();   

CRowset(IRowset* pRowset);  
```  
  
#### <a name="parameters"></a>參數  
 `pRowset`  
 [in] 要與這個類別相關聯的 `IRowset` 介面指標。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)