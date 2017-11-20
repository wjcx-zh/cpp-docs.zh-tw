---
title: "BLOB_ENTRY_LENGTH_STATUS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_ENTRY_LENGTH_STATUS
dev_langs: C++
helpviewer_keywords: BLOB_ENTRY_LENGTH_STATUS macro
ms.assetid: 09da67de-421b-4853-9a26-760e38324502
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed99a2834ace8809bcc2a4bd2fd784f7bd454d7d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="blobentrylengthstatus"></a>BLOB_ENTRY_LENGTH_STATUS
搭配`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`繫結的二進位大型物件 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。 類似於[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不過此巨集也會取得的長度和 BLOB 資料行的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
  
BLOB_ENTRY_LENGTH_STATUS(  
nOrdinal  
,   
IID  
,   
flags  
,   
data  
, length, status )  
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
  
 *length*  
 [out]BLOB 資料行的位元組 （實際） 長度。  
  
 *status*  
 [out]BLOB 資料行的狀態。  
  
## <a name="example"></a>範例  
 請參閱[如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)