---
title: 'Crowsetimpl:: Validatecommandid |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
dev_langs:
- C++
helpviewer_keywords:
- ValidateCommandID method
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b83f0e8bb65a6043a9ca48f87ffe8babfb73e22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetimplvalidatecommandid"></a>CRowsetImpl::ValidateCommandID
檢查是否有任一個或兩個**DBID**s 包含字串值，而且如果是的話，會將它們複製到其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>參數  
 `pTableID`  
 [in]指標**DBID**代表資料表的識別碼。  
  
 `pIndexID`  
 [in]指標**DBID**代表索引識別碼。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法透過由靜態向上轉型呼叫`CRowsetImpl`來填入其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 根據預設，這個方法會檢查是否有任一個或兩者**DBID**s 包含字串值，而且如果是的話，會將它們複製到其資料成員。 藉由放置在這個簽章的方法您`CRowsetImpl`-衍生的類別，而不是基底實作，會呼叫您的方法。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)