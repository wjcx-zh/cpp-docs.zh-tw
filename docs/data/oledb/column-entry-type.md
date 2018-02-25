---
title: COLUMN_ENTRY_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_TYPE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE macro
ms.assetid: ac424261-ff6c-443b-a197-2cec8d78d738
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: de5ead25c4e1c95b98411602a420cc424ff0c716
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="columnentrytype"></a>COLUMN_ENTRY_TYPE
表示在資料庫中的特定資料行的繫結。 支援`type`參數。  
  
## <a name="syntax"></a>語法  
  
```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)  
  
```  
  
#### <a name="parameters"></a>參數  
 `nOrdinal`  
 [in] 資料行編號。  
  
 `wType`  
 [in]資料類型資料行項目。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
## <a name="remarks"></a>備註  
 這個巨集是特殊的[COLUMN_ENTRY](../../data/oledb/column-entry.md)巨集，提供一種指定資料型別。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)