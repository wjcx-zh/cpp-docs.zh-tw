---
title: 'Irowsetnotifyimpl:: Onrowsetchange |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- OnRowsetChange method
ms.assetid: 5125b0c8-f175-4ee6-befa-8df2c904d5e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 508dea3173aeab17372b6e31776b1e2fbff5f705
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetnotifyimplonrowsetchange"></a>IRowsetNotifyImpl::OnRowsetChange
通知任何變更會影響整個資料列集取用的者。  
  
## <a name="syntax"></a>語法  
  
```cpp
   STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)參數說明。  
  
## <a name="return-value"></a>傳回值  
 請參閱[IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)的回傳值描述。  
  
## <a name="remarks"></a>備註  
 這個方法會包裝[IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetNotifyImpl 類別](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)