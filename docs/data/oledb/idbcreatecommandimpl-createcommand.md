---
title: 'Idbcreatecommandimpl:: Createcommand |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- CreateCommand method
ms.assetid: 50ffbf8b-2c07-4bcb-96c5-ffce4519c7f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 709f734ad0349ea7908466958e282a8ca2a5c2db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="idbcreatecommandimplcreatecommand"></a>IDBCreateCommandImpl::CreateCommand
建立新的命令，並傳回要求的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[idbcreatecommand:: Createcommand](https://msdn.microsoft.com/en-us/library/ms709772.aspx)中*OLE DB 程式設計人員參考*。  
  
 有些參數會對應至*OLE DB 程式設計人員參考*參數不同的名稱，如下所述的**idbcreatecommand:: Createcommand**:  
  
|OLE DB 樣板參數|*OLE DB 程式設計人員參考*參數|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IDBCreateCommandImpl 類別](../../data/oledb/idbcreatecommandimpl-class.md)