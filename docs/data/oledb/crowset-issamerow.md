---
title: CRowset::IsSameRow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b43788e1c64df3db223aa02df53014d3871b4c71
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)