---
title: "Csimplerow:: Csimplerow |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 70a9c1f28c777d60c45c34291cdb16d07193341d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [CSimpleRow 類別](../../data/oledb/csimplerow-class.md)