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
ms.openlocfilehash: 14d0c07f8d1b8ff5cef19620fc00d156e251bf80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>另請參閱  
 [CArrayRowset 類別](../../data/oledb/carrayrowset-class.md)