---
title: "Crowsetimpl:: Validatecommandid |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
dev_langs: C++
helpviewer_keywords: ValidateCommandID method
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e59ca9d64ea71edcf52d151a592848434a109f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetimplvalidatecommandid"></a>CRowsetImpl::ValidateCommandID
檢查是否有任一個或兩個**DBID**s 包含字串值，而且如果是的話，會將它們複製到其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT CRowsetBaseImpl::ValidateCommandID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
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
  
## <a name="see-also"></a>請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)