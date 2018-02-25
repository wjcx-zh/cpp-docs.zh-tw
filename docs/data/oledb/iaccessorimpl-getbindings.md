---
title: "Iaccessorimpl:: Getbindings |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
dev_langs:
- C++
helpviewer_keywords:
- GetBindings method
ms.assetid: eb550077-77ef-450b-89f1-a2930cee6ab8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3c7cab7607f1113c28b5eb365049d0358e16d12a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="iaccessorimplgetbindings"></a>IAccessorImpl::GetBindings
從取用者的存取子中傳回的基本資料行繫結。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(GetBindings)(HACCESSOR hAccessor,  
   DBACCESSORFLAGS* pdwAccessorFlags,  
   DBCOUNTITEM* pcBindings,  
   DBBINDING** prgBindings);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IAccessor::GetBindings](https://msdn.microsoft.com/en-us/library/ms721253.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IAccessorImpl 類別](../../data/oledb/iaccessorimpl-class.md)