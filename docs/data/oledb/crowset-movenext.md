---
title: "Crowset:: Movenext |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.MoveNext
- ATL.CRowset.MoveNext
- ATL::CRowset<TAccessor>::MoveNext
- CRowset<TAccessor>.MoveNext
- CRowset.MoveNext
- CRowset<TAccessor>::MoveNext
- CRowset::MoveNext
- ATL::CRowset::MoveNext
dev_langs: C++
helpviewer_keywords: MoveNext method
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2b0a3a3a10ae2cc18ab83800cc50f25903a3607
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetmovenext"></a>CRowset::MoveNext
將游標移至下一筆記錄。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT MoveNext( ) throw( );   
HRESULT MoveNext(   
   LONG lSkip,   
   bool bForward = true    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `lSkip`  
 [in]擷取之前略過的資料列數目。  
  
 `bForward`  
 [in]傳遞**true**向前移到下一筆記錄，到**false**向後移動。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。 當已到達資料列集結尾時，傳回**DB_S_ENDOFROWSET**。  
  
## <a name="remarks"></a>備註  
 擷取下一個連續的資料列，從`CRowset`物件，記住先前的位置。 （選擇性） 您可以選擇跳`lSkip`資料列或向後移動。  
  
 這個方法會要求您設定下列屬性，才能呼叫**開啟**的資料表上包含資料列集的命令：  
  
-   **DBPROP_CANSCROLLBACKWARDS**必須`VARIANT_TRUE`如果`lSkip`< 0  
  
-   **DBPROP_CANFETCHBACKWARDS**必須`VARIANT_TRUE`如果`bForward`= false  
  
 否則 (如果`lSkip`> = 0 和`bForward`= true)，您不需要設定任何其他屬性。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [Crowset:: Movefirst](../../data/oledb/crowset-movefirst.md)   
 [Crowset:: Movetobookmark](../../data/oledb/crowset-movetobookmark.md)   
 [Crowset:: Moveprev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)