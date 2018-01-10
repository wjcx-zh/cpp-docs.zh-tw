---
title: "Carrayrowset:: Operator |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs: C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 61929df340fb12afc5c2abdc6bd9f4e8bd899108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
提供在資料列集中存取資料列，類似陣列的語法。  
  
## <a name="syntax"></a>語法  
  
```  
  
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