---
title: ICommandImpl::GetDBSession | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
dev_langs:
- C++
helpviewer_keywords:
- GetDBSession method
ms.assetid: e5b1cb13-453f-4698-90bf-f6bfe6814a54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc7b057d43d0f5b28817fc1b4f4c7c23210ed141
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
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
  
## <a name="see-also"></a>請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)