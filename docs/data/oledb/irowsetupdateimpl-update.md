---
title: 'Irowsetupdateimpl:: Update |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c47ee5bf8c8ddc3436414e89b7d365c06158f195
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104239"
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
會傳送自上次擷取或更新資料列所做的變更。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>參數  
 `hReserved`  
 [in]對應至`hChapter`中的參數[irowsetupdate:: Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)。  
  
 其他參數，請參閱[irowsetupdate:: Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 藉由呼叫傳輸變更[irowsetchangeimpl:: Flushdata](../../data/oledb/irowsetchangeimpl-flushdata.md)。 取用者必須呼叫[Crowset](../../data/oledb/crowset-update.md) ，變更才會生效。 設定*prgRowstatus*中所述的適當值[資料列狀態](https://msdn.microsoft.com/en-us/library/ms722752.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)