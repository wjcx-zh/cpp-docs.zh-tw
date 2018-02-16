---
title: IRowsetImpl::m_bReset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
dev_langs:
- C++
helpviewer_keywords:
- m_bReset
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ca38b0fa56f901d18e90d3305c92cc097452369
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
用來判斷是否資料列集上定義資料指標位置的位元旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>備註  
 如果取用者呼叫[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)具有負`lOffset`或*cRows*和`m_bReset`為 true，`GetNextRows`移動至資料列集結尾。 如果`m_bReset`為 false，取用者收到的錯誤代碼，依照 OLE DB 規格。 `m_bReset`旗標會設成**true**先建立資料列集時，當取用者呼叫[irowsetimpl:: Restartposition](../../data/oledb/irowsetimpl-restartposition.md)。 它會設成**false**當您呼叫`GetNextRows`。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)