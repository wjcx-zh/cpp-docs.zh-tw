---
title: COLUMN_ENTRY_PS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_PS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_PS macro
ms.assetid: 563c12b0-3376-49d5-a14f-aa68d1e63a7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab593c66aad4e0315d6df7e4dae3aa9f4ec84783
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="columnentryps"></a>COLUMN_ENTRY_PS
表示資料列集中的特定資料行之繫結的資料列集。  
  
## <a name="syntax"></a>語法  
  
```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)  
  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程式設計人員參考*。  
  
 `nOrdinal`  
 [in] 資料行編號。  
  
 `nPrecision`  
 [in] 要繫結之資料行的最大精確度。  
  
 `nScale`  
 [in] 要繫結之資料行的小數位數。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
## <a name="remarks"></a>備註  
 可讓您指定要繫結之資料行的精確度和小數位數。 這個參數可以用於下列狀況：  
  
-   之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。  
  
-   之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。  
  
-   之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)