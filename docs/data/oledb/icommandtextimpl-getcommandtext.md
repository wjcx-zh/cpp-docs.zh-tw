---
title: 'Icommandtextimpl:: Getcommandtext |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
dev_langs:
- C++
helpviewer_keywords:
- GetCommandText method
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e2f52f17258e4a317f58e40a60583998673f2efd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icommandtextimplgetcommandtext"></a>ICommandTextImpl::GetCommandText
傳回上次呼叫所設定的文字命令[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(GetCommandText)(GUID * pguidDialect,   
   LPOLESTR * ppwszCommand);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)中*OLE DB 程式設計人員參考*。 *PguidDialect*依預設，會忽略參數。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [ICommandTextImpl 類別](../../data/oledb/icommandtextimpl-class.md)