---
title: 'Irowsetimpl:: M_bcanfetchback |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
dev_langs:
- C++
helpviewer_keywords:
- m_bCanFetchBack
ms.assetid: cfa007b0-7ba5-48a3-9d05-9f1916305fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf194fc7d7547cf03194f4dd5bedf014c9101b0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102052"
---
# <a name="irowsetimplmbcanfetchback"></a>IRowsetImpl::m_bCanFetchBack
指出提供者是否支援回溯擷取。  
  
## <a name="syntax"></a>語法  
  
```cpp
unsigned m_bCanFetchBack:1;  
  
```  
  
## <a name="remarks"></a>備註  
 連結至此網站**DBPROP_CANFETCHBACKWARDS**屬性**DBPROPSET_ROWSET**群組。 提供者必須支援**DBPROP_CANFETCHBACKWARDS**如**m_bCanFetchBackwards**即為 true。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)