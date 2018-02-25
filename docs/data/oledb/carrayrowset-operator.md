---
title: "Carrayrowset:: Operator |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs:
- C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2dd001dc3946a3eb22b793874ba1f4b16affb72
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
提供在資料列集中存取資料列，類似陣列的語法。  
  
## <a name="syntax"></a>語法  
  
```cpp
      TAccessor  
      & operator[](int nrow);  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 指定儲存在資料列集中存取子類型的範本參數。  
  
 `nRow`  
 [in] 要存取的資料列號碼 (陣列項目)。  
  
## <a name="return-value"></a>傳回值  
 所要求資料列的內容。  
  
## <a name="remarks"></a>備註  
 如果 `nRow` 超出資料列集中的資料列號碼，就會擲回例外狀況。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CArrayRowset 類別](../../data/oledb/carrayrowset-class.md)