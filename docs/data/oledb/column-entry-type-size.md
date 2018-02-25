---
title: COLUMN_ENTRY_TYPE_SIZE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_TYPE_SIZE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE_SIZE macro
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cec18aa88ea5d34589e69e41b4a08136d6edf525
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="columnentrytypesize"></a>COLUMN_ENTRY_TYPE_SIZE
表示在資料庫中的特定資料行的繫結。 支援`type`和`size`參數。  
  
## <a name="syntax"></a>語法  
  
```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>參數  
 `nOrdinal`  
 [in] 資料行編號。  
  
 `wType`  
 [in]資料類型資料行項目。  
  
 `nLength`  
 [in]資料行項目，以位元組為單位的大小。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
## <a name="remarks"></a>備註  
 這個巨集是特殊的[COLUMN_ENTRY](../../data/oledb/column-entry.md)巨集，提供一種指定資料大小和類型。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)