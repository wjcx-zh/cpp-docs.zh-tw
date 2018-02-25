---
title: COLUMN_NAME_LENGTH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLUMN_NAME_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_LENGTH macro
ms.assetid: 3c4b6c94-d29d-4fba-a425-8186c9dc3f6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 99c9b63bd45c002a2798d1c951e4ac2bdc7d9fe5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="columnnamelength"></a>COLUMN_NAME_LENGTH
表示資料列集中的特定資料行之繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過此巨集也會採用資料行長度。  
  
## <a name="syntax"></a>語法  
  
```cpp
COLUMN_NAME_LENGTH(pszName, data, length)  
  
```  
  
#### <a name="parameters"></a>參數  
 `pszName`  
 [in]指向的資料行名稱。 名稱必須是 Unicode 字串。 您可以完成這項作業，例如放在名稱前面 'L': `L"MyColumn"`。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
 *length*  
 [in] 要繫結至資料行長度的變數。  
  
## <a name="remarks"></a>備註  
 請參閱[COLUMN_NAME](../../data/oledb/column-name.md)位置資訊**COLUMN_NAME_\*** 可用巨集。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)