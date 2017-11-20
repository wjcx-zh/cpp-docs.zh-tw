---
title: "BLOB_NAME_STATUS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_NAME_STATUS
dev_langs: C++
helpviewer_keywords: BLOB_NAME_STATUS macro
ms.assetid: 4564e4a0-8e5e-436a-bd1e-012d2a1b8642
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c76e47264c90bb21841279ca568b75c6d285611b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="blobnamestatus"></a>BLOB_NAME_STATUS
搭配`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`繫結的二進位大型物件 ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx))。 類似於[BLOB_NAME](../../data/oledb/blob-name.md)，只不過此巨集也會取得 BLOB 資料行的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
  
BLOB_NAME_STATUS(  
pszName  
,   
IID  
,   
flags  
,   
data  
, status )  
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
  
 *status*  
 [out]BLOB 欄位的狀態。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME](../../data/oledb/blob-name.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)