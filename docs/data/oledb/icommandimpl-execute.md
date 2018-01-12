---
title: "Icommandimpl:: Execute |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::Execute
- ICommandImpl.Execute
dev_langs: C++
helpviewer_keywords: Execute method
ms.assetid: 033e0d4e-256b-4eed-9215-70e0bebb768c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 965a344b55b6d290f112970ff357f383fefcd630
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="icommandimplexecute"></a>ICommandImpl::Execute
執行命令。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT Execute(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset   
);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[icommand:: Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 傳出要求的介面會從這個函式建立的資料列集物件取得的介面。  
  
 **執行**呼叫[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)。 若要建立多個資料列集，或提供您自己的條件建立不同的資料列集的預設實作會覆寫。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)