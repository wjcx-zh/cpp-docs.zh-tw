---
title: "Idbcreatecommandimpl:: Createcommand |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 83566713a42de25fb2c0e515daa94ee61eed53ed
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [IDBCreateCommandImpl 類別](../../data/oledb/idbcreatecommandimpl-class.md)