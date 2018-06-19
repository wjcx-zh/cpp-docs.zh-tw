---
title: 'Iaccessorimpl:: Getbindings |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e49d1b7b1ff313a1afc89dd39422d50a52342e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099182"
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
  
## <a name="see-also"></a>另請參閱  
 [IAccessorImpl 類別](../../data/oledb/iaccessorimpl-class.md)