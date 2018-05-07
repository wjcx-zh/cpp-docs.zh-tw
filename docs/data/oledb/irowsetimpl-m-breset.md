---
title: 'Irowsetimpl:: M_breset |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9aec38e3cf7e9a58c4fe99d06f35ae55cfdf81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)