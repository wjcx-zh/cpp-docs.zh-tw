---
title: COLUMN_ENTRY_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_STATUS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_STATUS macro
ms.assetid: 29ffe8b6-cb1e-438c-813e-2e6d73a5deef
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0351c479503f357712f25e9928b8082eb8bfbb29
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="columnentrystatus"></a>COLUMN_ENTRY_STATUS
表示從資料列集至資料庫的特定資料行的繫結。  
  
## <a name="syntax"></a>語法  
  
```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)  
  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程式設計人員參考*。  
  
 `nOrdinal`  
 [in] 資料行編號。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
 *status*  
 [in] 要繫結至資料行狀態的變數。  
  
## <a name="remarks"></a>備註  
 這個巨集支援*狀態*變數。 這個參數可以用於下列狀況：  
  
-   之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。  
  
-   之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。  
  
-   之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)