---
title: 'Icommandimpl:: Getdbsession |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
dev_langs:
- C++
helpviewer_keywords:
- GetDBSession method
ms.assetid: e5b1cb13-453f-4698-90bf-f6bfe6814a54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 116838ebb5857d5761b9d58d4f84e315de56d240
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icommandimplgetdbsession"></a>ICommandImpl::GetDBSession
傳回建立命令的工作階段的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD (GetDBSession) (REFIID riid,  
   IUnknown** ppSession);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[ICommand::GetDBSession](https://msdn.microsoft.com/en-us/library/ms719622.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 適用於從工作階段中擷取屬性。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)