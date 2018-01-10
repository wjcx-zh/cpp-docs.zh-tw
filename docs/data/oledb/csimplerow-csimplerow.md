---
title: "Csimplerow:: Csimplerow |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
dev_langs: C++
helpviewer_keywords: CSimpleRow class, constructor
ms.assetid: 3968a36c-b8bb-48df-bd06-3956e64b0842
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aaf96092efa8e3e595e815fddd5b0d3a75260702
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csimplerowcsimplerow"></a>CSimpleRow::CSimpleRow
建構函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
      CSimpleRow(  
   DBCOUNTITEM iRowsetCur   
);  
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