---
title: BLOB_NAME | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB_NAME
dev_langs:
- C++
helpviewer_keywords:
- BLOB_NAME macro
ms.assetid: 757acd0d-946d-447d-937e-94ecd700ba38
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b4d5d7bbad25c7b2921e7b379c1014f893216d3d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="blobname"></a>BLOB_NAME
搭配`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`繫結的二進位大型物件 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。 類似於[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不過此巨集接受的資料行名稱，而不是資料行編號。  
  
## <a name="syntax"></a>語法  
  
```cpp
BLOB_NAME(pszName, IID, flags, data )  
```  
  
#### <a name="parameters"></a>參數  
 `pszName`  
 [in]指向的資料行名稱。 名稱必須是 Unicode 字串。 您可以完成這項作業，例如放在名稱前面 'L': `L"MyColumn"`。  
  
 *IID*  
 [in]介面的 GUID，例如**IDD_ISequentialStream**，用來擷取 BLOB。  
  
 `flags`  
 [in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如， **STGM_READ**)。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
## <a name="example"></a>範例  
 請參閱[如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)