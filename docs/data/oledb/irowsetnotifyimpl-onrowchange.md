---
title: "Irowsetnotifyimpl:: Onrowchange |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
dev_langs: C++
helpviewer_keywords: OnRowChange method
ms.assetid: 148bee03-3707-4bbf-8c51-657efc63645f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c765561ce1320944888e599fd4d9f7bf1da04976
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetnotifyimplonrowchange"></a>IRowsetNotifyImpl::OnRowChange
告知消費者的資料列的第一個變更或是任何會影響整個資料列的變更。  
  
## <a name="syntax"></a>語法  
  
```  
  
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
 [Irowsetnotify:: Onrowchange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)