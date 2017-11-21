---
title: "Irowsetupdateimpl:: Update |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs: C++
helpviewer_keywords: Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef3b93f85139ae0499d7e6679f39c8c885dbf4b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
會傳送自上次擷取或更新資料列所做的變更。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD ( Update )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus   
);  
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