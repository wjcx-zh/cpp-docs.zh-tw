---
title: 'Irowsetnotifyimpl:: Onrowchange |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
dev_langs:
- C++
helpviewer_keywords:
- OnRowChange method
ms.assetid: 148bee03-3707-4bbf-8c51-657efc63645f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8eae9d40b34adb6368b863f3534c5867a90979af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105604"
---
# <a name="irowsetnotifyimplonrowchange"></a>IRowsetNotifyImpl::OnRowChange
告知消費者的資料列的第一個變更或是任何會影響整個資料列的變更。  
  
## <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[irowsetnotify:: Onrowchange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)參數說明。  
  
## <a name="return-value"></a>傳回值  
 請參閱[irowsetnotify:: Onrowchange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)的回傳值描述。  
  
## <a name="remarks"></a>備註  
 這個方法會包裝[irowsetnotify:: Onrowchange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetNotifyImpl 類別](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)