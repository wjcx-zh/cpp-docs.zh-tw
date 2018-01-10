---
title: "Crowset:: Movefirst |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset<TAccessor>::MoveFirst
- ATL::CRowset::MoveFirst
- CRowset<TAccessor>.MoveFirst
- CRowset::MoveFirst
- CRowset.MoveFirst
- ATL.CRowset.MoveFirst
- ATL.CRowset<TAccessor>.MoveFirst
- ATL::CRowset<TAccessor>::MoveFirst
dev_langs: C++
helpviewer_keywords: MoveFirst method
ms.assetid: a17c0799-ead9-4d85-9a1d-8b17188d01e3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 405549f94e5aad7ea241a5b6ed4687084aa73ff0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovefirst"></a>CRowset::MoveFirst
將游標移至的初始位置，並擷取初始資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT MoveFirst( ) throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 呼叫[irowset:: Restartposition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)重新定位到的初始位置 （資料列集建立時是下一個提取位置的位置） 的下一個提取位置，並擷取初始資料列。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [Crowset:: Movenext](../../data/oledb/crowset-movenext.md)   
 [Crowset:: Movetobookmark](../../data/oledb/crowset-movetobookmark.md)   
 [Crowset:: Moveprev](../../data/oledb/crowset-moveprev.md)   
 [Crowset:: Movelast](../../data/oledb/crowset-movelast.md)   
 [Irowset:: Restartposition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)