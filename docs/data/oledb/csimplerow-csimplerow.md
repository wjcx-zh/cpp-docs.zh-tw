---
title: 'Csimplerow:: Csimplerow |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
dev_langs:
- C++
helpviewer_keywords:
- CSimpleRow class, constructor
ms.assetid: 3968a36c-b8bb-48df-bd06-3956e64b0842
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 28033bb7fd8d0bd60fdea9fa4d12691ef87ef57d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099338"
---
# <a name="csimplerowcsimplerow"></a>CSimpleRow::CSimpleRow
建構函式。  
  
## <a name="syntax"></a>語法  
  
```cpp
      CSimpleRow(DBCOUNTITEM iRowsetCur);  
```  
  
#### <a name="parameters"></a>參數  
 `iRowsetCur`  
 [in]目前的資料列集的索引。  
  
## <a name="remarks"></a>備註  
 設定[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)至`iRowsetCur`。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [CSimpleRow 類別](../../data/oledb/csimplerow-class.md)