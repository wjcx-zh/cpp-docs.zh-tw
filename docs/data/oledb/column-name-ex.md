---
title: COLUMN_NAME_EX |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_NAME_EX
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_EX macro
ms.assetid: 4f916a85-f6ae-464a-9cbe-0a56dbb274a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3992a727519ed83a0dbf4c570bad3bbf8d0404ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098689"
---
# <a name="columnnameex"></a>COLUMN_NAME_EX
表示資料列集中的特定資料行之繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在於資料類型、 大小、 有效位數、 小數位數、 資料行長度，以及資料行狀態，也會使用這個巨集。  
  
## <a name="syntax"></a>語法  
  
```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>參數  
 `pszName`  
 [in]指向的資料行名稱。 名稱必須是 Unicode 字串。 您可以完成這項作業，例如放在名稱前面 'L': `L"MyColumn"`。  
  
 `wType`  
 [in]資料型別。  
  
 `nLength`  
 [in]資料大小 （位元組）。  
  
 `nPrecision`  
 [in]取得資料時所要使用的最大有效位數和`wType`是`DBTYPE_NUMERIC`。 否則，這個參數已忽略。  
  
 `nScale`  
 [in]要取得資料時所使用的縮放比例和`wType`是`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。  
  
 `data`  
 [in] 使用者記錄中相對應的資料成員。  
  
 *length*  
 [in] 要繫結至資料行長度的變數。  
  
 *status*  
 [in] 要繫結至資料行狀態的變數。  
  
## <a name="remarks"></a>備註  
 請參閱[COLUMN_NAME](../../data/oledb/column-name.md)位置資訊**COLUMN_NAME_\*** 可用巨集。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
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