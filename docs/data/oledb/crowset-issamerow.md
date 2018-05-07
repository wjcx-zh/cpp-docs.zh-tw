---
title: 'Crowset:: Issamerow |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset::IsSameRow
- CRowset.IsSameRow
- IsSameRow
- ATL::CRowset::IsSameRow
- ATL.CRowset.IsSameRow
- CRowset<TAccessor>::IsSameRow
- ATL.CRowset<TAccessor>.IsSameRow
- CRowset<TAccessor>.IsSameRow
- ATL::CRowset<TAccessor>::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IsSameRow method
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cbe8179c04b8d7ab855942a4e6190341cc03128
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetissamerow"></a>CRowset::IsSameRow
比較指定的資料列的目前資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT IsSameRow(HROW hRow) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `hRow`  
 [in]要比較目前資料列的資料列控制代碼。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。 `S_OK` 表示資料列都相同。 如需其他值，請參閱[IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)