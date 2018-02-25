---
title: BLOB_ENTRY_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB_ENTRY_STATUS
dev_langs:
- C++
helpviewer_keywords:
- BLOB_ENTRY_STATUS macro
ms.assetid: 191007f4-dfcc-4ae2-a7fc-6f7899accc9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 207f42094ea62db103fb39a0057f595182a2ec9a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="blobentrystatus"></a>BLOB_ENTRY_STATUS
搭配`BEGIN_COLUMN_MAP`或`BEGIN_ACCESSOR_MAP`繫結的二進位大型物件 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。 類似於[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不過此巨集也會取得 BLOB 資料行的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)  
  
```  
  
#### <a name="parameters"></a>參數  
 `nOrdinal`  
 [in] 資料行編號。  
  
 *IID*  
 [in]介面的 GUID，例如**IDD_ISequentialStream**，用來擷取 BLOB。  
  
 `flags`  
 [in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如， **STGM_READ**)。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
 *status*  
 [out]BLOB 欄位的狀態。  
  
## <a name="example"></a>範例  
 請參閱[如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)